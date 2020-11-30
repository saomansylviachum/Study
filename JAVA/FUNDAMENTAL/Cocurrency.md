# Atomicity, Visibility and Ordering 

(from:(http://jeremymanson.blogspot.com/2007/08/atomicity-visibility-and-ordering.html#:~:text=Atomicity%20deals%20with%20which%20actions,can%20be%20seen%20by%20another.)[http://jeremymanson.blogspot.com/2007/08/atomicity-visibility-and-ordering.html#:~:text=Atomicity%20deals%20with%20which%20actions,can%20be%20seen%20by%20another.])  
(Note: I've cribbed this from my doctoral dissertation. I tried to edit it heavily to ease up on the mangled academic syntax required by thesis committees, but I may have missed some / badly edited in places. Let me know if there is something confusingly written or just plain confusing, and I'll try to untangle it.)

There are these three concepts, you see. And they are fundamental to correct concurrent programming. When a concurrent program is not correctly written, the errors tend to fall into one of the three categories: atomicity, visibility, or ordering.

Atomicity deals with which actions and sets of actions have indivisible effects. This is the aspect of concurrency most familiar to programmers: it is usually thought of in terms of mutual exclusion. Visibility determines when the effects of one thread can be seen by another. Ordering determines when actions in one thread can be seen to occur out of order with respect to another. Let's talk about them.
## ATOMICITY
Everyone doing any serious concurrent programming knows what atomicity is (or will when I describe it) — I'm just putting it in for completeness's sake. If an action is (or a set of actions are) atomic, its result must be seen to happen ``all at once'', or indivisibly. Atomicity is the traditional bugbear of concurrent programming. Enforcing it usually means using locking to enforce mutual exclusion. To see atomicity in action (or in inaction, perhaps), consider this code:

```java
class BrokenBankAccount {
  private int balance;

  synchronized int getBalance() {
    return balance;
  }

  synchronized void setBalance(int x) 
    throws IllegalStateException {
    balance = x;
    if (balance < 0) {
      throw new IllegalStateException("Negative Balance");
    }
  }

  void deposit(int x) {
    int b = getBalance();
    setBalance(b + x);
  }

  void withdraw(int x) {
    int b = getBalance();
    setBalance(b - x);
  }
}
```

Since all accesses to the shared variable balance are guarded by locks, this code is free of what are called data races, which are basically what happens when you access a variable concurrently without some use of synchronization or volatile or the like (one of those accesses has to be a write to be a data race in the true sense). When code is free from data races, we say it is correctly synchronized. So the code is correct, right?

No, of course not. This code is not at all correct, in the sense that it doesn't necessarily do what we want it to do. Think about what happens if one thread calls deposit(5) and another calls withdraw(5); there is an initial balance of 10. Ideally, at the end of these two calls, there would still be a balance of 10. However, consider what would happen if:
The deposit() method sees a value of 10 for the balance, then

The withdraw() method sees a value of 10 for the balance
and withdraws 5, leaving a balance of 5, and finally

The deposit() method uses the balance it originally saw (10) to
calculate a new balance of 15.
As a result of this lack of "atomicity", the balance is 15 instead of 10. This effect is often referred to as a lost update, because the withdrawal is lost. A programmer writing multi-threaded code must use synchronization carefully to avoid this sort of error. In Java, if the deposit() and withdraw() methods are declared synchronized, it will ensure that locks are held for their duration: the actions of those methods will be seen to take place atomically.

Atomicity, of course, is only guaranteed when all the threads use synchronization correctly. If someone comes along and decides to read the balance without acquiring a lock, it can end up with all sorts of confusing results.

Atomicity is the most common problem you get when using synchronization. It is a common mistake to think that it is the only problem; it is not. Here's another one:
## VISIBILITY
What's visibility, you ask? Well, if an action in one thread is visible to another thread, then the result of that action can be observed by the second thread. In order to guarantee that the results of one action are observable to a second action, then you have to use some form of synchronization to make sure that the second thread sees what the first thread did.

(Note: when I say synchronization in this post, I don't actually mean locking. I mean anything that guarantees visibility or ordering in Java. This can include final and volatile fields, as well as class initialization and thread starts and joins and all sorts of other good stuff.)

Here's an example of a code with visibility problems:

```java
class LoopMayNeverEnd { 
  boolean done = false; 

  void work() { 
    while (!done) { 
      // do work 
    } 
  } 
 
  void stopWork() { 
    done = true; 
  } 
} 
```


In this code, imagine that two threads are created; one thread calls work, and at some point, the other thread calls stopWork on the same object. Because there is no synchronization between the two, the thread in the loop may never see the update to done performed by the other thread. In practice, this may happen if the compiler detects that no writes are performed to done in the first thread; the compiler may decide that the program only has to read done once, transforming it into an infinite loop.

(By the way, "compiler" in this context doesn't mean javac — it actually means the JVM itself, which plays lots of games with your code to get it to run more quickly. In this case, if the compiler decides that you are reading a variable that you don't have to read, it can eliminate the read quite nicely. As described above.)

To ensure that this does not happen, you have to use a mechanism that provides synchronization between the two threads. In LoopMayNeverEnd, if you want to do this, you can declare done to be volatile. Conceptually, all actions on volatiles happen in a single order, where each read sees the last write in that order. In other words, the compiler can't prevent a read of a volatile from seeing a write performed by another thread.

There is a side issue here; some architectures and virtual machines may execute this program without providing a guarantee that the thread that executes work will ever give up the CPU and allow other threads to execute. This would prevent the loop from ever terminating because of scheduling guarantees, not because of a lack of visibility guarantees. This is typically called cooperative multithreading.

There's one more problem that crops up:
## ORDERING
Ordering constraints describe what order things are seen to occur. You only get intuitive ordering constraints by synchronizing correctly. Here's an example of when ordering problems can bite you:

```java
class BadlyOrdered {
  boolean a = false;
  boolean b = false;

  void threadOne() {
    a = true;
    b = true;
  }

  boolean threadTwo() {
    boolean r1 = b; // sees true
    boolean r2 = a; // sees false
    boolean r3 = a; // sees true
    return (r1 && !r2) && r3; // returns true
  }

}
```

Consider what happens if threadOne() gets invoked in one thread and threadTwo() gets invoked on the same object in another. Would it be possible for threadTwo() to return the value true? If threadTwo() returns true, it means that the thread saw both updates by threadOne, but that it saw the change to b before the change to a.

Well, this code fragment does not use synchronization correctly, so surprising things can happen! It turns out that Java allows this result, contrary to what a programmer might have expected.

The assignments to a and b in threadOne() can be seen to be performed out of order. Compilers have a lot of freedom to reorder code in the absence of synchronization; they could either reorder the writes in threadOne or the reads in threadTwo freely.

How do you fix it? Synchronize your code carefully! In this case, you can throw a lock around threadOne or threadTwo, or you can declare them both both a and b to be volatile, and get the ordering you want.

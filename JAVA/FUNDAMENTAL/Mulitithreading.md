# Multithreading
## Cocurrency Safety
- synchronization is the easiest and most widely used tool for thread safety in java.
- Use of Atomic Wrapper classes from java.util.concurrent.atomic package. For example AtomicInteger
- Use of locks from java.util.concurrent.locks package.
- Using thread safe collection classes, check this post for usage of ConcurrentHashMap for thread safety.
- Using volatile keyword with variables to make every thread read the data from memory, not read from thread cache.
**ps: difference between atomic and volatile**
The effect of the volatile keyword is approximately that each individual read or write operation on that variable is atomic.

Notably, however, an operation that requires more than one read/write -- such as i++, which is equivalent to i = i + 1, which does one read and one write -- is not atomic, since another thread may write to i between the read and the write.

The Atomic classes, like AtomicInteger and AtomicReference, provide a wider variety of operations atomically, specifically including increment for AtomicInteger.

## Locks
- Java Lock API provides more visibility and options for locking, unlike synchronized where a thread might end up waiting indefinitely for the lock, we can use tryLock() to make sure thread waits for specific time only.
- Synchronization code is much cleaner and easy to maintain whereas with Lock we are forced to have try-finally block to make sure Lock is released even if some exception is thrown between lock() and unlock() method calls.
- synchronization blocks or methods can cover only one method whereas we can acquire the lock in one method and release it in another method with Lock API.
- synchronized keyword doesn’t provide fairness whereas we can set fairness to true while creating ReentrantLock object so that longest waiting thread gets the lock first.
- We can create different conditions for Lock and different thread can await() for different conditions.
```java

package com.journaldev.threads.lock;

import java.util.concurrent.TimeUnit;
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class ConcurrencyLockExample implements Runnable{

	private Resource resource;
	private Lock lock;
	
	public ConcurrencyLockExample(Resource r){
		this.resource = r;
		this.lock = new ReentrantLock();
	}
	
	@Override
	public void run() {
		try {
			if(lock.tryLock(10, TimeUnit.SECONDS)){
			resource.doSomething();
			}
		} catch (InterruptedException e) {
			e.printStackTrace();
		}finally{
			//release lock
			lock.unlock();
		}
		resource.doLogging();
	}

}
```

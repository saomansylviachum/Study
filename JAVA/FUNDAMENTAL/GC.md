## Finally or finalize

You should not depend much on finalization process of garbage collection since it's unpredictable.

If you want to clean up resources for sure, you may use a try-finally clause.

**Try-finally**

You can acquire resources and use them in a try block and release them in the associated final bloc.

But sometimes you didn't know when to clean up, then just use finalize so that you can clean up before gc.

## Object rescurrection

1. First time the gc ask the finalize()
2. If the object make a reference in the finalized and recurrect itself, it would be marked as finalized.
3. And the next time, the gc would not invoke finalize again.



## State of an Object

Two criteria:

- Finalization status
- Reachability

For Finalization

- Unfinalized
- Finalizable
- Finalized

For Reachability:

- Reachable
- Finalizer-reachable
- Unreachable



## Weak Reference

• Softly reachable
• Weakly reachable
• Phantom reachable

![image-20200914230215523](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200914230215523.png)

![image-20200914230338065](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200914230338065.png)



```java
Employee john = new Employee ("John Jacobs");
SoftReference sr = new SoftReference(john);
```

![image-20200914230441101](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200914230441101.png)





### Difference

1. If there is a week reference to an object, the gc would still reclaim the object.

2. Soft>weak>phantom

   ![image-20200914231355426](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200914231355426.png)

   1. **Strong reference** : 大家平常写代码的引用都是这种类型的引用，它可以防止引用的对象被垃圾回收。
   2. **Soft reference** : 它引用的对象只有在内存不足时，才会被回收。
   3. **Weak reference** : 它并不会延长对象的生命周期，即它不能阻止垃圾收集器回收它所引用的对象。
   4. **Phantom reference** : 它与上面的3种类型有很大的不同，它的`get()` 方法始终返回`null`，即通过这个引用，你甚至都不能获取它所引用的对象，如果你看它的源码，它的构造器必须要给定一个`ReferenceQueue`，当然了，你也可以把它设置为空，但是这样的引用 一点意义都没有。我在下文中会结合Phantom reference的作用来解释为什么会这样。

3. ![image-20200914231311959](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200914231311959.png)

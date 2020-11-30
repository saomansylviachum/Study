# ConcurrencyCollections
## CopyOnWriteArrayList

When iterate the list, we won't add a lock. 
When adding items, we create a new array and insert the element to the new array and change the reference to the new array.

> reminder: the arraylist maintains a reference to an array inside the class. So what we do is to change this reference value.

```java
/** The array, accessed only via getArray/setArray. */
private transient volatile Object[] array;
public boolean add(E e) {
    final ReentrantLock lock = this.lock;
	//1. 使用Lock,保证写线程在同一时刻只有一个
    lock.lock();
    try {
		//2. 获取旧数组引用
        Object[] elements = getArray();
        int len = elements.length;
		//3. 创建新的数组，并将旧数组的数据复制到新数组中
        Object[] newElements = Arrays.copyOf(elements, len + 1);
		//4. 往新数组中添加新的数据	        
		newElements[len] = e;
		//5. 将旧数组引用指向新的数组
        setArray(newElements);
        return true;
    } finally {
        lock.unlock();
    }
}
```

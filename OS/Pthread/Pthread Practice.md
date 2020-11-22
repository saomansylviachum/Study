# Pthread practice
## 1 Pthread creation
### 1.1 Birrell's Mechanisms
```c
pthread_t aThread;
int pthread_create(pthread_t *thread, const pthread_attr_t *attr, void * (*start_routine)(void *),void *arg);
int pthread_join(pthread_t thread, void **status)
```
### 1.2 pthread_attr_t
- specified in pthread_create
- defines features of the new thread
- has default behavior with NULL in pthread_create

stack size inheritance
joinable scheduling policy
priority system/process scope

```c
int pthread_attr_init(pthread_attr_t *attr)
int pthread_attr_destroy(pthread_attr_t *attr)
pthread_attr_{set/get}{attribute}
```

#### 1.3 Detaching Pthreads
```c
int pthread_detach();
pthread_attr_setdetachstate(attr,PTHREAD_CREATE_DETACHED)
//...
pthread_create(...,attr,...)

//And the parent thread can simply exit by 
void pthread_exit();
```

### 1.4 Compiling Pthreads
1. ``#include <pthread.h>``
2. Compile source with ``-lpthread`` or ``-pthread``
3. Check return values of common functions
```sh
gcc -o main main.c -lpthread
gcc -o main main.c -pthread
```

### 1.5 Problem analysis
**Creation Code**
```c
#include<stdio.h>
#include<pthread.h>
#define NUM_THREADS 4

void *threadFunc(void *pArg)
{
        int *p=(int*)pArg;
        int myNum=*p;
        printf("Thread number %d\n",myNum);
}

int main(void){
        int i;
        pthread_t tid[NUM_THREADS];
        for(i=0;i<NUM_THREADS;i++){
                /*create/fork threads*/
                printf("%d ", i);
                pthread_create(&tid[i],NULL,threadFunc,&i);
        }
        for(i=0;i<NUM_THREADS;i++){
                pthread_join(tid[i],NULL);
        }
        return 0;
```
This code would cause the problem that every thread's output would be the same!!
Reason:
The function input the address of i, and i remain the same address during this process. 
We can use an array to give every thread different variables.

## 2 Pthread Mutex
To solve mutual exclusion problems among concurrent threads.
Corresponding Syntax in Pthreads:
```c
pthread_mutex_t aMutex;//mutex type
// explicit lock
int pthread_mutex_lock(pthread_mutex_t *mutex);
//explicit unlock
int pthread_mutex_unlock(pthread_mutex_t *mutex);
```
Other Mutex Operations
```c
int pthread_mutex_init(pthread_mutex_t *mutex,const pthread_mutexattr_t *attr);
//mutex attributes == specifies mutex behavior when
// a mutex is shared among processes

int pthread_mutex_trylock(pthread_mutex_t *mutex);
int pthread_mutex_destroy(pthread_mutex_t *mutex);
```

**some tips**
1. Shared data should always be accessed through a single mutex
2. Mutex scope must be visible to all
3. Global order locks: for all threads, lock mutexes in order
4. Always unlock a mutex: always unlock the correct mutex

## 3. Pthread Condition Variables
```c
pthread_cond_t aCond;//Condition
int pthread_cond_wait(pthread_cond_t *cond,pthread_mutex_t* mutex);
int pthread_cond_signal(pthread_cond_t *cond);
int pthread_cond_broadcast(pthread_cond_t *cond);
```
other
```c
int pthread_cond_trylock(pthread_mutex_t *mutex);
// if it's shared
int pthread_cond_destroy(pthread_mutex_t *mutex);
```


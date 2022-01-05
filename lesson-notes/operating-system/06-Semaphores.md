## 信号量

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105091809174.png" alt="image-20220105091809174" style="zoom:67%;" />

### 通过信号量构建锁

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105091626413.png" alt="image-20220105091626413" style="zoom:50%;" />

### 通过锁和条件变量构建信号量

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105091732077.png" alt="image-20220105091732077" style="zoom:50%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105091745987.png" alt="image-20220105091745987" style="zoom:50%;" />

### 通过信号量构建读写锁

新增`reader_enter_lock`

在读者和写者尝试获取锁的操作上加上`reader_enter_lock`

当没有写者，多个读者时，读者获取锁不受影响，任意读者都可进入开始读；

当有写者进入时，获取了`reader_enter_lock`，不再有新读者可以进入，当所有正在执行的读者执行完毕后，释放写者锁，写者进入，释放`reader_enter_lock`，这时可以有新的读者进入等待；

读者和写者可以公平的竞争`reader_enter_lock`，读者获取时，写者无法进入；写者获取时，读者无法进入。

```c
typedef struct __rwlock_t {
    sem_t lock;
	sem_t writelock;
    sem_t reader_enter_lock;
	int readers;
} rwlock_t;


void rwlock_init(rwlock_t *rw) {
    rw->readers = 0;
	sem_init(&rw->lock, 0, 1);
	sem_init(&rw->writelock, 0, 1);
	sem_init(&rw->reader_enter_lock, 0, 1);
}

void rwlock_acquire_readlock(rwlock_t *rw) {
    sem_wait(&rw->reader_enter_lock);
    sem_wait(&rw->lock);
    sem_post(&rw->reader_enter_lock);
	rw->readers++;
	if(rw->readers == 1)
		sem_wait(&rw->writelock);
	sem_post(&rw->lock);
}

void rwlock_release_readlock(rwlock_t *rw) {
    sem_wait(&rw->lock);
	rw->readers--;
	if(rw->readers == 0)
		sem_post(&rw->writelock);
	sem_post(&rw->lock);
}

void rwlock_acquire_writelock(rwlock_t *rw) {

    sem_wait(&rw->reader_enter_lock);


    sem_wait(&rw->writelock);


    sem_post(&rw->reader_enter_lock);

}


void rwlock_release_writelock(rwlock_t *rw) {
    sem_post(&rw->writelock);
}
```


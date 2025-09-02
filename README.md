# Overview
A POSIX threads-based read-write lock implementation that provides concurrent read access and exclusive write access to shared resources. The implementation uses mutexes and condition variables to manage synchronization between readers and writers.

- Writer Priority: Waiting writers get priority when the lock becomes available
- Thread Safety: Uses pthread mutex and condition variables for synchronization
- Double Implementation: Provided in both header-only (__RWLOCK_IMPL__) and separate compilation versions

# Usage
- Include `rwlock.h`
- Either:
  - Header-only: Define `__RWLOCK_IMPL__` before including
  - Separate compilation: Compile and link `rwlock.c`

Example code:
```c
rwlock_t lock;
rwlock_init(&lock);

read_lock(&lock);
// ... read operations ...
read_unlock(&lock);

write_lock(&lock);
// ... write operations ...
write_unlock(&lock);
```

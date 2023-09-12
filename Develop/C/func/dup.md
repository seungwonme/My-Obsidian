## dup
```c
#include <unistd.h>

int dup(int fd);
```

매개변수 fd를 복제하여 반환, 오류 시 -1을 반환
## dup2
```c
#include <unistd.h>

int dup2(int fd, int fd2);
```

fd의 값을 fd2로 지정
만약 fd2가 이미 열려있다면 fd2를 닫고 fd에 복제, 오류 시 -1을 반환

- [ref](https://reakwon.tistory.com/104)
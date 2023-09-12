```c
#include <fcntl.h>

int open(const char *path, int oflag, ...);
```

- path : file의 path
- oflag : file에 대한 열기 옵션
- 반환 : 성공 시 해당 파일에 대한 fd 반환, 실패 시 -1

| oflag      | description                                                                        |
| ---------- | ----------------------------------------------------------------------------------|
| O_RDONLY   | 읽기 전용으로 열기                                                                     |
| O_WRONLY   | 쓰기 전용으로 열기                                                                     |
| O_RDWR     | 읽기, 쓰기가 모두 가능                                                                 |
| O_CREAT    | 해당 파일이 없으면 생성, 생성한다면 파일의 접근권한 지정해줘야 함                                 |
| O_EXCL     | O_CREAT를 사용할 때 같이 사용하면 이미 파일이 있을 때 open 함수가 실패되어 이전 파일을 보존할 수 있음  |
| O_TRUNC    | 기존의 파일 내용을 모두 삭제                                                             |
| O_APPEND   | open 후에 쓰기 포인터가 파일의 끝에 위치, 덧붙여 쓸 수 있게 됨                                 |
| O_NONBLOCK | 읽을 내용이 없을 때에는 읽을 내용이 있을 때까지 기다리지 않고 바로 복귀                            |
| O_SYNC     | 쓰기를 할 때, 실제 쓰기가 완료될 때까지 기다림 즉, 물리적으로 쓰기가 완료되어야 복귀                  |

- [ref](https://badayak.com/entry/C%EC%96%B8%EC%96%B4-%ED%8C%8C%EC%9D%BC-%EC%97%B4%EA%B8%B0-%ED%95%A8%EC%88%98-open)
```c
#include <unistd.h>

int access(const char *path, int mode);
```

- path : 체크하고자할 디렉토리 혹은 파일명
- return : 성공 시 0, 실패 시 -1

| mode | description                     |
| ---- | ------------------------------ |
| R_OK | 파일 존재 여부, 읽기 권한 여부 |
| W_OK | 파일 존재 여부, 쓰기 권한 여부 |
| X_OK | 파일 존재 여부, 실행 권한 여부 |
| F_OK | 파일 존재 여부                 |
- [ref](https://jdm.kr/blog/76)
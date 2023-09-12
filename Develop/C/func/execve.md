```c
#include <unistd.h>

int execve(const char *path, char *const argv[], char *const envp[]);
```

- path : 실행 파일의 경로
- argv : 실행 파일, 그 밖의 옵션 ... 마지막에 NULL인 문자열의 배열
- envp : 환경변수  (환경 변수가 쓰이는 awk같은 명령어 사용 시 고려)

- [man](https://man7.org/linux/man-pages/man2/execve.2.html)
- [ref](https://badayak.com/entry/C%EC%96%B8%EC%96%B4-%EB%8B%A4%EB%A5%B8-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EC%8B%A4%ED%96%89-%ED%95%A8%EC%88%98execve)
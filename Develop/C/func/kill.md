```c
#include <signal.h>

int kill(pid_t pid, int sig);
```

- pid : 시그널을 보내는 process id
- sig : signal number
- return : 성공 시 0, 실패 시 -1

특정 프로세스 뿐만 아니라 그룹 ID가 같은 모든 프로세스에게 동시에 시그널을 전송할 수 있으며, 권한 안에 있는 모든 프로세스에게도 시그널을 전송할 수 있다.

| pid                            | description                                                                         |
| ------------------------------ | ----------------------------------------------------------------------------------- |
| positive number                | 지정한 프로세스 ID에만 시그널을 전송                                                |
| 0                              | 함수를 호출하는 프로세스와 같은 그룹에 있는 모든 프로세스에 시그널을 전송           |
| -1                             | 함수를 호출하는 프로세스가 전송할 수 있는 권한을 가진 모든 프로세스에 시그널을 전송 |
| Negative numbers other than -1 | 첫 번째 인수 pid 의 절대값 프로세스 그룹에 속하는 모든 프로세스에 시그널을 전송     |

- [man](https://man7.org/linux/man-pages/man2/kill.2.html)
- [ref](https://badayak.com/entry/C%EC%96%B8%EC%96%B4-kill-%EC%8B%9C%EA%B7%B8%EB%84%90-%EC%A0%84%EC%86%A1-%ED%95%A8%EC%88%98-kill)
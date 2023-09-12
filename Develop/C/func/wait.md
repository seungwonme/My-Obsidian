## wait
```c
#include <sys/wait.h>

pid_t wait(int *stat_loc);
```

## waitpid
```c
#include <sys/wait.h>

pid_t waitpid(pid_t pid, int *stat_loc, int options);
```

- [ref](https://codetravel.tistory.com/42)
- [ref](https://codetravel.tistory.com/30)
- [ref](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=muri1004&logNo=221286169068)
- [ref](https://reakwon.tistory.com/105)
- [ref](https://colinch4.github.io/2021-06-11/wait_waitpid/)
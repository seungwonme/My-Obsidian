
#C

```c
void free(void *ptr);
```

free() 함수의 매개변수 ptr이 NULL 값을 갖는다면 동작하지 않는다.

```c
#include <stdlib.h>

int main(void)
{
	int *a;
	int *b;

	a = malloc(sizeof(int));
	b = malloc(sizeof(int));
	
	free(a);
	free(b);
	
	a = NULL;
	
	free(a);
	free(b); // free error
	return (0);
}
```

따라서, 다음과 같은 함수를 통해서만 free를 하여 이중 free를 방지하는 습관을 들이자

```c
void protected_free(void *ptr)
{
	free(ptr);
	ptr = NULL;
}

// if (ptr != NULL)
//     free(ptr);
// 굳이 이렇게 free 하지 않아도 된다 !
```

를 해봤는데 배열 혹은 문자열(포인터 혹은 포인터처럼 쓰이는 변수)을 프리해줄 때 
main 함수의 변수에 직접 NULL을 넣어줘야 하므로 형변환이 필요하다 -> 가독성이 떨어진다..

```c

int main(void)
{
	char *line = ft_calloc(1, sizeof(char));

	protected_free((void *)&line);
	protected_free((void *)&line);

	return (0);
}

void protected_free(void **ptr)
{
	free(*ptr);
	*ptr = NULL;
}
```

-[ref](https://dojang.io/mod/forum/discuss.php?d=1002)
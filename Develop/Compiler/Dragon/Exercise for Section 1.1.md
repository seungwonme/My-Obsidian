## Exercise 1.1.1 : What is the di erence b etween a compiler and an interpreter?

- Compiler : 소스 파일 -> 전처리기 -> 변경된 소스 파일 -> 컴파일러 -> 어셈블리 목적 파일 -> 어셈블러 -> 재배치 가능 목적파일(기계어) ->링커(목적 파일들, 라이브러리 등을 연결) -> 로더(메모리에 배치)
- Interpreter : 한줄씩 기계어로 변역 후 실행

## Exercise 1.1.2 : What are the advantages of (a) a compiler over an interpreter (b) an interpreter over a compiler?

- a : 컴파일 시간(초기 시간)이 들지만 컴파일이 끝나면 기계어 실행파일을 실행만 하면 되기 때문에 interpreter 방식보다 훨씬 더 빠르다.
- b : 소스 프로그램을 단계마다 실행하기 때문에 컴파일러보다 더 명시적인 에러 진단을 해줄 수 있다. 

## Exercise 1.1.3 : What advantages are there to a language-processing system in which the compiler produces assembly language rather than machine language?

- 어셈블리어로 번역하는 것이 더 쉽고 디버그하기 용이하기 때문이다.

## Exercise 1.1.4 : A compiler that translates a high-level language into another high-level language is called a source-to-source translator. What advantages are there to using C as a target language for a compiler?

- 가장 단순하고, 어셈블리어로 변환이 쉬운 저수준언어이기 때문이다.
- [ref](https://www.quora.com/What-advantages-are-there-to-using-C-as-a-target-language-for-a-compiler)

## Exercise 1.1.5 : Describe some of the tasks that an assembler needs to per-form

- 어셈블리 목적 파일을 실행 가능한 기계어로 해석
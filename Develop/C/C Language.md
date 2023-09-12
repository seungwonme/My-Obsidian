#C 

C언어를 제대로 배우지 못했다는 것은 구체적으로 어떤 것을 말하는 것일까? 
아래 질문에 답을 하거나 개념이라도 확실히 알고 있다면 C언어를 제대로 배운 것이고 아니라면 기초가 부실하거나 잘못 배운 것이다. (아래 질문들의 절반도 모르겠다면 C언어를 제대로 배운 것이라고 할 수 없다)

#### Q0. C언어는 언제, 어디서, 누가, 무엇을 위해 만들었는가?

#### Q1. C언어 국제표준(ISO/IEC 9899)은 무엇이며 C99, C11은 무엇인가?

#### Q2. C언어의 stdio(표준입출력)는 왜 만들어졌는가?

#### Q3. 전처리기(preprocessor)가 하는 일은 무엇인가? 그리고 왜 만들어졌는가?

#### Q4. long, int, short, pointer 변수의 크기는 몇 bit인가? (이들 크기는 고정 사이즈가 아님. int는 32bit라고 단정하면 틀린 거다

- 운영체제의 비트(word의 크기)에 따라 다르다. 
	- long, int = word
	- short = word / 2
	- pointer = 2 * word

#### Q5. API와 ABI는 무엇인가?

- API : Application Interface
  자판기처럼 사용자는 돈을 넣고 버튼을 눌러 음료수를 얻는 것 처럼 정해진 사용법대로 사용하면 정해진 결과가 나오는 소프트웨어

#### Q6. 오브젝트(object)란 무엇인가? (객체지향의 오브젝트를 말하는 것이 아님)

- 오브젝트 파일이란 

#### Q7. 링커(linker)가 하는 일은 무엇인가?

#### Q8. call-by-reference, call-by-value란 무엇인가? (C에 왜 call-by-reference가 없는지 설명할 수 있어야 함)

#### Q9. C언어의 main 함수의 return 값은 왜 int 인가? (void main()으로 선언하면 왜 틀리는가?)

#### Q10. C언어와 C++은 다른 하나가 부분집합인 서브셋인가? 아니면 둘은 다른 언어인가?

#### Q11. 하드웨어 제어에 C언어가 사용되는 이유는 무엇인가?

#### Q12. 시퀀스 포인트(sequence point)가 무엇인가?

#### Q13. Side effect란 무엇인가?

#### Q14. UB(Undefined behavior)란 무엇인가?

-[ref](https://sunyzero.tistory.com/m/225)
#Debugger

> 🐻 [야곰닷넷 LLDB 정복]()과 🐉 [LLDB Tutorial](https://lldb.llvm.org/use/tutorial.html)을 보고 정리한 글입니다.

- [[#LLDB란?|LLDB란?]]
- [[#LLDB 기본 문법|LLDB 기본 문법]]
	- [[#LLDB 기본 문법#Example|Example]]
	- [[#LLDB 기본 문법#Help & Apropos|Help & Apropos]]
	- [[#LLDB 기본 문법#Breakpoint|Breakpoint]]
		- [[#Breakpoint#Function Name|Function Name]]
		- [[#Breakpoint#File|File]]
		- [[#Breakpoint#Condition|Condition]]
		- [[#Breakpoint#Execute Command & AutoContinue|Execute Command & AutoContinue]]
		- [[#Breakpoint#b (\_regexp-break)  Command|b (\_regexp-break)  Command]]
		- [[#Breakpoint#Breakpoint List|Breakpoint List]]
		- [[#Breakpoint#Delete & Disable Breakpoint|Delete & Disable Breakpoint]]
	- [[#LLDB 기본 문법#Stepping|Stepping]]
	- [[#LLDB 기본 문법#Expression|Expression]]
	- [[#LLDB 기본 문법#Image|Image]]
		- [[#Image#Image List|Image List]]
		- [[#Image#Image Dump|Image Dump]]
		- [[#Image#Image Lookup|Image Lookup]]
- [[#Alias|Alias]]

## LLDB란?

LLDB는 차세대 고성능 디버거이자 macOS의 Xcode의 기본 디버거이며 C, Objective-C, C++디버깅을 지원한다고 [LLDB 공식 문서](https://lldb.llvm.org/)에 적혀있다.

## LLDB 기본 문법

```zsh
<noun> <verb> [-options [option-value]] [argument [argument...]]
```
- Command와 Subcommand는 LLDB 내 Object의 이름이며 Command에 따라 사용가능한 Subcommand 종류가 다르다
- Option의 경우 Command 뒤 어느 곳에서든 -(hyphen)으로 시작한다.
- Argument는 공백이 포함될 수 있으므로 ""(quotes)로 묶어줄 수 있다.

### Example
```shell
(lldb) breakpoint set --file test.c --line 12

cmd : breakpoint
sub : set
opt : --file, --line
```

### Help & Apropos

알았는데 까먹었거나 필요한 기능이 있는지 확인하기 위한 Command가 있다.

```shell
# LLDB에서 제공하는 Command 확인
(lldb) help

# 특정 Command의 Subcommand, Optione 확인
(lldb) help [Command] 
(lldb) help [Command] [Subcommand]

(lldb) apropos "Evaluate an expression"
The following commands may relate to 'Evaluate an expression':
  _regexp-display -- Evaluate an expression at every stop (see 'help target
                     stop-hook'.)
  expression      -- Evaluate an expression on the current thread.  Displays
                     any returned value with LLDB's default formatting.
  call            -- Evaluate an expression on the current thread.  Displays
                     any returned value with LLDB's default formatting.
  display         -- Evaluate an expression at every stop (see 'help target
                     stop-hook'.)
  p               -- Evaluate an expression on the current thread.  Displays
                     any returned value with LLDB's default formatting.
  po              -- Evaluate an expression on the current thread.  Displays
  ...
```

### Breakpoint

```shell
(lldb) breakpoint set [option] "arguments" 
# 줄이면
(lldb) br s [option] "arguments"
```

> [!tip] Tip !
> 대부분의 명령어와 옵션들은 command 맨 앞 1~2개 알파벳으로 줄여쓸 수 있다.

#### Function Name

이름을 가진 모든 함수에 -n(name) option을 사용해 break을 걸 수 있다

```shell
# 함수 이름 이용해 break 
(lldb) breakpoint set --name viewDidLoad
(lldb) b -n viewDidLoad
```

또한, _–func-regex (-r)_ option을 이용해 **정규표현식**을 활용 할 수 있습니다.

```shell
(lldb) breakpoint set --func-regex '^hello'
(lldb) br s -r '^hello' # 'breakopint set --func-regex'는 줄여서 'rb'로 사용 가능 
(lldb) rb '^hello'
```

#### File

파일 이름과 line 번호를 이용하여 break을 걸 수 있다.

```shell
# 특정 파일의 20번째 line에서 break 
(lldb) br s --file ViewController.swift --line 20 
(lldb) br s -f ViewController.swift -l 20
```

#### Condition

_–contidion (-c)_ option을 이용하면, breakpoint에 원하는 조건을 걸 수도 있습니다. _-c_ option 뒤의 expression이 true인 경우에만 breakpoint에서 멈춥니다.

```shell
# viewWillAppear 호출시, animated가 true인 경우에만 break 
(lldb) breakpoint set --name "viewWillAppear" --condition animated 
(lldb) br s -n "viewWillAppear" -c animated
```

#### Execute Command & AutoContinue

-  _-command (-C)_ option을 이용하면 break시 원하는 lldb command를 실행 할 수 있습니다
- _–auto-continue (-G)_ option의 기능은 auto continue로, command 실행 후 break에 걸린채로 있지 않고 프로그램을 자동 진행하게 해줍니다.

```shell
(lldb) breakpoint set -n "viewDidLoad" --command "po $arg1" -G1 
(lldb) br s -n "viewDidLoad" -C "po $arg1" -G1
```

#### b (\_regexp-break)  Command

```shell
# 특정 이름을 가진 function에서 break 
(lldb) b viewDidLoad 
# 현재 파일 20번째 line에서 break 
(lldb) b 20 
# 특정 파일 20번째 line에서 break 
(lldb) b ViewController.swift:20 
# 현재 파일 내 특정 text를 포함한 line에서 break 
(lldb) b /stop here/ 
# 특정 주소값에서 break 
(lldb) b 0x1234000
```

#### Breakpoint List

`(lldb) breakpoint list` command를 통해 현재 프로그램에 생성되어있는 Breakpoint의 목록을 확인할 수 있습니다. 또한, 이 목록 정보에는 Breakpoint의 id와 이름, hit-count 정보, enable 여부, source 상의 위치, 주소값 등등 유용한 정보가 포함되어있습니다.

프로그램 실행 중 활성 상태인 Breakpoint 지점이 실행되면 Debugger는 hit count를 1씩 늘려가며 기록한다.
disable 상태라면 count되지 않는다.

Breakpoint id를 통해 원하는 내용만 출력하거나, _–brief (-b)_ option을 통해 간단한 내용을 확인해 볼 수도 있습니다.

```shell
# breakpoint 목록 전체 출력 
(lldb) breakpoint list 
(lldb) br list 
# breakpoint 목록 간단하게 출력 
(lldb) br list -b 
# 특정 id를 가진 breakpoint의 정보만 출력 
(lldb) br list 1
```

#### Delete & Disable Breakpoint

```shell
# breakpoint 전체 삭제 
(lldb) breakpoint delete 
(lldb) br de 
# 특정 breakpoint 삭제 
(lldb) br de 1 
# breakpoint 전체 비할성화 
(lldb) breakpoint disable 
(lldb) br di 
# 특정 breakpoint 비활성화 
(lldb) br di 1.1
```

### Stepping

Stepping은 프로세스를 단계별로 진행하면서 상태 변화를 관찰해 볼 수 있는 유용한 기능입니다

- Stepping Over
	`(lldb) next` Command를 이용하면, 현재 Break 걸려있는 지점에서 바로 다음 Statement로 **Step Over** 할 수 있습니다. 줄여서 `(lldb) n`으로 사용 가능합니다.
- Stepping In
	**Stepping In** 은 다음 Statement가 Function Call 인경우 Debugger를 해당 함수 내부에 위치한 시작 지점으로 이동하게 해줍니다.  `(lldb) step` Command를 이용해 실행 할 수 있습니다. 줄여서 `(lldb) s`으로 사용 가능합니다.
- Stepping Out
	현재 진행중인 function이 return 될때까지 프로그램을 진행한 후 프로그램 Break걸어주는 Stepping Action을 **Stepping Out** 이라고 합니다. `(lldb) finish` Command로 실행해볼 수 있습니다. Stack Memory 관점에서 Stepping Out은 Stack Frame을 Pop하는 것과 동일합니다.

```shell
# 다음 breakpoint가 나타날 때까지 프로그램을 진행
(lldb) continue 
```

### Expression

`po`는 `(lldb) expression -O --` 의 Shorthand입니다. 여기서 _-O_ option은 object의 description을 출력하겠다는 뜻입니다.
**po**가 출력하는 description은 `NSObject`의 `debugDescription`입니다.

### Image

`(lldb) image`

**Module** 내에서 나타나는 **Symbol**에 대한 자세한 정보를 알아낼 수 있는 Command 입니다.

Image Command를 이용하면, Framework에 대한 Private한 정보들 _(private Class, private Method 등)_ 를 Header File에 공개되어 있는 것 이상으로 알아 볼 수 있습니다. **Private API**들에 접근 가능하다면, 객체에 대한 숨겨진 Description을 확인하거나, 더 세부적인 속성을 확인할 수 있을 겁니다 ? 디버깅이 좀 더 간편해지겠죠?

> [!quote] Module이란?
> Process에 Load되어 실행되는 Code를 의미
> C언어에서 메인 실행파일 뿐만 아니라 Library, Fremework 등을 포함하는 개념이다. 

> [!quote] Symbol이란?
> Method, Variable, Class 등 말 그대로 기계가 아닌 사람이 식별할 수 있는 Source Code를 이루는 작은 단위
> Symbol Table은 Compile된 Binary를 그에 맞게 상호 Mapping 해주는 역할, Binary가 Symbol로 번역되는 것은 Symbolicate라고 한다.

#### Image List

 `(lldb) image list` 는 현재 Process에 Load 되어잇는 모든 Module들의 정보를 출력합니다.
  
 현재 Load 되어있는 Module들의 **UUID**, 실제 Memory상 Load되어있는 **주소값**, 그리고 Disk 내에서 Binary가 존재하는 **Path** 정보를 알 수 있습니다.

#### Image Dump

이번에는 UIKitCore Library에 대한 좀 더 구체적인 내용을 뽑아보고 싶습니다. `(lldb) image dump`

Command 를 이용하면 Module의 세부적인 정보를 dumping(dump는 기억장치의 내용을 기록하는 것입니다) 해볼 수 있습니다.

```shell
image dump symtab a.out -s address
```

이렇게 출력된 Symbol Table에는 해당 모듈에 포함되어있는 Variable, Method, Metadata, Protocol 등 모든 Symbol이 들어있습니다.

#### Image Lookup

Image dump의 내용들을 필터링 해서 볼 수 있는 command가 바로 `(lldb) image lookup` 입니다!

```shell
# 함수 이름 (--function) 
(lldb) image lookup -F "functionName" 
# 주소값 (--address) 
(lldb) image lookup -a "0x00address" 
# 파일 이름 (--filename) 
(lldb) image lookup -f "FileName.swift" 
# 라인 번호 (--line) 
(lldb) image lookup -f "FileName.swift" -l 15 
# 정규식 이용 (--regex) 
(lldb) image lookup -rn "regexExpression"
```

`(lldb) image lookup` Command는 **Symbolicate** 되지않은 **Crash Log**를 살펴볼 때 굉장히 유용합니다.

## Alias

`(lldb) command alias 별명 "줄이고 싶은 Command"`

~/.lldbinit 파일에 
`command alias 별명 "줄이고 싶은 Command"` 형식으로 지정해두면 사라지지 않는다.

- [apple lldb](https://developer.apple.com/library/archive/documentation/IDEs/Conceptual/gdb_to_lldb_transition_guide/document/lldb-basics.html)
# Clean-Code <애자일 소프트웨어 장인 정신>
[1장. 깨끗한 코드 ](#1장-깨끗한-코드)   
[2장. 의미 있는 이름](#2장-의미-있는-이름)  
[3장. 함수](#3장-함수)  
[4장. 주석](4장-주석)  
[5장. 형식 맞추기](5장-형식-맞추기)  
[6장. 객체와 자료구조](6장-객체와-자료구조)  
[7장. 오류 처리](7장-오류-처리)  
[8장. 경계](8장-경계)
<br>
<br>


## 1장. 깨끗한 코드

### 깨끗한 코드란 무엇일까?

**비야네 스트롭스트룹 (C++ 창시자)**
- **깨끗한 코드** : "보기에 즐거운 코드", "단순한 속도뿐만 아니라 CPU자원도 낭비하지 않는 코드"  
- **나쁜 코드** : "나쁜 코드는 나쁜 코드를 유혹한다!" (=나쁜 코드를 고치면서 오히려 더 나쁜 코드를 만듦), "오류코드(메모리 누수, 경쟁 상태, 일관성 없는 명명법)"
<br>

**데이브 토마스와 앤디 헌트 (실용주의 프로그래머)**
- **나쁜 코드** : "깨진 창문" (=창문이 꺠지고 나면 쇠토하는 과정이 시작됨)
<br>

**그래디 부치**  
- **깨끗한 코드** : "가독성이 좋은 코드", "단순하고 직접적인 코드"
<br>

**큰 데이브 토마스 (이클립스의 대부)**
- **깨끗한 코드** : "가독성이 좋은 코드면서 다른 사람이 고치기 쉬운 코드", 
<br>

**마이클 페더스 (이클립스의 대부)**
- **깨끗한 코드** : "손댈 곳이 없는 코드", "주의 깊게 짠 코드"
<br>


**론 제프리스**  

켄트 백이 제안한 단순 코드 규칙
- 모든 테스트를 통과한다.
- 중복이 없다.
- 시스템 내 모든 설계 아이디어를 표현
- 클래스, 메서드, 함수 등을 최대한 줄임

- 즉, **"중복을 피하라"**, **"한가지 기능만 수행하라"** , **"제대로 표현하라"**, **"작게 추상화하라"**
<br>

**위드 커닝햄 (위키의 창시자)**
- **깨끗한 코드** : "짐작가능한 코드"
<br>


### 그렇다면 어떻게 코드를 짜야하는가?
<br>

**보이스카우트 규칙**
>"캠프장은 처음 왔을 때보다 더 깨끗하게 해놓고 떠나라"
<br>

**프리퀄과 원칙**  
Agile Software Development: Principles, Patterns, and Practices(PPP)의 프리퀄    
PPP에서 얘기하는 원칙은 다음과 같음    
- **SRP(The Single Responsibility)** : 클래스에는 한 가지, 단 한 가지 변경 이유만 존재해야 함     
- **OCP(The Open Closed Principle)** : 클래스는 확장에 열려 있어야 하며 변경에 닫혀 있어야 함      
- **LSP(The Liskov Subsititution Principle)** : 상속받은 클래스는 기초 클래스를 대체할 수 있어야 함    
- **DIP(The Dependency Inversion Principle)** : 추상화에 의존해야 하며, 구체화에 의존하면 안 됨  
- **ISP(The Inferface Segregation Principle)** : 클라이언트에 밀접하게 작게 쪼개진 인터페이스를 유지함  
<br>


## 2장. 의미 있는 이름

### 1. 의도를 분명히 밝혀라
변수나 함수 그리고 클래스 이름은 다음과 같은 굵직한 질문에 모두 답해야 함
>"변수(혹은 함수나 클래스)의 존재 이유는? 수행 기능은? 사용 방법은? 따로 주석이 필요하다면 의도를 분명히 드러내지 못했다는 뜻"
<br>

아래의 사례를 한번 보자
<br>

```JAVA
int d; // 경과 시간(단위: 날짜)
```
<br>

여기서 이름 d는 아무 의미도 드러내지 않음. 경과 시간이나 날짜라는 느낌이 안 들기 때문에 측정 하려는 값과 단위를 표현하는 이름이 필요함
<br>

```JAVA
int elapsedTimeImDays;
int daysSinceCreation;
int fileAgeInDays;
}
```
<br>

위처럼 의도가 드러나는 이름을 사용하면 코드이해와 변경이 쉬워짐.
<br>

그럼 아래의 코드를 한번 보자.  
코드가 하는 일을 짐작할 수가 없음. 복잡한 문장은 없지만 왜일까?  
공백과 들여쓰기도 적당, 변수는 세 개, 상수는 두 개뿐임. 화려한 클래스나 다형메서드(?)도 없고, 겉보기에는 배열 목록만 사용함.  
<br>

문제는 코드의 단순성이 아니라 **코드의 함축성**이다.  
코드 맥락이 코드 자체에 명시적으로 드러나지 않음, **보는 사람이 다음과 같은 정보를 안다고 가정한 코드**이다.  
<br>

- theList에 무엇이 들었는가?
- theList에서 0번째 값이 어째서 중요한가?
- 값4는 무슨 의미인가?
- 함수가 반환하는 리스트 list을 어떻게 사용하는가?
<br>

```JAVA
public List<int[]> getThem() {
  List<int[]> list1 = new ArrayList<int[]>();
for (int[] x :theList)
  if (x[0] == 4);
    list1.add(x);
return list1;
}
```
<br>

각 개념에 이름만 붙여도 코드가 상당히 나아질 수 있다.
<br>

```JAVA
public List<int[]> getFlaggedCells() {
    if (gameBoard == null) {
        throw new IllegalStateException("gameBoard is null");
    }
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard) {
        if (cell != null && cell.length > STATUS_VALUE && cell[STATUS_VALUE] == FLAGGED) {
            flaggedCells.add(cell);
        }
    }
    return flaggedCells;
}
```
<br>

위에서 보듯, 코드의 단순성은 변하지 않았다. 연산자 수와 상수는 앞의 예시와 똑같으며, 들여쓰기 단계도 동일하다.  
그런데 코드는 더욱 명확해졌다.
<br>

-int 배열을 사용하는 대신, 칸을 간단한 클래스로 만들고, isFlagged라는 좀더 명시적인 함수를 사용해 FLAGGED라는 상수를 감춰도 좋겠다.  
다음과 같이 또 개선해보자.
<br>

```JAVA
public List<Cell> getFlaggedCells() {
    List<Cell> flaggedCells = new ArrayList<Cell>();
    for (Cell cell : gameBoard) {
        if (cell.isFlagged()) {
            flaggedCells.add(cell);
        }
    }
    return flaggedCells;
}
```
<br>

단순히 이름만 고쳤는데도 함수가 하는 일을 이해하기 쉬워진다.  
이것이 바로 좋은 이름이 주는 위력이다.   
<br>

### 2. 그릇된 정보를 피하라
프로그래머는 코드에 그릇된 단서를 남겨서는 안된다.  
**❗ 나름대로 널리 쓰이는 의미가 있는 단어를 다른 의미로 사용해도 안 된다.**  
<br>

여러 계정을 그룹으로 묶을 때, 실제 List가 아니라며느 accountList라 명명하지 않는다.  
계정을 담는 컨테이너가 실제 List가 아니라면 프로그래머에게 그릇된 정보를 제공하는 셈이다.  

그러므로 accountGroup, bunchOfAccounts, 아니면 단순히 Accounts라 명명한다.
<br>
<br>

**❗ 서로 흡사한 이름을 사용하지 않도록 주의한다.**  
<br>

한 모듈에서 XYZControllerForEfficientHandleingOfStrings라는 이름을 사용하고, 조금 떨어진 모듈에서 XYZControllerForEfficientStorageOfStrings라는 이름을 사용한다면?      
유사한 개념은 유사한 표기법을 사용한다. 일관성이 떨어지는 표기법은 그릇된 정보이다.    
<br>

십중팔구 개발자는 (객체에 달린 상세한 주석이나 클래스가 제공하는 메서드 목록을 살펴보지 않은 채) 이름만 보고 객체를 선택한다.    
<br>

이름으로 그릇된 정보를 제공하는 끔찍한 예가 **소문자L이나 대문자O 변수**다.  
다음 코드에서 보듯, 소문자L은 숫자 1처럼 보이고 대문자O는 숫자0처럼 보인다.  
<br>

```JAVA
int a =1;
if ( 0 == 1)
a= 01;
else
1 = 01;

```
<br>

### 3.  의미 있게 구분하라 
<br>

**getActiveAccount()**
**getActiveAccounts()**
**getActiveAccountInfo()**

이 프로젝트에 참여한 프로그래머는 어느 함수를 호출할지 어떻게 알까?  
<br>

명확한 관례가 없다면 변수 moneyAmount는 money와 구분이 안 된다.  
customerInfo는 customer와 accountData는 account와, theMeassage는 message와 구분이 안 된다.  
<br>

읽는 사람이 차이를 알도록 이름을 지어라.  
<br>

### 4.  발음하기 쉬운 이름을 사용하라
<br>

```JAVA
class DtaRcrd102 {
  private Date genymdhms;
  private Date modymdhms;
  private final String pszqint = '102';
   /*...*/
};
```
<br>

와

```JAVA
class DtaRcrd102 {
  private Date generationTimestamp;
  private Date modificationTimestamp;
  private final String recoedId = '102';
   /*...*/
};
```
<br>

둘째 코드는 지적인 대화가 가능해진다.  
"마이키, 이 레코드 좀 보세요. 'Generation Timestamp'값이 내일 날짜입니다! 어떻게 이렇죠?"  
<br>


### 5.  검색하기 쉬운 이름을 사용하라
<br>

```JAVA
for (int j=0; j<34; j++) {
  s += (t[j]*4)/5;
}
```

와

```JAVA
int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;
int SUM =0;
for (INT J=0; J<NUMBER_OF_TASKS; j++) {
  int realTaskDays = taskEstimate[j] * realDaysPerIdealDays;
  int realTaskWeeks = (realaskDays / WORK_DAYS_PER_WEEK);
  sum += realTaskWeeks;
```
<br>

위 코드에서 sum이 유용하진 않으나, 최소한 검색이 가능하다.
이름을 의미있게 지으면 함수가 길어진다.
<br>

하지만, WORK_DAYS_PER_WEEK를 찾기가 얼마나 쉬운지 생각해보라.  
그냥 5를 사용한다면 5가 들어가는 이름을 모두 찾은 후 의미를 분석해 상수를 가려내야 한다.
<br>


### 5.  인코딩을 피하라
<br>
유형이나 범위 정보까지 인코딩에 넣으면 그 만큼 이름을 해독하기 어려워진다.  
인코딩한 이름은 거의 발음하기 어려우며 오타가 생기기도 쉽다.  
<br>

**헝가리식 표기법**  
<br>
이름 길이가 제한된 언어를 사용하던 옛날에는 어떨 수 없이 안타까워하면서도 이 규칙을 위반헀다.    
포트란은 첫 글자로 유형을 표현했다. 초창기 베이식은 글자 하나에 숫자 하나만 허용했다.    
헝가리식 표기법은 기존 표기법을 완전히 새로운 단계로 끌어올렸다.     

하지만 과거와와는 달리 현재, 컴파일러가 타입을 기억하고 강제한다.  
또한 변수를 선언한 위치와 사용하는 위치가 멀지 않다.  

IDE는 코드를 컴파일 하지 않고도 타입 오류를 감지할 정도로 발전했다.  
따라서 이제는 헝가리식 표기법이나 기타 인코딩 방식이 오히려 방해가 될 뿐이다.   
<br>

**멤버 변수 접두어**  
<br>
이제는 멤버 변수에 m_ 이라는 접두어를 붙일 필요가 없다.  
클래스와 함수는 접두어가 필요없을 정도로 작아야한다.   
이제는 변수를 다른 색으로 표시해주는 IDE가 있다.  


### 6.  자신의 기억력을 자랑하지 마라
<br>

독자가 코드를 읽으면서 변수 이름을 자신이 아는 이름으로 변환해야 한다면 그 변수 이름은 바람직하지 못하다.  
이는 일반적으로 문제 영역이나 해법 영역에서 사용하지 않는 이름은 선택하기 때문에 생기는 문제다.  

문자하나만 사용하는 변수 이름은 문제가 있다.
루프에서 반복 횟수를 세는 변수 i,j,k는 괜찮다. (l은 절대 안 된다!)

최악은  이미 a와 b를 사용하므로 c를 선택한다는 논리다.
전문가 프로그래머들은 자신의 능력을 좋은 방향으로 사용해 남들이 이해하는 코드를 내놓는다.
<br>

### 7.  클래스 이름
<br>

클래스 이름과 객체 이름은 **명사나 명사구**가 적합하다.
Customer, WikiPage, Account, AddressParser 등이 좋은 예다.
Manager, Processor, Data, Info 등과 같은 단어는 피하고, 동사는 사용하지 않는다.
<br>

### 8.  메서드 이름
<br>

메서드 이름과 객체 이름은 명사나 명사구가 적합하다. postPayment, deletePage, save 등이 좋은 예다.  
접근자(Accessor) , 변경자(Mutator), 조건자(Predicate)는 javabean 표준에 따라 값에 get, set, is를 붙인다.
<br>

```JAVA
string name = employee.getName();
customer.setName('mike');
if (paycheck.isPosted()..)
```
<br>

생성자(Construnctor)를 중복범위(Overload)할 때는 정적 팩토리 메서드를 사용한다.  
메서드는 인수를 설명하는 이름을 사용한다.
<br>


### 9.  가발한 이름은 피하라
<br>

이름이 너무 기발하면 농담을 기억하는 동안만, 이름을 기억한다.  
HolyHandGrenade라는 함수가 무엇을 하는지 알겠는가?   

기발한 이름이지만 DeleteItems가 좋다. **재미난 이름보다 명료한 이름**을 선택하라.  
간혹, 프로그래머가 나름대로 재치를 발휘해 구어체나 속어를 이름으로 사용하는 사례가 있다.  
예를 들어, kill() 대신에 whack()이라 부르거나 Abort() 대신 eatMyShort()라 부른다.   
특정 문화에서만 사용하는 농담은 피하는 편이 좋다.
<br>

### 10.  한 개념에 한 단어를 사용하라
<br>

추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다.

🤣 여기서는 내가 이해하기엔 내용이 너무 어렵다.
나중에 따로 찾아서 정리해보자.
<br>

### 11.  말 장난 하지마라
<br>

똑같은 메서드를  클래스마다 fetch, retrieve, get으로 제각각 부르면 혼란스럽다.  
일관성 있는 어휘를 쓴 코드를 사용하자!  
<br>

### 12.  해법 영역에서 가져온 이름을 사용하라
<br>

코드를 읽는 사람도 프로그래머라는 사실을 명심한다. 모든 이름을 문제 영역domain에서 가져오는 정책은 현명하지 못하다.   
기술 개념에는 기술 이름이 가장 적합한 선택이다.   
<br>

### 13.  문제 영역에서 가져온 이름을 사용하라
<br>

적절한 프로그래머 용어가 없다면 문제 영역에서 이름을 가져온다.  
그러면 코드를 보수하는 프로그래머가 분야 전문가에게 의미를 물어 파악할 수 있다.  
문제영역개념과 관련이 깉은 코드라면 무제 영역에서 이름을 가져와야 한다. 
<br>

### 14.  의미 있는 맥락을 추가하라
<br>

클래스 함수, 이름 공간에 넣어 맥락을 부여한다.
<br>

### 16.  불필요한 맥악을 없애라
<br>

일반적으로 짧은 이름이 졸다. 단, 의미가 분명한 경우에 한해서다.  
이름에 불필요한 맥락을 추가하지 않도록 주의한다.  
<br>

**❗ 요약**  
<br>

좋은 이름을 선택하려면 설명 능력이 뛰어나야하고 문화적인 배경이 같아야 한다.  
이 장에서 소개한 규칙 몇개를 적용해 코드 가독성을 높여보자.  
<br>



## 3장. 함수

### 1. 작게 만들어라
함수를 만드는 첫째 규칙은 '작게'이다.
함수를 만드는 듈째 규칙은 '더 작게'이다.
<br>

### 2. 블록과 들여쓰기
다시 말해, if문/else문 등에 들어가는 블록은 한 줄이어야 한다는 의미다.
대개 거기서 함수를 호출한다. 그러면 바깥을 감싸는 함수가 작아질 작아질 뿐만 아니라, 블록 안에서 호출하는 함수 이름을 적절히 짓는다면  
코드를 이해하기도 쉬워진다.

함수에서 들여쓰기 기준은 1단이나 2단을 넘어서면 안된다. 
그래야 함수가 읽고 이해하기 쉬워진다.
<br>

### 3. 한 가지만 해라!
"함수는 한 가지를 해야한다. 그 한가지를 잘해야 한다. 그 한가지만을 해야 한다."

함수가 "한 가지"만 하는지 판단하는 방법은 단순히 다른 표현이 아니라 의미 있는 이름으로 다른 함수를 추출할 수 있다면 그 함수는 여러 작업을 하는 셈이다.
<br>

### 4. 함수 당 추상화 수준은 하나로!
함수가 확실히 "한 가지" 작업만 하려면 함수 내 모든 문장의 추상화 수준이 동일해야 한다.

한 함수내에 추상화 수준을 섞으면 코드를 읽는 사람이 헷갈린다.
특정 표현이 근본 개념인지 아니면 세부사항인지 구분하기 어려운 탓이다.
<br>

**위에서 아래로 읽기 : 내려가기 규칙**
코드는 위에서 아래로 읽혀야 좋다.
한 함수 다음에는 추상화 수준이 한단계 낮은 함수가 온다. 
<br>


### 5. Switch 문
switch문은 작게 만들기 어렵다.
이 예시는 자바로 되어있어 나중에 한번 다시 보고 정리하기
<br>

### 6. 서술적인 이름을 사용하라!
코드를 읽으면서 짐작했던 기능을 각 루틴이 그대로 수햏한다면 깨끗한 코드라 불러도 되겠다.
이름이 길어도 길고 서술적인 이름이 짧고 어려운 이름보다 좋다.
함수 이름을 정할 때는 여러 단어가 쉽게 읽히는 명명법을 사용한다.
그런 다음, 여러  단어를 사용해 함수 기능을 잘 표현하는 이름을 선택한다.
<br>

### 7. 함수 인수
함수에서 이상적인 인수 개수는 0개(무항)이다.
다음은 1개(단항)이고 다음은 2개(이항)이다.
4개 이상(다항)은 특병한 이유가 필요하다. 특병한 이유가 있어도 사용하면 안된다.
<br>

### 8. 부수 효과를 일으키지 마라!
부수효과로 기능이 숨겨진 경우에는 더더욱 혼란이 커진다. 함수 이름의 중요성.
<br>

### 9. 명령과 조회를 분리하라!
함수는 무너가를 수행하거나 뭔가에 답하거나 둘 중 하나만 해야 한다. 
즉, 객체 상태를 변경하거나 객테 정보를 반환하거나 둘 중 하나다.
둘 다 하면 혼란을 초래한다. 
<br>

### 10. 오류 코드보다 예외를 사용해라!

```JAVA
if (deletePage(page) == E_OK)
/*...*/
```
<br>

위 코드는 if/else 중첩된 코드는 동상/형용사 혼란을 일으키지 않는 대신 여러 단계로 중첩되는 코드를 야기한다.
오류 코드를 반환하면 호출자는 오류 코드를 곧바로 처리해야한단느 문제에 부딪힌다.

반면 오류 코드 대신 예외를 사용하면 오류 처리 코드가 원래 코드에서 분리되므로 코드가 깔끔해진다.(try catch문 이용)
<br>


### 11. Try/Catch 블록 뽑아내기
try/catch블록은 별도 함수로 뽑아내는 편이 좋다.
<br>


## 4장. 주석

### 1. 주석은 나쁜 코드를 보완하지 못한다.  
코드에 주석을 추가하는 일반적인 이유는 코드 품질이 나쁘기 때문이다.   
주석을 달아야겠다!!!가 아닌 코드를 정리해야한다!!! (명언)  
<br>

### 2.코드로 의도를 표현하라!  
주석이 아닌 코드로 대다수 의도를 표현할 수 있다. 많은 경우 주석으로 달려는 설명을 함수로 만들어 표현해도 충분하다.  
<br>

### 3.좋은 주석
<br>

- **법적인 주석**  
때로는 회사가 정립한 구현 표준에 맞춰 법적인 이유로 특정 주석을 넣으려고 명시한다.   
예를 들어, 각 소스 파일 첫머리에 주석으로 들어가는 저작권 정보와 소유권 정보는 필요하고도 타당하다.   
<br>

- **정보를 제공하는 주석**  
주석이 유용하다 할지라도 가능하다면, 함수 이름에 정보를 담는 편이 더 좋다.   
<br>

- **의도를 설명하는 주석**  
때떄로 주석은 구현을 이해하게 도와주는 선을 넘어 결정에 깔린 의도까지 설명 한다.   

- **의미를 명료하게 밝히는 주석**  
모호한 인수나 반환값은 그 의미를 읽기 좋게 표현하면 이해하기 쉬워진다.   
<br>

- **결과를 경고하는 주석**  
다른 프로그래머에세 결과를 경고하는 목적으로 주석을 사용한다.  
예를 들어, 특정 케이스를 꺼야 하는 이유를 설명하는 주석이다.  
물론 요즘에는 @ignore 속성을 사용해 테스트 케이스를 꺼버린다.  
<br>

- **TODO주석**  
앞으로 해야 할 일을 //TODO주석으로 남겨두면 편하다.   
TODO주석은 프로그래머가 필요하다 여기지만 당장 구현하기 어려운 업무를 기술한다.   
더 이상 필요없는 기을 삭제하라는 알림, 누군가에게 문제를 봐달라는 요청, 더 좋은 이름을 떠올려 달라는 부탁, 앞으로 발생할 이벤트에 맞춰 코드를 고치라는 주의 등에 유용하다.   
<br>

- **중요성을 강조하는 주석**     
자칫 대수롭지 않다고 여겨질 뭔가의 중요성을 강조하기 위해서도 주석을 사용한다.    
<br>


### 4.나쁜 주석    
대다수 주석이 이 범주에 속한다.     
<br>

- **같은 이야기를 중복하는 주석**    
헤더에 달린 주석이 같은 코드 내용을 그대로 중복한다.     
<br>

- **오해 할 여지가 있는 주석**    
주석에 담긴 살짝 잘못된 정보로 인해 문제가 발생할 수 있다.     
<br>

- **의무적으로 다는 주석**    
모든 변수, 함수에 주석을 다는 것은 안된다.    
<br>

- **이력을 기록하는 주석**    
변경을 모두 기록하는 일종의 일지 혹은 로그가 되서는 안된다.    
<br>

- **있으나 마나한 주석**     
때때로 있으나 만 한 주석을 말한다.     
너무 당연한 사실을 언급하며 새로운 정보를 제공하지 못하는 주석이다.     
<br>

- **함수나 변수로 표현할 수 있다면 주석을 달지 마라**    
주석보단 코드에 집중하자!    
<br>

- **닫는 괄호에 다는 주석**    
때로는 프로그래머들이 닫는괄호에 특수한 주석을 달아놓는다.     
닫는 괄호에 주석을 달아야 겠다는 생각이 든다면 대신에 함수를 줄이려 시도하자.    
<br>

- **공로를 돌리거나 저자를 표시하는 주석**    
소스 코드관리 시스템은 누가 언제 무엇을 추가했는지 귀신처럼 기억한다.    
저자 이름으로 코드를 오염시킬 필요가 없다.    
<br>

- **주석으로 처리한 코드**    
주석으로 처리된 코드는 다른 사람들이 지우기를 주저한다.     
이유가 있어 넘겨놓았으리라고 생각해서 지우면 안된다고 생각한다.     
그래서 나쁜 코드들이 쌓여간다.     
<br>

- **HTML 주석**    
소스코드에서 HTML주석은 혐오그자체다.    
<br>


- **전역정보**    
주석을 달아야 한다면 근처에 있는 코드만 기술해라.    
코드 일부에 주석을 달면서 시스템의 전반적인 정보를 기술하지 마라.    
<br>

- **너무 많은 정보**  
주석에다 흥미로운 역사나 관련없는 정보를 장황하게 늘어놓지 마라.  
<br>

- **모호한 관계**  
주석과 주석이 설명하는 코드는 둘 사이 관계가 명확해야 한다.   
<br>

- **함수 헤더**  
짧은 함수는 긴 설명이 필요없다.   
짧고 한가지만 수행하며 이름을 잘 붙인 함수가 주석으로 헤더를 추가한 함수보다 좋다.   
<br>


## 5장. 형식 맞추기

### 1. 형식을 맞추는 목적
코드의 가독성은 앞으로의 코드 품질에 큰 영향을 미치기 때문에 코드 형식을 맞추는 것이 중요하다.
<br>

### 2. 적절한 행 길이를 유지하라
대부분 500줄을 넘기지 않고 대부분 200줄로도 커다란 시스템 구축이 가능하다.
반드시 지켜야 할 엄격한 규칙은 아니지만 바람직한 규칙으로 삼자.
<br>

### 3. 신문 기사처럼 작성하라
소스파일의 첫 부분은 고차원 개념과 알고리즘을 설명한다. 아래로 내려갈 수록 의도를 세세하게 묘사한다.
마지막에는 가장 저차원 함수와 세부 내역이 나온다. 
<br>

저차원 함수와 고차원 함수는 프로그래밍에서 함수의 추상화 수준을 나타내는 개념이다.
간단하게 설명하면, 함수가 얼마나 세부적인 구현을 담고 있는지에 따라 구분되는 개념이다.
<br>

**저차원 함수 (Low-Level Functions)**

- 기본 함수, 하나의 동작을 수행하는 간단한 명령어 
- 세부적인 동작을 담당하는 함수들을 의미한다.
- 주로 기본적인 계산, 조작, 입출력 등의 기능을 수행한다.
- 일반적으로 코드의 구체적인 세부 내역을 담당하며, 코드의 가독성이 낮을 수 있다.
- 다른 함수에서 자주 호출되거나 반복되는 작업을 수행한다.
- 예시: 배열의 요소들을 정렬하는 함수, 특정 값을 검색하는 함수, 파일을 읽고 쓰는 함수 등이 저차원 함수에 해당한다.
<br>

```JAVASCRIPT
// 배열의 요소들을 오름차순으로 정렬하는 함수 (저차원 함수)
function sortArray(arr) {
  // 정렬 알고리즘 구현 (저차원 함수)
  // ...
  return sortedArray;
}

// 특정 값을 배열에서 검색하는 함수 (저차원 함수)
function searchValue(arr, target) {
  // 검색 알고리즘 구현 (저차원 함수)
  // ...
  return foundValue;
}
```
<br>

**고차원 함수 (High-Level Functions)**

- 추상화 함수, 고차원 함수
- 추상화된 개념이나 전체적인 로직을 담당하는 함수들을 의미한다.  
- 저차원 함수를 활용하여 더 큰 의미를 담고 있는 작업을 수행한다.  
- 코드의 가독성이 높고, 재사용성과 유지보수가 용이한다.  
- 일반적으로 하나 이상의 저차원 함수를 조합하여 더 큰 기능을 수행한다.  
- 예시: 데이터를 필터링하거나 변형하여 새로운 배열을 생성하는 함수, 웹 페이지에서 사용자 정보를 가져와 렌더링하는 함수, 데이터베이스에서 데이터를 가져와 비즈니스 로직을 처리하는 함수 등이 고차원 함수에 해당할 수 있다.  
<br>

```JAVASCRIPT
// 배열에서 홀수만 필터링하여 새로운 배열을 생성하는 함수 (고차원 함수)
function filterOddNumbers(arr) {
  return arr.filter(item => item % 2 !== 0);
}

// 사용자 정보를 가져와서 화면에 렌더링하는 함수 (고차원 함수)
function renderUserInfo(userId) {
  // 사용자 정보를 가져오는 비동기 함수 호출 (저차원 함수)
  getUserData(userId)
    .then(userData => {
      // 화면에 데이터를 렌더링하는 로직 (저차원 함수)
      // ...
    })
    .catch(error => {
      // 에러 처리 (저차원 함수)
      // ...
    });
}
```
<br>

### 4. 개념은 빈 행으로 분리하라
각 행은 수식이나 절을 나타내고, 일련의 행 묶음은 완결된 생각하나를 표현한다.
생각 사이에는 빈 행을 넣어 분리해야 마땅하다.
<br>

빈 행은 새로운 개념을 시작한다는 시각적 단서이다.
빈 행을 빼버리면 코드의 가족성이 현저하게 떨어져 암호처럼 보인다.
<br>

### 5. 세로 밀집도
줄바꿈이 개념을 분리한다면 세로 밀집도는 연관성을 의미한다.
즉, 서로 밀접한 코드 행은 세로로 가까이 놓여야 한다.
코드가 한눈에 더 잘들어오게 된다.
<br>


### 6. 수직 거리
함수 연관 관계와 동작 방식을 이해하려고 이 함수에서 저 함수로 오가며 소스 파일을 위아래로 뒤지는 등 뺑뺑이를 돌았으나
결국 미로 같은 코드 때문에 혼란만 가중될 때가 있다.
<br>

함수나 변수가 정의된 코드를 찾으려 상속 관계를 줄줄이 거슬러 올라간 경험이 있다.
서로 밀접한 개념은 세로 거리로 연관겅을 표현한다.
<br>

연관성이 깊은 두 개념이 멀리 떨어져 있으면 코드를 읽는 사람이 소스 파일과 클래스를 여기저기 뒤지게 된다. 
<br>

### 7. 변수 선언
변수는 사용하는 위치에 최대한 가까이 선언한다.
아래는 매우 짧으므로 지역 변수는 각 함수 맨 처음에 선언한다.
<br>

```JAVA
private static void readPreferences() {
    InputStream is = null;
    try {
        is = new FileInputStream(getPreferencesFile());
        setPreferences(new Properties(getPreferences()));
        getPreferences().load(is);
    } catch (IOException e) {
        try {
            if (is != null)
                is.close();
        } catch (IOException e1) {
            // 예외 처리를 수행
        }
    }
}
```
<br>

루프를 제어하는 변수는 흔히 루프 문 내부에 선언한다.

```JAVA
public int countTestCases() {
  int count = 0;
  for (Test each : tests)
    count += each.countTestCases();
  return count;
}
```
<br>

아주 드물지만 다소 긴 함수에서 블록 상단이나 루프 직접에 변수를 선언하는 사례도 있다.


```JAVA
for (XmalTest : m_suite.getTests()) {
  TestRunner tr = m_runnerFactory.newTestRunner(this, test);
  tr.addListener(m_textReporter);
  m_testRunners.add(tr);

  invoker = tr.getInvoker();

  for (ITestNGMethod m : tr.getBeforeSuiteMethod()) {
beforeSuiteMethods.put(m.getMethod(), m);
}

  for (ITestNGMethod m : tr.getBeforeSuiteMethod()) {
afterSuiteMethods.put(m.getMethod(), m);
```
<br>

종속 함수

한 함수가 다른 함수를 호출한다면 두 함수는 세로로 가까이 배치한다.  
또한 가능한다면 호출하는 함수를 호출되는 함수보다 먼저 배치한다.
그러면 코드가 자연스럽게 읽힌다.

규칙을 일관적으로 적용한다면 독자는 방금 호출한 함수가 잠시 후에 정의되리라는 사실을 예측할 수 있다.

### 8.개념적 유사성
<br>

개념적인 친화도가 높을수록 코드를 가까이 배치한다.  
친화도가 높은 요인  
-한 함수가 다른 함수를 호출해 생기는 직접적인 종속성이 한 예 (부차적인 요인, 종속적인 관계가 없더라고 아래 두가지에 해당한다면 가까이 배치할 함수들이다.)  
-변수와 그 변수를 사용하는 함수(명명법이 똑같음)  
-비슷한 동작을 수행하는 함수(기본 기능이 유사)  
<br>

아래 함수들은 개념적인 친화도가 매우 높다. 명명법이 똑같고 기본 기능이 유사하고 간단하다.  
서로가 서로를 호출하는 관계는 부차적인 요인이다.   
종속적인 관계가 없더라고 가까이 배치 할 함수들이다.   

```JAVA
public class Assert {
  static public void assertTrue(String message, boolean condition) {
    if (!condition)
      fail(message);

static public void assertTrue(boolean condition) {
  assertTrue(null, condition);
}

static public void assertFalse(String message, boolean condition) {
  assertTrue(message, !condition);

static public void assertFalse(boolean condition) {
  assertFalse(message, !condition);
}
```

### 9.세로 순서
호출되는 함수를 호출하는 함수보다 나중에 배치하면 소스 코드 모듈이 고차원에서 저차원으로 자연스럽게 내려간다.
<br>

### 10.가로형식 맞추기
보통 100자에서 120자 정도가 바람직하다. 그 이상은 대부분 필요없음
<br>

### 11.가로공백과 밀집도
가로로는 공백을 사용해 밀접한 개념과 느슨한 개념을 표현한다.  
<br>

- 아래 코드를 보면 할당 연산자를 강조하려고 앞 뒤에 공백을 줬다.  
할당문은 왼쪽 요소와 오른쪽 요소가 분명히 나뉜다.  
공백을 넣으면 두 가지 주요 요소가 확실히 나뉜다는 사실이 더욱 명확해진다.  

```JAVA
private void measureLine(String line) {
  lineCount++;
  int LineSize = line.length();
  totalChars += lineSize;
  lineWidthHistogram.addLine(lineSize, lineCount);
  recordWidestLine(lineSize)
}
```
<br>

반면, 함수 이름과 이어지는 괄호 사이에는 공백을 넣지 않았다.
함수와 인수는 서로 밀접하기 때문이다.
공백을 넣으면 한 개념이 아니라 별개로 보인다.
<br>

- 연산자의 우선순위를 강조하기 위해서도 공백을 사용한다.
  
```JAVA
public class Quadratic {
private static double determinant(double a, double b, double c) {
  return b*b - 4*a*c;
}
```
<br>

수식을 읽기가 아주 편한다. 곱셈은 우선순위가 가장 높기 때문에 공백이 없다.
반면, 덧셈과 뺄셈은 우선순위가 곱셈보다 낮기 깨문에 항과 항 사이에 공백이 들어간다.
<br>

### 11.들여쓰기
소스파일은 윤곽도와 계층이 비슷하다.
범위 SCOPE로 이뤄진 계층을 표현하기 위해 우리는 코드를 들여쓴다.
들여쓰기한 파일은 구조가 한눈에 들어온다. 
<br>

### 12.팀규칙
팀은 한 가지 규칙에 합의해야 한다. 그리고 모든 팀원이 그 규칙을 따라야 한다. 그래야 소프트웨어가 일관적인 스타일을 보인다. 
한 소스차일에서 봤던 형식이 다른 소스 파일에도 쓰이리라는 신뢰감을 독자에게 줘야 한다. 
<br>


## 6장. 객체와 자료구조

#### 1. 자료 추상화 (Data Abstraction)

- 자료를 감추고(숨기고) 복잡한 내부 동작을 캡슐화하는 것을 의미한다.
- 클래스나 객체를 사용하여 데이터와 해당 데이터에 대한 동작을 하나로 묶어서 추상화한다.
- 이렇게 하면 내부 구현이 외부에 노출되지 않으며, 기능을 사용하는 사용자는 내부 동작에 대해 자세히 알 필요 없이 인터페이스만 사용할 수 있다.
<br>

- 목록 6-3 구체적인 Vehicle 클래스
- 자동자 연료 상태를 구체적인 숫자값으로 알려준다.
- 두 메소드는 자동차의 연료 탱크 용향을 갤런 단위로 반환
```JAVA
public interface Vehicle {
  double getFuelTankCapacityInGallons();
  double getGallonsOfGasoline();
}
```
<br>

- 목록 6-4 추상적인 Vehicle 클래스
-추상적인 개념인 백분율을 반환
```JAVA
public interface Vehicle {
  double getPercentFuelRemaining();
}
```
<br>

이처엄 자료를 세세하기 공개하기 보다는 추상적인 개념으로 표현하는 것이 좋다.

### 2. 자료/객체 비대칭 (Data/Object Asymmetry)
자료와 객체는 서로 다른 접근 방식을 가지고 있다.

- 자료 구조 : 데이터를 그대로 노출하고 동작이 없거나 제한적이다. (별다른 함수 제공하지 않음)
- 객체 : 추상화 뒤로 자료를 숨긴 채 자료를 다루는 함수만 공개한다.

  클린 코드에서는 객체와 자료를 사용할 때, 상황에 따라 적절하게 선택하여 사용하는 것이 중요하다.
<br>

### 3. 디미터 법칙(Law of Demeter):
디미터 법칙은 잘 알려진 휴리스틱heuristic(경험에 기반하여 문제를 해결하거나 학습하거나 발견해 내는 방법)으로, **모듈은 자신이 조작하는 객체의 속사정을 몰라야 한다는 법칙** 이다.

좀 더 정확히 표현하자면, 디미터 법칙은 “클래스 C의 메서드 f는 다음과 같은 객체의 메서드만 호출해야 한다”고 주장한다.

```
클래스 C
f가 생성한 객체
f 인수로 넘어온 객체
C 인스턴스 변수에 저장된 객체
```
하지만 위 객체에서 허용된 메서드가 반환하는 객체의 메서드는 호출하면 안 된다. 다시 말해, 낯선 사람은 경계하고 친구랑만 놀라는 의미이다.

이렇게 하면 객체들 간의 결합도가 낮아지고, 코드의 유지보수성과 재사용성을 높여준다.
의존성이 낮아야 한 요소의 변경이 다른 요소에 미치는 영향이 적고, 독립적으로 수정하거나 대체할 수 있다.
<br>

### 4. 자료 전달 객체 (Data Transfer Object, DTO):
데이터를 저장하고 전달하는 데 사용되는 단순한 데이터 구조이다.
DTO는 일반적으로 데이터베이스에서 데이터를 조회한 후, 비즈니스 로직에서 해당 데이터를 전달하거나 전송할 때 사용된다. 이렇게 하면 데이터 전송에 사용되는 객체가 간단하고 명확하게 유지되며, 데이터베이스와 비즈니스 로직 사이의 결합도가 낮아진다.
<br>

## 7장. 오류 처리


### 1. 오류 코드보다 예외를 사용하라
여기저기 흩어진 오류처리 코드때문에 실제 코드가 하는 일을 파악하기가 힘들 때가 있다.

아래는 오류 플래그를 설정하거나 호출자에게 오류 코드를 반환하는 방법이 전부였다.

```JAVA
public class DeviceController {
...
    public void sendShutDown() {
        DeviceHandle handle = getHandle(DEV1);
        //디바이스 상태를 점검한다.
        if (handle != DeviceHandle.INVALID) {
        //레코드 필드에 디바이스 상태를 저장한다.
            retrieveDeviceRecord(handle);
        //디바이스가 일시정지 상태가 아니라면 종료한다.
            if (record.getStatus() != DEVICE_SUSPENDED) {
                pauseDevice(handle);
                clearDeviceWorkQueue(handle);
                closeDevice(handle);
            } else {
                logger.log("Device suspended. Unable to shut down");
            }
        } else {
            logger.log("Invalid handle for: " + DEV1.toString());
        }
    }

 ...
}
```
<br>

위와 같은 방법을 사용하면 호출자 코드가 복잡해진다. 함수를 호출한 즉시 오류를 확인해야 하기 때문이다.

아래와 같이 오류가 발생하면 예외를 던지는 편이 낫다.   
그러면 호출자 코드가 더 깔끔해진다.  
<br>

```JAVA
public class DeviceController {
...
public void sendShutDown() {
  try {
    tryToShutDown();
  } catch (DeviceShutDownError e) {
    logger.log(e);
  }
}

private void tryToShutDown() throws DeviceShutDownError {
  DeviceHandle handle = getHandle(DEV1);
  DeviceRecord record = retrieveDeviceRecord(handle);
  pauseDevice(handle);
  clearDeviceWorkQueue(handle);
  closeDevice(handle);
}

private DeviceHandle getHandle(DeviceID id) {
  ...
  throw new DeviceShutDownError("Invalid handle for: " + id.toString());
  ...
}
...
}
```
<br>



### 2. Try-Catch-Finally 문부터 작성하라
예외가 발생할 코드를 짤 때는 try-catch-finally 문으로 시작하는 편이 낫다.
try문은 transaction처럼 동작하는 실행코드로, catch문은 try문에 관계없이 프로그램을 일관적인 상태로 유지하도록 한다.


- Step 1: 아래 코드는 예외를 던지지 않으므로 단위테스트는 실패한다.
  잘못된 파일 접근을 시도하게 구현을 변경하자. 두 번째 코드는 예외를 던진다.
  
```JAVA

@Test(expected = StorageException.class)
public void retrieveSectionShouldThrowOnInvalidFileName() {
  sectionStore.retrieveSection("invalid - file");
}

public List<RecordedGrip> retrieveSection(String sectionName) {
  // dummy return until we have a real implementation
  return new ArrayList<RecordedGrip>();
}
```

- Step 2: 코드가 예외를 던지므로 이제는 단위테스트가 성공한다.
  
```JAVA
public List<RecordedGrip> retrieveSection(String sectionName){
  try{
    FileInputStream stream = new FileInputStream(sectionName);
  } catch (Exception e) {
    throw new StorageException("retrieval error", e);
  }
  return new ArrayList<RecordedGrip>();
}
```

- Step 3: Exception의 범위를 FileNotFoundException으로 줄여 정확히 어떤 Exception이 발생한지 체크하자.

```JAVA
public List<RecordedGrip> retrieveSection(String sectionName) {
  try {
    FileInputStream stream = new FileInputStream(sectionName);
    stream.close();
  } catch (FileNotFoundException e) {
    throw new StorageException("retrieval error", e);
  }
  return new ArrayList<RecordedGrip>();
}
```

이처럼 먼저 강제로 예외를 일으키는 테스트 케이스를 작성한 후, 테스트를 통과하게 코드를 작성하는 방법을 권장한다.
<br>


### 3. 예외에 의미를 제공하라
- 예외를 던질 때는 전후 상황을 충분히 덧붙인다.
- 실패한 연산 이름과 실패 유형도 언급한다.
<br>

### 4. null을 반환하지 마라
 메소드가 null을 반환하게 된다면 메소드를 호출하는 모든 로직에서는 null 검사를 해줘야 하는데 개발자는 사람이기에 놓칠 수 있고 이는 곧 이슈로 변한다. 
 
### 5. null을 전달하지 마라
null 은 반환 뿐 아니라 인수 값으로 전달 하는 방식도 피해야 한다. 
인수값을 null을 전달하면 결국 메소드위치에서 null을 검사하는 로직을 넣어야 한다. 


## 8장. 경계
프로젝트를 진행하다 보면 오픈 소스, 다른 부서가 만들어 놓은 API, 모듈 등 외부 코드를 사용하는 경우가 대부분인데
외부 코드를 내 코드에서 호출하는 부분을 **경계(boundaries)**라고 한다.

단순하게 외부 코드를 사용하려는 곳에서 직접 호출할 수 있지만 그렇게 하는 경우는 드물고
외부 코드를 호출하는 부분을 따로 만드는 게 보편적인 방법이다.

통제가 불가능한 외부 코드에 바로 의존하지 말고 중간에 경계 클래스를 두어 그 클래스에 의존하자.
<br>

### 경계 살피고 익히기
경계 클래스를 잘 만들려면 외부 코드를 잘 사용할줄 알아야 한다.
아무 내용도 모르는 외부 코드를 어떻게 알아볼 수 있을까?

바로 우리쪽 코드에를 작성해 외부 코드를 호출하는 대신 먼저 간단한 테스트 케이스를 작성해 외부 코드를 익히면 어떨까?
짐 뉴커크는 **학습 테스트(Learning Test)**라 부른다.

학습테스트는 프로그램에서 사용하려는 방식대로 외부 API를 호출한다. 통제된 환경에서 API를 제대로 이해하는지를 확인하는 셈이다.
학습테스트는 API를 사용하려는 목적에 초점을 맞춘다.
<br>

<장점>
1. 외부 코드에 대해 정확히 알 수 있다.
2. 외부 코드가 버전이 변경됐을 때 사라지거나 변경된 코드가 있는지 알 수 있다. <- 내부 코드에 영향성을 파악할 수 있음
3. 패키지의 새 버전으로 이전하기 쉬워진다.







# Kotlin : 디모의 코틀린 강좌

## 1. 코틀린의 시작
특징
자바를 대체하기 위한 목적으로 개발된 언어로 언어적으로는 최신의 패러다임을 적용하여 자바의 몇몇 약점들을 개선하면서 기존 자바에서 사용하는 자바 가상머신과 호환될 수 있게 만들어졌다. 코틀린은 자바로 개발이 가능했던 웹서비스 안드로이드 개발뿐아니라 자바 스크립트 및 스위프트와의 연동 개발이 가능하다
코틀린은 업계에서 실제로 만은 안드로이드 개발자가 이미 코틀린으로 개발을 진행하고 있다.

개발환경
안드로이드 스튜디오, 인텔리제이가 일반적이다. 

## 2. 변수와 자료형
주석  
1. //주석 : 한줄짜리 주석  
2. /*주석 */ : 여러줄 주석  
  
코틀린은 자바와 다르게 구문이 끝나는 부분에서 세미콜론을 붙이지 않아도 된다.  
규칙만 지키면 구문이 끝나는지 언어 차원에서 판단한다.  
  
파스칼 표기법  
: 클래스 이름을 표기하는 방법으로 모든 단어는 대문자로 시작한다.  
ClassName  
  
카멜 표기법  
: 함수나 변수 이름을 표기하는 방법으로 첫단어를 제외한 모든 단어는 대문자로 시작한다.  
functionName  
  
변수 선언  
var : 언제든지 읽기 쓰기가 가능하다.  
val : 선언시에만 초기화 가능하다 중간에 값을 변경할 수 없다.  
런타임시 변경되면안되는 변수는 val로 선언하는것이 좋다.  
  
변수 호칭  
Property(속성) : 클래스에 선언된 변수  
Local variable(로컬변수) : Scope내에 선언된 변수  
  
코틀린은 기본 변수에서 null을 허용하지 않으며 초기화되지 않은 변수를 사용하면 문법에러를 발생시켜 의도치않은 동작이나 null pointer exception등을 원천적으로 차단해준다.  
변수에 값을 할당하는 것은 반드시 선언시에 할 필요는 없다.  
변수를 참조하여 사용하기 전까지만 할당하면 된다.  
ex)  
var a: Int  
a = 123  

그러나 프로그램에 따라 변수에 값이 할당되지 않았음을 하나의 정보로 사용하는 경우도 있다. 이런 경우 변수형 뒤에 ?를 붙이면 null을 혀용하는 nullable 변수로 선언할 수 있다.  
ex)  
var a: Int? = null  

nullable 변수는 값이 null인 상태로 연산할시 null pointer exception이 발생할 수 있으므로 꼭 필요한 경우에만 사용하는 것이 좋다.  
  
기본자료형(primitive type)  
자바와의 호환을 위해 자바와 거의 동일하다. 

코틀린은 8진수의 표기는 지원하지 않는다.  
실수표기법  
var doubleValue: Double = 123.5  
var doubleValueWithExp: Double = 123.5e10  
var floatValue: Float = 123.5f  
  
기본적으로 Double형을 사용하며 필요시 지수표기법을 추가해줘도 된다.  
Float형인 경우 소문자 또는 대문자 f를 붙여줘야한다.  
  
문자형  
var charValue: Char = “a’  
  
코틀린은 유니코드 인코딩 중에 한 방식인 UTF-16 BE로 관리해서 한 문자당 2byte를 차지한다.  
  
문자열  
var stringValue = “one line string test” // 한줄의 문자열 표기법  
val multiLineStringValue = “”“ multiline  
string  
test“”“ //두 줄 이상의 문자열 표기법  
  
논리형  
var booleanValue: Boolean = true  
  
## 3. 형변환과 배열
형변환(type casting)  
하나의 변수에 지정된 자료형을 호환되는 다른 자료형으로 변환하는 기능이다.   
  
기본자료형들은 자료형 간의 형변환을 지원하기 위해 형변환 함수들을 제공하고 있다.  
toByte(), toShort(), toInt(), toLong(), toFloat(), toDouble(), toChar()등이 있는데  
to<자료형>()의 형태이다.  
  
var a: Int = 54321
var b: Long = a.toLong()

전문용어로는 명시적 형변환이라고 한다. 코틀린은 형변환시 발생할 수 있는 오류를 막기 위해 다른 언어들이 지원하는 암시적 형변환은 지원하지 않는다.  
명시적 형변환은 변환될 자료형을 개발자가 직접 지정하는 것이고  
암싲거 형변환은 변수를 할당시 자료형을 지정하지 않아도 자동으로 현 변환이 된다.  
  
배열  
var intArr = arrayOf(1, 2, 3, 4, 5)  

만약 특정한 크기의 공간을 가지는 비어있는 배열을 만들고 싶으면 다음과 같이 선언한다.  
var nullArr = arrayOfNulls<Int>(5)  
이렇게 선언하면 5개의 공간이 null로 채워진 배열이 생성된다.  
<> 안에는 배열에 할당할 자료형을 지정해주면 된다. 이를 제너릭이라고 한다  
	
배열에 값을 할당하거나 사용하려면 다른 언어들처럼 배열이름[index] 후 할당하거나 참조할 수 있다.   
intArr[0] = 12  
배열은 한번 크기를 지정하면 변경할 수 없다는 단점이 있지만  
한번 선언 빠른 입출력이 가능하다는 장점이 있다.  
 
   
## 4. 타입추론과 함수  
  
타입 추론(type inference)  
: 변수나 함수들을 선언할 때나 연산할때 자료형을 코드에 명시하지 않아도 코틀린이 자료형을 추론해준다.  
  
val stringValue(: String) = “문자열을 할당해볼까요?”  
var intArr(: Array<Int>) = arrayOf(1,2,3,4,5)  
처럼 자료형을 생략할 수 있다.  

변수가 선언될때 할당된 값의 형태로 해당 변수가 어떤 변수가 어떤 자료형을 가지는지 추론이 가능하기 때문에 이가 가능하다.  
  
기본 자료형도 선언시 값을 할당만 해준다면 대부분 자료형을 명시할 필요가 없다.  
자료형 없이 값을 할당한다면 어떠한 자료형으로 선언될까??  

var a = 1234 // Int  
var b = 1234L // Long  
var c = 12.45 // Double  
var d = 12.45f // Float  
var g = true // boolean  
var h = ‘c’ // char  
  
반드시 특별한 자료형이 아니라면 코틀린의 타입 추론을 이용하여 코드량을 줄일 수 있다.  
  
함수(function)  
함수는 특정한 동작을 하거나 원하는 결과값을 연산하는데 사용되는 기능  
main(), println() 등 많은 함수들이있다.  
코틀린에서 함수는 어디에나 둘수 있다.  
함수는 fun으로 시작한다.  
fun main(){  
	println(add(5,6,7))  
}  
  
fun add(a:Int, b: Int, c: Int): Int{// 반환형은 함수 맨 뒤에 선언한다. 반환값이 없으면 생략가능  
	return a+b+c  
}  
  
단일 표현식 함수(single-expression function)  
  
방금 만든 add함수를 마치 변수에 결과값에 할당하듯  
fun add(a: Int, b: Int, c: Int) = a+b+c  
처럼 만들 수 있다.  
또한 단일 표현식 함수에서 반환형의 타입 추론이 가능해서 반환형을 생략할 수 있다.  
  
코틀린에서 함수는 내부적으로 기능을 가진 형태이지만 외부에서 볼때는 파라미터를 넣는다는 점 외에는 자료형이 결정된 변수라는 개념으로 접근하시는 것이 좋다.  
그래야 이후에 배울 함수형 언어라는 코틀린의 중요한 특징을 이해하기 쉽다.  
  
## 5. 조건문과 비교연산자
if 만약 ~ 한다면 if문에 주어진 값이 참이라면 따라오는 구문을 실행하는 기능이다.  
  
fun main(){  
	var a = 7  
  
	if(a > 10){  
	println(“참”)  
	}   
}  
  
위 코드는 아무것도 실행되지 않는다.  
  
fun main(){  
	var a = 7  
  
	if(a > 10){  
		println(“참”)  
	} else {  
		println(“거짓”)  
	}  
}  
예외구문의 처리를 위한 방법으로 if문 뒤에 else를 붙여서 실행 구문을 넣어주면 된다.  
조건문을 처리할 수 있는 연산자는  
<, <= >, >=, !=, == 등이 있다.  
is 연산자도 있는데 이는 자료형이 맞는지 확인하는 연산자이다. 형변환도 시켜준다.  
ex ) a is Int  

When  
다른 언어에서의 Switch 문과 비슷한 함수이다.  
  
fun doWhen(a: Any){  
	when(a){  
		1 -> println(“정수 1입니다.”)  
		“DiMo” -> println(“디모의 코틀린 강좌입니다..”)  
		is Long -> println(“Long 타입입니다.”)  
		!is String -> println(“String 타입이 아닙니다”)  
		else -> println(“어떤 조건도 만족하지 않습니다.”)  
}  
  
여기서 Any 자료형은 모든 자료형을 호환할 수 있는 코틀린의 최상위 자료형이다.  
등호나 부등호의 사용은 불가능하다!!  
여러개의 조건이 만족할 경우 맨처음 만나는 조건문의 코드를 실행하고 when문을 탈출한다.  
  
fun doWen(a: Any){  
	var result = when(a) {  
		1-> “정수입니다.”  
		“DiMo” -> “디모의 코틀린 강좌입니다.”  
		is Long -> “Long 타입입니다.”  
		!is String -> “String 타입이 아닙니다.”  
		!is String -> “String 타입이 아닙니다.”  
		else -> “어떤 조건도 만족하지 않습니다.”  
		}  
	println(result)  
}  
  
이 코드를 실행하면 result에 -> 뒤에 있는 값이 result에 할당된다.  
  
## 6. 반복문과 증감연산자
  
반복문에는 두가지 타입이 있다.  
조건이 참인 경우 반복을 유지하는 조건형 반복문과  
반복 범위를 정해 반복을 수행하는 범위형 반복문이 있다.  
  
조건형 반복문은 while과 dowhile이 있다.  
  
fun main(){  
	var a = 0  
	while(a<5){  
		println(a++)  
	}  
}  

a++에서 증가 연산자인 ++을 볼 수 있는데 이는 변수의 값을 ‘1’ 증가시켜주는 역할을 한다.  
감소 연산자도 존재하는데(--) 이는 증가연산자와 반대로 변수의 값을 ‘1’ 감소시켜주는 역할을 한다. 이 두 개를 통칭하여 증감연산자라고 한다.   
  
앞에 붙이는것과 뒤에 붙이는 것의 차이  
앞에 붙이면 전위 연산자(prefix operators)라고 하며 연산자가 변수 앞에 연산자가 있는 경우인데 이는 해당 코드를 실행하기전 증감연산을 하고 해당 연산이 진행되는 반면  
뒤에 붙이게 되면 후위 연산자(postfix operators)라고 하여 연산자가 변수 뒤에 연산자가 있는 경우인데 이는 해당 코드가 실행되고 난 후 해당 변수의 값을 증감한다.  
  
do..while  
while에 의해 조건을 체크하여 반복한다는 점은 같지만 최초 한번은 조건에 상관없이 수행하고 while문의 조건을 확인한다.  
  
범위형 반복문에는 for가 있다.  
for의 사용법은 고전적인 언어들과 사뭇 다르다.  
  
fun main(){  
	for(i in 0..9){  
		print(i)	  
	}  
}  

for 문을 쓰고 index로 사용할 변수를 적는다. 그 뒤에 in 0..9 를 적으면 0에서 9까지 반복이 되며 이 수들이 i에 할당된다.  
  
증가값을 1이 아닌 다른 수로 지정할 경우 옵션으로 step을 붙여주면된다.  
  
fun main(){  
	for(i in 0..9 step 3){  
		print(i)	  
	}  
}  
[출력]  
0369  
  
감소시키는 경우 .. 이 아닌 downTo 를 사용한다.  
  
fun main(){  
	for(i in 9 downTo 0){  
		print(i)  
	}  
}  
[출력]  
9876543210  
  
감소 역시 step을 붙이면 감소값을 지정할 수 있다.  
  
for의 범위로 char형을 사용할 수 도 있다.  
  
fun main(){  
	for(i in ‘a’ .. ‘e’) {  
		print(i)  
	}  
}  
[출력]  
abced  
   
## 7. 흐름제어와 논리연산자  
return  
함수를 배울때 언급했듯이 ‘함수를 종료’하고 값을 ‘반환’하는 역할을 한다.  
  
break  
반복문 내애 구문이 실행이 되는 도중, 반복문을 중단하고 다음 구문으로 넘어가는 역할을 한다.  

fun main(){  
	for( i in 1.. 10){  
		if(i==3) break  
		print(i)  
	}  
}  
[출력]  
12  

continue  
다음 반복 조건으로 즉시 넘어가는 역할을 한다.  
  
fun main(){  
	for( i in 1.. 10){  
		if(i==3) continue  
		print(i)  
	}  
}  
[출력]  
1245678910  
  
코틀린은 다른언어와 다르게 다중 반복문의 흐름제어도 가능하다.  
외부 반복문에 레이블 이름과 @ 기호를 달고 break문에서 @ 과 레이블 이름을 달아주면  
레이블이 달린 반복문을 기준으로 즉시 break를 시켜준다. continue도 마찬가지이다.  
 
fun main() {  
	loop@for(i in 1..10) {  
		for(j in 1..10) {  
			if(i == 1 && j == 2) break@loop  
			println(“i : $i, j : $j”)  
		}  
	}  
}  
[출력]  
i : 1, j : 1  
  
따음표 안에서 변수를 출력할때는 변수이름 앞에 $를 붙여주면 변수의 값이 출력된다.  
  
논리연산자(logical operators)  
논리값을 연산하여 새로운 논리값을 도출할 때 쓰는 연산자이다.  
and 연산 : &&  
or 연산 : ||  
not 연산 : !  

fun main(){    
	println(true && false)  
	println(true || false)  
	println(!true)  
	println(!false)  
}   
[출력]  
false  
true  
false  
true   

``` 
람다식
```

[02] 람다식                                                        
\1. 함수형 프로그래밍과 람다식
\- 자바는 객체지향 언어로 클래스를 만들고 클래스안의 메소드에
 기능을 구현하고 메소드를 호출한다. 
\- 프로그래밍 중 클래스 없이 함수를 구현하고 호출하는 방법이다.
\- 자바는 자바8 부터 함수형 프로그래밍을 지원한다.
\- 자바에서 제공하는 함수형 프로그래밍 방식을 람다식(Lambda expression)이라 한다.

\2. 람다식 구현하기
\- 람다식은 함수 이름이 없는 익명함수를 만드는 것이다.
\- (매개변수) -> {실행문;} 으로 표현 한다.

int add(int x, int y) {
   return x + y     => (int x, int y) -> {return x+y;}
}

\3. 람다식 문법
(1) 매개변수 자료형과 괄호 생략
\- 람다식에서는 매개변수 자료형을 생략할 수 있다.
\- 매개변수가 하나인경우는 괄호도 생략할 수 있다.
 str -> {System.out.println(str);}
\- 매개변수가 두개인 경우는 괄호를 생략할 수 없다.

(2) 중괄호 생략
\- 중괄호 안의 구현 부분이 한 문장인 경우 중괄호를 생략할 수 있다.
 str -> System.out.println(str);
\- 중괄호 안의 구현부분이 한 문장이라도 return문이 있으면 중괄호를 생략할 없다.

(3) return 생략
\- 중괄호 안의 구현 부분이 return문만 있다면 중괄호와 return을 모두 생략하고
 식만 쓴다.
(x, y) -> x + y;  -> {return x + y;}
str -> str.length(); ->{return str.length();}

\4. 람다식 사용
(1) 함수형 인터페이스 
\- 람다식을 구현할 추상 메소드 선언
\- MyNumber 인터페이스에 getMax() 추상메소드 선언

\>>> MyNumber.java



package lambda;

 

@FunctionalInterface

public interface MyNumber {

 

  int getMax(int num1, int num2);

}

 


(2) 람다식 구현과 호출
\- MyNumber 인터페이스형 변수(max)에 람다식을 대입한다.
\- MyNumber 타입인 max의 getMax()를 호출 한다.

\>>> TestMyNumber.java


package lambda;

 

public class TestMyNumber {

 

  public static void main(String[] args) {

​    MyNumber max = (x, y)->(x>= y)? x:y; // 람다식을 인터페이스 자료형 max 변수에 대입

 

​    System.out.println(max.getMax(10, 20));// 인터페이스 자료형 변수로 함수 호출

​    

  }

}


\5. 함수형 인터페이스
\- 람다식 구현을 위해 함수형 인터페이스를 만들고, 인터페이스에 람다식 메서드를 대입한다.
\- 람다식은 하나의 메서드를 구현하여 인터페이스형 변수에 대입된다.
\- 함수형 인터페이스는 두 개 이상의 메서드를 가질 수 없다.

(1) @FunctionalInterface 애노테이션
\- 실수로 메서드를 하나 이상 선언하면 오류가 나도록 한다.
\- 함수형 인터페이스를 명시적으로 표현한다. 
\- 애노테이션을 생략해도 된다.

package lambda;

 

@FunctionalInterface

public interface MyNumber {

  

  int getMax(int num1, int num2);

   int getAdd(int num1, int num2);

}


\6. 객체지향 프로그래밍 방식과 람다식 비교
\- 람다식을 사용하면 기존 방식보다 간결한 코드를 구현할 수 있다.
\- 메소드의 구현부를 클래스에 만들고, 이를 다시 인스턴스로 생성하고 호출하는
 코드가 줄어들기 때문이다.

\- 공통 인터페이스 생성

\>>> StringConcat .java

package lambda;

 

public interface StringConcat {

 

   void makeString(String s1, String s2);

 

}

(1) 클래스에서 인터페이스 구현
\- 인터페이스를 구현한 클래스 생성후 추상메소드 재정의한다.
\- 클래스를 테스트하는 프로그램을 작성한다.

\>>>StringConCatImpl.java

package lambda;

 

public class StringConCatImpl implements StringConcat{

 

 @Override

 public void makeString(String s1, String s2) {

  System.out.println( s1 + "," + s2 );

 }

} 

\>>>TestStringConcat.java

package lambda;

 

public class TestStringConcat {

 

  public static void main(String[] args) {

 

​    String s1 = "Hello";

​    String s2 = "World";

​    StringConCatImpl concat1 = new StringConCatImpl();

​    concat1.makeString(s1, s2);

 }
}

(2) 람다식으로 인터페이스 구현
\- 람다식으로 인터페이스 구현시 클래스를 따로 생성할 필요없이 바로 메서드를
 구현한다.

\>>> TestStringConcat.java



package lambda;

 

public class TestStringConcat {

 

  public static void main(String[] args) {

 

​    String s1 = "Hello";

​    String s2 = "World";

​    

​    StringConcat concat2 = (s, v)->System.out.println(s + "," + v );
 

​    concat2.makeString(s1, s2);

 

  }

}

 


\7. 익명 객체를 생성하는 람다식   
\- 람다식은 객체 없이 인터페이스의 구현만으로 메서드를 호출한다.
\- 람다식으로 메서드를 구현해서 호출하면 컴퓨터 내부적으로 아래처럼 익명 클래스가
 생성되고 이를 통해 익명 객체가 생성되는 것이다.



StringConcat concat3 = new StringConcat() {

 

 @Override

 public void makeString(String s1, String s2) {

 

   System.out.println( s1 + "," + s2 );

 }

};    

(1) 람다식에서 사용하는 지역변수 
 \- 메인메소드의 지역변수 i는 익명의 내부클래스에서 사용할 수는 있지만 수정은 할 수
  없다. 
 \- 익명 내부클래스에서 외부 메서드의 지역변수는 상수가 된다. 이 변수를 변경하려고
  하면 오류가 난다.



int i = 100;

 

StringConcat concat2 = (s, v)->{

 System.out.println(s + "," + v ); 

 // i = 30; //오류남

};                                                                                         
\8. 함수를 변수처럼 사용하는 람다식 
\- 람다식을 이용하면 구현된 함수를 변수처럼 사용할 수 있다.
\- 람다식으로 구현된 메서드도 변수에 대입하여 사용할 수 있고,
 매개변수로 전달하고 반환할 수 있다.

(1) 인터페이스형 변수에 람다식 대입하기



package lambda;

 

interface PrintString{

  

  void showString(String str);

}

 

public class TestLambda {

 

  public static void main(String[] args) {

 

​    PrintString lambdaStr = s->System.out.println(s); //람다식을 변수에 대입

​    lambdaStr.showString("hello lambda_1");

​    

 }
}


(2) 매개변수로 전달하는 람다식
\- 람다식을 변수에 대입하면 이를 매개변수로 전달할 수 있다. 
\- 이 때 전달되는 매개변수의 자료형은 인터페이스형이다.



package lambda;

 

interface PrintString{

  

  void showString(String str);

}

 

public class TestLambda {

 

  public static void main(String[] args) {

 

​    PrintString lambdaStr = s->System.out.println(s); //람다식을 변수에 대입

​    lambdaStr.showString("hello lambda_1");

​    

​    showMyString(lambdaStr);             //메서드 매개변수로 전달

​       

  }

  

  public static void showMyString(PrintString p) {

​    p.showString("hello lambda_2");

  }

}

(3) 반환 값으로 쓰이는 람다식
\- 메서드의 반환형을 람다식의 인터페이스형으로 선언하면 구현한 람다식을 반환할 
 수 있다.

package lambda;

 

interface PrintString{

  

  void showString(String str);

}

 

public class TestLambda {

 

  public static void main(String[] args) {

 

​    PrintString lambdaStr = s->System.out.println(s); //람다식을 변수에 대입

​    lambdaStr.showString("hello lambda_1");

​    

​    showMyString(lambdaStr);             //메서드 매개변수로 전달

​    

​    PrintString reStr = returnString(); 

​    reStr.showString("hello ");

​    

  }

  

  public static void showMyString(PrintString p) {

​    p.showString("hello lambda_2");

  }

  

  public static PrintString returnString() {     //반환 값으로 사용

​    return s->System.out.println(s + "world");

  }

}

 
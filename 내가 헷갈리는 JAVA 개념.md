# 내가 헷갈리는 JAVA 개념



#### 연산자



[](http://lectureblue.pe.kr/ckstorage/images/java/04/java04-01.jpg)

\8. 삼항 연산자 

\>>>>> Ternary.java 
class Ternary 
{ 
  public static void main(String args[]) 
  { 
    int x = 10; 
    int y; 
     
    //System.out.println("결과는 " + y); 

​    //System.out.println("초기화되지 않은 y의 값: " + y); 
​    //y = 조건문 ? 참값 : 거짓값 
​    y = x < 9 ? 3 : 5; 
​    System.out.println("결과는 " + y); 
  } 
} 

#### 분기문 (If,Switch)문

 \- 조건에 따라 분기를 할 수 있습니다. 
   \- if (조건식){ 
      참일 경우 실행; 
      참일 경우 실행; 
   } else{ 
      거짓일 경우 실행 
   } 
    

* EX)If

class IfTest1 {              

 public static void main(String[] args) {

  int i = 120;

 

  // 참일 경우만 처리, 거짓은 무시

  if (i % 2 == 0) {           

   int count = 1;

   System.out.println(i + "은(는) 짝수");

  }

 

  // System.out.println("count: " + count);

  

  // else를 통한 참, 거짓 구분 처리

  if (i % 2 == 0) {

   System.out.println("짝수 " + i); // 참

  } else {

   System.out.println("홀수 " + i); // 거짓

  }

 

  // 조건에 걸릴때까지 계속적인 검사, 다중 IF

  if (i % 3 == 0) {

   System.out.println("3의 배수");

  } else if (i % 4 == 0) {

   System.out.println("4의 배수");

  } else if (i % 7 == 0) {

   System.out.println("7의 배수");

  } else {

 

   System.out.println("3, 4, 7의 배수가 아닙니다.");

  }

  

  if ( 1 == 1) System.out.println("동일");  // X

  

  if ( 2 == 2)

  System.out.println("동일");        // X

  

  if ( 3 == 3){

   

   System.out.println("동일");      

   

  }

 }

}

-------------------------------------------------------------------------------------------

  public static void main(String[] args) { 
    int year = 5;     //근무(경력) 년수 
    int child = 0;    //자녀수 
    int pay = 1500000;  //초봉 기본급 
     

    if (year == 0){ 
      System.out.println("신입사원입니다.");   
    }else if (year == 1) { 
      pay = pay + 200000; 
      System.out.println("경력 1년 입니다."); 
    }else if(year == 2) { 
      pay = pay + 400000; 
    }else if(year == 3) { 
      pay = pay + 600000; 
    }else if(year == 4) { 
      pay = pay + 800000; 
    }else{ 
      pay = pay + 1500000; 
    } 
     
    //자녀수당을 계산합니다. 
    if ( year >=1){ 
      if (child > 1){ 
        pay = pay + (child * 200000); 
      } 
    } 
     
    System.out.println("기본급: " + pay); 
    System.out.println("연 봉: " + (pay * 13)); 
    System.out.println("월급여: " + ((pay * 13)/12)); 
  } 
} 



#### 분기문 Switch 문 

 \- 수식의 결과가 일정한 수치 형태로 나열되어 있는 값과 비교하는 경우 
    사용합니다. 
   \- case문에 올수 있는 데이터 타입은 byte, char, short, int, long처럼 정수
    형태만 올 수 있습니다. 



public class SwitchTest2{ 
  public static void main(String args[]){ 
    char c = 'C'; 
    String str = "C"; 
     
    switch(c){ //정수 계열만 가능 
      case 'A': //65 
        System.out.println("입력된 코드는 A 입니다."); 
        break; 
      case 'B': //66 
        System.out.println("입력된 코드는 B 입니다."); 
        break; 
      case 'C': 
        System.out.println("입력된 코드는 C 입니다."); 
        break; 
      case 'D': 
        System.out.println("입력된 코드는 D 입니다."); 
        break; 
      default: 
        System.out.println("코드는 A부터 D까지 입력해야 합니다."); 
        break; 
    } 
  } 
} 



\>>>> Switch를 이용한 실습예제 2 

점수       출력 내용 
================================ 
100 
99~90      등급은 A입니다. 
89~80         B 
79~70         C 
69~60         D 
59 이하     노력하세요. 










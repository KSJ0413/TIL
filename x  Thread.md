```
 Thread 
```

[01] Thread 
  \- 하나의 프로그램에서 여러 개를 동시에 처리하는 기능
  \- 우리가 일반적을으로 사용하는 프로그램은 한 프로그램에서 하나씩 순차적으로 
   처리되는 방식이다. 즉 작업1이 완료된 뒤 작업 2가 처리된다.
  \- 스레드는 작업1과 작업2가 동시에 처리될 수 있다.

 (http://lectureblue.pe.kr/ckstorage/images/java/22/1.jpg)

  \- Process
   . thread의 집합으로 하나의 exe, com, dll 프로그램을 말한다. 
   . 현재 실행되고 있는 프로그램이다. 
   . Process간 자원(memory)을 공유할 수 없다. 따라서 Process를 많이 발생 시키면 
    자원이 바닥나게 된다.
 
 \- Thread
  . 독립된 작업처리 단위로 프로세스를 구성한다.
  . 메소드(함수)단위의 처리 모듈 이며 process의 구성 요소이다.
  . Thread는 많이 발생해도 자원을 공유함으로 Process에 비해 시스템에 적은 
   부담이 된다. 
  . 스레드 스케줄러에 의해서 스레드의 여러상태중 실행상태로 변경할 수 있다.
  . 스레드의 상태는 준비상태, 실행상태, 대기상태, 정지상태가 있다.
 
 \- run()메소드안에 처리로직을 구현하거나 처리로직을 호출하는 로직이 구현되어있다.
 \- 네크워크, 게임, 데이터베이스, 웹 관련 프로그램에서 많이 사용된다. 
 \- 자바의 스레드는 많은 Reference 참조로 인해 C언어의 스레드보다 속도 및
  안정성이 떨어져 접속자가 많은 네트워크 관련 프로그램에 사용을 하지 않는다. 
  . Hash Code 관리 부분에 많은 리소스가 소모된다.

 \- thread의 상태 
[http://www.lectureblue.pe.kr/ckstorage/images/java/22/java22_01.jpg](http://lectureblue.pe.kr/ckstorage/images/java/22/java22_01.jpg)

\1. 스레드 콜백 메소드와 기본 메소드 
 \- start(): 
  . 스레드를 스레드 스케줄러에 등록하고 준비상태에서 실행을 기다린다.
  . 이 메소드를 실행했다고해서 바로 스레드가 실행이 되는 것은 아님
  . JVM은 스레드를 실행할 수 있는 여유가 생겼을 때 자신이 작성한 스레드 스케줄러에 
  의해서 스레드의 run()메소드를 호출한다.

 \- run(): JVM이 호출하는 콜백메소드로 여기서 콜백 메소드는 개발자가 호출을 코드상에 
  지시 하는 것이 아니라 JVM이 호출하는 메소드를 말하는 것으로 이 run()메소드 안에는 
  스레드 상태 에서 처리하려고 하는 모든 비즈니스 로직이 구현되어 있어야 하며 가장 
  중요한 메소드이다. 

 \- sleep(long milli second): 지정된 시간동안 스레드를 쉬게하고, 그 시간이 지나면 
  다시 쓰레드가 작동된다. (천 분의 1초)
 \- wait(): 현재를 스레드 무한정 대기 시킵니다. notify(), notifyall() 메소드를 통해서 
  재 실행 가능. 
 \- suspend():스레드의 실행을 일시적으로 중단 시킴,  다시 실행은 resume()를 
  통해서만 가능. 
 \- yield(): 스레드의 실행 권한을 무조건 다른 스레드에게 넘겨 준다.(양보) 
 \- stop(): 스레드 실행을 완전히 종료 한다.
 \- getName(): 쓰레드의 이름을 알려줍다.
 \- Thread.currentThread()는 현재 실행중인 쓰레드를 알려준다. 

\2. 단일 스레드: 
 \- 하나의 프로세스가 하나의 쓰레드로 실행되는 환경을 말함.
 \- main() 메소드가 대표적인 단일 스레드이며, 프로세스에서 디폴트로 할당되는 스레드이다.
 \- 모든 프로세스는 최소한 하나의 쓰레드를 가지게 되며 메인 쓰레드에서 더이상
  새로운 쓰레드를 생성하지 않았다면 이 프로세스는 단일 쓰레드 환경이 된다.

\3. 멀티 스레드:
 \- 하나의 프로세스에 두개 이상의 쓰레드가 존재하는 것을 말함.
 \- 하나의 메소드가 처리가 끝나는 것이 아니라 여러 메소드가 계속적으로 실행상태에 
  있으면서 자원을 공유하고 이용하는 처리 형태

\4. 스레드의 생성 방법 
 \- Thread 클래스를 상속받는 방법 
 \- Runnable 인터페이스를 구현하는 방법 
  . 자바는 다중 상속이 안됨으로 클래스가 특정 클래스를 상속할 필요가 있는 경우는 반드시
   Runnable인터페이스를 구현해야 한다. 

\5. 스레드 실습 

(1) 스레드를 이용하지 않은 경우 
\>>>>> NonThread.java
class GenClass{ 
  private int num; 
  private String name; 
   
  public GenClass(String a, int b){ //생성자 
    name = a; 
    num = b; 
  } 
   
  public void start(){ 
    for(int i=0; i<num; i++){
      System.out.println(name + " : " + i); 
    } 
  }
} 
 
public class NonThread{ 
  public static void main(String args[]) { 
    GenClass t1 = new GenClass("first", 5); 
    GenClass t2 = new GenClass("second", 5); 
    GenClass t3 = new GenClass("third", 5); 
 
    t1.start();  
    t2.start();  
    t3.start();      
  } 
} 
 
(2) Thread 클래스를 상속받은 경우
   java.lang.Object 
   | 
   +--java.lang.Thread 
    | 
    +--MyThread.java 


![img](http://lectureblue.pe.kr/ckstorage/images/java/22/2.jpg)

\>>>>> ThreadTest1.java 
class MyThread extends Thread{ 
  private int num; 
  private String name; 
   
  public MyThread(String a, int b) { 
    name = a; 
    num = b; 
  } 
   
  public void run() { //Callback 메소드 
    for(int i=0; i<num ; i++){
      System.out.println(name + " : " + i); 
    } 
  } 
}
public class ThreadTest1{ 
  public static void main(String args[]) { 
    MyThread t1 = new MyThread("first", 1000); 
    MyThread t2 = new MyThread("second", 1000); 
    MyThread t3 = new MyThread("third", 1000); 

​    t1.start(); 
​    t2.start(); 
​    t3.start();     
  } 
} 


(3) Runnable 인터페이스를 사용한 경우 
 \- Thread 클래스외에 다른 클래스를 상속받는 경우는 Runnable 인터페이스를 사용한다.

![img](http://lectureblue.pe.kr/ckstorage/images/java/22/3.jpg)

\>>>>> ThreadTest2.java 
class ThreadOne implements Runnable { 
  private int num; 
  private String name; 
  public ThreadOne(String a, int b) { 
    name = a; 
    num = b; 
  } 
     public void run(){ 
    for(int i=0; i<num;i++)
      System.out.println(name + " : " + i); 
  } 
} 
public class ThreadTest2{ 
  public static void main(String args[]) { 
    //Runnable Interface를 구현한 클래스 객체를 
    //Thread 클래스의 생성자로 할당합니다. 
    Thread t1 = new Thread(new ThreadOne("first", 1000)); 
    Thread t2 = new Thread(new ThreadOne("second", 1000)); 
    Thread t3 = new Thread(new ThreadOne("third", 1000)); 
    t1.start();     
    t2.start(); 
    t3.start(); 
  } 
} 



 

 

(3) 스레드와 sleep 메서드  
 \- sleep()를 적용한 경우 특정 스레드의 CPU자원이 집중하는 것을 막을 수 있다.
\>>>>> SchedulingTest2.java 

class RunThread2 extends Thread {  
  public RunThread2(String name) { 
    super(name); 
  } 
  public void run() { 
    for ( int i = 1; i <= 30000000 ; i++ ) { 
      if ( i % 50 == 0 ){ 
        System.out.println("Thread [" + getName() + "] : " + i); 
        try{ 
          //sleep(1); //0.001초 
          System.out.print(""); 
        }catch(Exception e){ } 
      } 
    } 
  }   
} 
public class SchedulingTest2 { 
  public static void main(String args[]) { 
    Thread[] t = new RunThread2[5]; 
    t[0] = new RunThread2("☆"); 
    t[1] = new RunThread2("★");  
    t[2] = new RunThread2("◆"); 
    t[3] = new RunThread2("◇"); 
    t[4] = new RunThread2("○"); 
     
    t[0].start(); 
    t[1].start(); 
    t[2].start();     
    t[3].start(); 
    t[4].start(); 
  } 
} 



\>>>>> SleepThread.java

class  SleepThread extends Thread{ 

  public SleepThread(String name){ 

​    setName(name); 

  } 

  public void run(){show();} 

  public void show(){ 

​    for(int i=0 ;i<50;i++){ 

​      print(); 

​        try{ 

​        Thread.sleep(50);//50/1000 초 

​      }catch(InterruptedException ite){} 

​    } 

  } 

  public void print(){ 

​    System.out.print(getName());//Thread에서  

  } 

} 

 

public class  SleepThreadMain{ 

  public static void main(String[] args) { 

​    SleepThread t1=new SleepThread("a"); 

​    SleepThread t2=new SleepThread("b"); 

​    SleepThread t3=new SleepThread("c"); 

​    t2.setPriority(7);//1~10 클수록 우선순의 높음

​    t1.start();//t2가 t1보다 우선이지만 

​    try{ 

​      t1.join();//t1을 끝낸후 t2, t3를 실행한다. 

​    }catch(InterruptedException ite){} 

​    t2.start(); 

​    t3.start(); 

  } 

} 
 



\6. 우선순위 

  \- setPriority(int p): 현재 스레드의 우선순위를 인자 p로 설정하기 위한 메소드 
  \- getPriority(): 현재 스레드의 우선순위를 반환하는 메소드 
  \- Thread.MAX_PRIORITY  10 
  \- Thread.NORM_PRIORITY 5 
  \- Thread.MIN_PRIORITY  1 
  \- sleep()의 이용, 우선순위가 적용은 되나 다른 스레드에게 제어권이 자주 넘어감 

\>>>>> SchedulingTest4.java 
class RunThread4 extends Thread {  
  public RunThread4(String name) { 
    super(name); 
  } 
  public void run() { 
    for ( int i = 1; i <= 10000 ; i++ ) { 
      if ( i % 50 == 0 ) 
        System.out.println("Thread [" + getName() + "] : " + i); 

​      try{ 
​        sleep(1); //0.001초 
​      }catch(InterruptedException e){ } 

​    } 
  }   
} 
public class SchedulingTest4 { 
  public static void main(String args[]) { 
​    Thread[] t = new RunThread4[3]; 
​    t[0] = new RunThread4("☆"); 
​    t[1] = new RunThread4("◑"); 
​    t[2] = new RunThread4("○");     
​    t[0].start(); 
​    t[0].setPriority(1); 
​    t[1].start(); 
​    t[1].setPriority(5); 
​    t[2].start();     
​    t[2].setPriority(10); 
​    /* 
​    System.out.println("t[0]" + t[0].getPriority()); 
​    System.out.println("t[1]" + t[1].getPriority()); 
​    System.out.println("t[2]" + t[2].getPriority()); 
​    */     
  } 
} 

\7. 내부 클래스를 이용하여 스레드 구현
 \- 클래스 안에 선언된 클래스를 내부 클래스(inner class)라 한다.
 \- 클래스안의 메소드에 선언된 것을 지역 내부 클래스(local inner class)라고 한다.
 \- main()안에서 선언된 class는 main() 메소드 안에서만 사용할 수 있고 외부에서는
  사용할 수 없다.
 \- 내부 클래스는 컴파일된 후에 '외부클래스이름$내부클래스이름.class' 형식으로
  바이트 코드가 생성된다.

(1) 스레드로 3대의 자동차 작동하기


public class Ex14_08 {

  public static void main(String[] args) {

 

​    class Car extends Thread {

​      String carName;

 

​      Car(String carName) {

​        this.carName = carName;

​      }

 

​      public void run() {

​        for (int i = 0; i < 3; i++) {

​          try {

​            Thread.sleep(10);

​            System.out.println(carName + "~~ 달립니다.");

 

​          } catch (Exception e) {

​          }

​        }

​      }

​    }

 

​    Car car1 = new Car("$자동차1");

​    car1.start();

 

​    Car car2 = new Car("@자동차2");

​    car2.start();

 

​    Car car3 = new Car("*자동차3");

​    car3.start();

  }

}

 


(2) Runnable 인터페이스로 3대의 자동차 작동하기



public class Ex14_09 {

  public static void main(String[] args) {

 

​    class Car {

​      String carName;

​    }

​    

​    class Truck extends Car implements Runnable {

​      Truck(String carName) {

​        this.carName = carName;

​      }

​      

​      public void run() {

​        for (int i = 0; i < 3; i++) {

​          try {

​            Thread.sleep(10);

​            System.out.println(carName + "~~ 달립니다.");

 

​          } catch (Exception e) {

​          }

​        }

​      }

​    }

 

​    Truck car1 = new Truck("$트럭1");

​    Thread truck1 = new Thread(car1);

​    truck1.start();

 

​    Truck car2 = new Truck("@트럭2");

​    Thread truck2 = new Thread(car2);

​    truck2.start();

 

​    Truck car3 = new Truck("*트럭3");

​    Thread truck3 = new Thread(car3);

​    truck3.start();

  }

}

 
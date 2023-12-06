# interview-question
> 실제 기술 면접에서 받은 질문들을 저장하는 문서 입니다.

### 2023-12-06
## Thread
> **쓰레드**는 프로그램의 실행 흐름이며 **프로세스의 작업 단위**이고 **프로세스**는 하나의 프로그램을 의미한다
>  한 개의 프로세스에서 여러 개의 쓰레드를 가지는 방식을 병렬 처리 방식이라고 한다.
##### 모든 자바 어플리케이션은 메인 스레드가 main() 메소드를 실행시 시작된다. 메인 스레드는 main() 메소드의   
##### 첫 코드부터 아래로 순차적으로 실행하고 main() 메소드의 마지막 코드를 실행하거나 return문을 만나면 실행이 종료된다.
|싱글 쓰레드|멀티 쓰레드|
|--|--|
|<img src="https://github.com/chanho0908/interview-question/assets/84930748/e6c134c0-7fcc-4e2a-9382-da03efca386a">|<img src="https://github.com/chanho0908/interview-question/assets/84930748/dac0f0a9-642e-45d0-831c-cd8c209b286b">|
##### 싱글 스레드에서는 메인 스레드 종료시 프로세스도 종료되지만 멀티 스레드 환경에선 실행 중인 스레드가 하나라도 있다면 프로세스는 종료되지 않는다.

## 2. How to Create Tread 
##### 자바에서는 java.lang.Thread 클래스에서 작업 스레드 객체를 생성할 수 있고 Runnable을 매개값으로 갖는 생성자를 호출한다.   
```
Thread thread = new Thread(Runnable target);
```
* Runnable은 작업 스레드가 실행할 수 있는 코드를 가지고 있는 객체를 의미한다.
* Runnable은 인터페이스 타입으로 구현 객체를 만들어야 한다.
* Runnable에는 run() 메소드가 하나 정의되어 있는데, 구현 클래스는 run()을 오버라이딩 하여 작업 스레드가 실행할 코드를 작성해야한다.
```
class Task implements Runnable(){
  public void run(){
    //작업 코드
  }
}
```
* Runnable은 작업 내용을 가지고 있는 객체이다. Runnable 구현 객체를 생성 후 이를 Thread 생성자로 호출하면 생성된다
```
// 람다식
Thread thread = new Thread(() -> {
    public void run(){
    }
}
```

* 쓰레드를 실행시키기 위해선 start() 메소드를 호출해야 한다.
```
thread.start():
```
  
 
 # 3. 하나의 변수를 여러 쓰레드에서 사용할 경우 발생할 수 있는 일(면접 질문)
   1) 임계 영역 : 멀티 쓰레드 프로그램에서 단 하나의 쓰레드만 실행할 수 있는 영역
   2) Lock : 지정된 쓰레드만 공유 데이터에 접근할 수 있고 lock을 release 해야만 다른 쓰레드에서 접근할 수 있다.
   3) Mutex : 쓰레드가 동시에 공유된 자원에 접근하는 것을 막기 위해 사용. 뮤텍스는 특정 코드 영역에 대한 잠금(lock)과 해제(unlock)를 허용하여 여러 쓰레드 간의 안전한 접근을 가능하게 한다.
## 3. Android Runtime Permission
  #### 과거에는 앱 설치시 모든 권한을 부여했지만 Android 6.0(API 레벨 23) 이상에서는 앱이 이런 위험한 권한들을 필요로 할 경우     
  #### 앱 실행중에 권한을 요청할 수 있도록 시스템에 Runtime Permission 을 도입하였습니다.
![image](https://github.com/chanho0908/interview-question/assets/84930748/15251c02-6d48-4f63-b3ad-2b8f201191d3)

## 기타 질문
> WAR(WEB Application Archive) 파일: Java 웹 어플리케이션을 패키징하고 배포하기 위한 파일 형식 중 하나
> Tomcat에서 서버를 열 때 포트 번호 : 8080
> TCP란 ? 네트워크 통신에서 패킷 전송을 담당하는 프로토콜 중 하나

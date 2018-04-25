# Design Pattern

## Definition

**Design Pattern**이란 소프트웨어 공학에서 프로그램을 설계하는 기법이다. 프로그램의 각기 ```pattern```에 따라 효율성이 향상될 수가 있다.

## MVC Pattern

**MVC**는 ***Model***, ***Control***, ***View*** 의 약자이다. MVC에 대한 설명과 간단한 프로그램을 예시로 들겠다.

### Model

- ```User```가 사용하는 모든 데이터를 소유하고 있어야 한다.  
- ```View```와 ```Controller```의 변동에 의한 파장이 없어야 한다.

```java
Class Model{

	private String name;
	private int age;

	public void setName(String name){
		this.name = name;
    }

	public String getName(){
		return name;
	}

	public void setAge(String age){
		this.age = age;
	}

	public Int getAge(){
		return age;
	}
}
```

### View

- ```UserInterface```만 구성되고 로직은 없어야 한다.  
- ```Model```과 ```Controller```의 변동에 의한 파장이 없어야 한다.  

```java
package MVC_Pattern;

public class View {

	public static void main(String[] args) {
		System.out.println("1  + 1 = ");
	}
```

### Control

- ```View```와 ```Model```의 알고리즘 변경 시마다 변경되어야 한다.  
- ```Model```과 ```View```의 변동을 인지하고 이에 따른 로직을 Model에서 호출해야 한다.  

Control은 Model과 View의 중간에서 ---하는 역할을 한다.

```java
package MVC_Pattern;

Class Control{

	Model info;

	public void setPeopleName(String name){
		info = new setName(name);
	}

	public String getPeopleName(){
		return info.getName();
	}

	public void setPeopleAge(int age){
		info.setAge = age;
	}

	public int getPeopleAge(){
		return info.getAge;
	}

	public void updateAge(){
		return info.setAge++;
	}


	//

}


Class Contorl{
	
}
```
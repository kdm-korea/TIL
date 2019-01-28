# SRP

### 정의
SRP - Single Responsibility Principle

#### '단일책임의 원칙'이란 모든 클래스는 하나의 책임만 가지며 클래스는 그책임을 완전히 캡슐화해야 함을일컫는다. 클래스가 제공하는 모든 기능은 이 책임과 주의깊게 부합해야 한다. -Wiki

하나의 클래스는 하나의 책임을 갖고 코드를 적절히 분배함으로써 코드의 가독성이 향상된다. 무엇보다도 책임 영역이 확실해지기 때문에 유지보수 및 하자보수에 용이하다.
물론 효율적인 분배와 깔끔한 코드 확립을 위해서는 많은 노력이 필요하다.

예시

****
```C#
public Class Person{
    private Eat eat;
    
    pubic setEat(Eat eat){
        this.eat = eat;
    }
    
    public play(){
        Console.writeLine(eat.toString());
    }
}
```

```C#
public Class Bread extend Eat{
    public String toString() {
        return "Bread";
    }
}
```

```C#
public Class Rice extend Eat{
    public String toString() {
        return "rice";
    }
}
```

```C#
public Class Eating{
    public void Main(){
        Person person = new Person();
        Eat eat = new Bread();
        
        person.getEat(eat);
    }
}
```

---

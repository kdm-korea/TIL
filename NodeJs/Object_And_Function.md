# Object, Function, Variable

## Definition

**NodeJs**에서 데이터를 담아 사용하는 방법에는 크게 두가지 방법이 있습니다. 노드의 문법은 js를 따라가기 때문에 아래의 글에서 설명하는 ```Object```와 ```Function```는 ***JavaScript*** 의 문법과 동일합니다. ```Object```와 ```Function```을 설명하기 전에 ***Variable*** 부터 설명하도록 하겠습니다.

## Variable

```JavaScript```에서 변수는 ***C language*** 나 ***Java*** 와 차이가 있습니다. 각 형태의 자료형(*정수, 실수, 문자, 문자열 등*)이 각 형태에 따라 변수의 선언부가 달라지지 않습니다. 선언은 **var**로 선언을 하게 됩니다.  

```javascript
var num = 15;
var name = '김동민';
var avg = 85.12;
var grades = 'A';
```

변수명의 첫글자는 소문자로 입력하는 것을 기본으로 하며 변수명이 두개의 단어 이상으로 이루어진 경우 두번째 단어부터 앞글자를 대문자로 사용합니다.  

```javascript
var totalAvg = 85.12;
```

***NodeJs*** 에서는 **Variable**에 **Function**을 할당하여 사용할 수 있습니다.
```javascript
var calAdd = function calculatorAdd(numFst, numsSec){
    return numFst + numsSec;
}
```

## Function

**Function**는 어떠한 기능을 수행하기 위해 만들어진 것을 뜻합니다. 함수는 기능별로 단위를 나누며 정규화가 잘 이루어진 함수는 가독성이 좋습니다.  
함수를 만드는 방법에는 두가지 방법이 있습니다.

- 변수에 함수를 처음부터 할당하여 만드는 경우
    ```javascript
    var add = function(numFst, numsSec){
        return numFst + numsSec;
    };
    ```

- 함수 이름을 생성하고 만드는 경우
    ```javascript
    function add(numFst, numsSec){
        return numFst + numsSec;
    }
    ```

## Object

**Object** 는 위에서 만든 ***Function*** 와 ***Variable*** 를 하나의 큰 틀에 넣어 사용하는 개념이라고 생각하면 좋습니다. 관련있는 정보를 하나의 큰 틀로 묶어 사용한다면 효율적인 코딩이 될 수 있습니다.  
예시로 학생에 대한 정보를 들겠습니다.

```javascript
var Student = [];
    Student['name'] = 'kim';
    Student['age'] = 24;
    Student['garde'] = 2;
    Student.info = function(name, age, job){
        console.log('name: ' + name + ' age: ' + age + ' grade:' + grade);
};
```
위와 같이 학생이라는 ```객체```에는 ```이름```, ```나이```, ```직업``` 마지막으로 정보를 출력해주는 ```info```라는 함수가 포함되어 있습니다. 함수를 할당할 수도 있으며 위처럼 사용할 수도 있습니다.
# Module

## Definition

하나의 함수 안에 모든 기능을 넣는 것보다 여러개의 함수로 분리 한 후 사용하는 것이 효율적이다.  
 각각의 기능을 분리시킬 때는 단순히 별도의 파일에 코드를 나우어 놓는다고 끝나는 것이 아니라 분리되어 있는 모듈 파일을 불러와서 사용할 수 있는 방법도 함께 만들어 줘야 한다.  
 또한 **기능별**로 분리한 함수들은 비슷한 기능 수행을 기준으로 구분하여 관리하는 것이 사용하기도 쉽다.  
 *Module*이란 별도의 파일로 분리된 독립 기능의 모음이라 볼 수 있다.

## 모듈의 종류

- ### 내장모듈  
    하나의 모듈 내부에 함수를 넣어 별도 파일로 분리하지 않으며 하나의 파일에 추가하여 사용한다.

- ### 외장모듈  
    여러개의 모듈로 분할하여 사용한다. 각 모듈을 구성하는 것은 비슷한 기능을 수행하는 함수로 이루어져 있으며 사용하는 방법에는 두가지가 있다.

## 외장모듈 사용법

분리되어 있는 모듈을 불러와 사용할 수 있는 방법에는 두가지가 있다.  
*Node*는 **CommonJs**의 표준 스펙을 따라 모듈을 사용할 수 있으며 ***exports*** 와 ***module.exports*** 을 사용할 수 있다.

- ### exports
        //Main Module
        var module = require('callmodule');
        callmodule.function_name;
- 
        //callmodule
        exports.function_name = function_definition;

- ### module.exports
        //Main Module
        exports.function_name;
-
        //callmodule
        var function_name = {};

        function_name.addition(num1st, num2nd){
            return num1st + num2nd;
        }
        
        module.exports = function_name;
# Javascript Coding Guidelines

## Naming

* variable should be in camelCase
* Class Name must be in PascalCase.
* Class **public or protect member** should be in camelCase.
* Class **private member** should be in camelCase having '_' in the end.
* A file name should be in snake case.
* global constant variables like configuration etc should be in CAPITAL_SNAKE_CASE 

```
class Person {
    name:string;

    constructor(name){
        this.name = name;
    }

    getMessage_(){
        return `your name is ${this.name}`;
    }

    sayMyName(){
        const message = this.getMessage_();
        alert(message); 
    }
}

const person1 = new Person("ujjwal gupta");
person1.sayMyName();
```

## File

files should be named in snake_case

```
person.ts
deposit_exporer.ts
withdraw_explorer.ts
```


## Static Member 

A class member which does not use instance member, then it should be made `static`.

```
class Util{
    static multiply(num1:number, num2:number){
        return num*num2
    }
}
```

### Static Member in another class

A static function or variable should not be used directly inside a class but it should be wrap in a private function.

```
class Main{
    private multiply_(num1:number, num2:number){
        return Util.multiply(num1,num2);
    }
}

```

## TypeScript guidelines

* Every variable should be staticly typed . If it may accept multiple type then use multiple type or **any** - Though **any** is not recommended until and unless there is hard requirement.

## Modules

Try to create a modules for every functionality, even if it is small. And import that module everywhere instead of a particular file.

e.g - Consider we have to create util methods

1. isEmpty
2. isObject

we created two files is_empty.js & is_object inside utils folder.

now users can use it this way - 

```
import {isEmpty} from "./utils/is_empty";
```

or we can create a module of all the methods inside utils and user will have to import only utils folder.

create a folder index.js inside utils folder and export all methods like this

```
export * from "./is_empty";
export * from "./is_object";
```
and then users will use like this - 

```
import {isObject} from "./utils";
```

## CodeThink Approach

* A variable, class, method name should clearly explain its behaviour.
* Always intialize and assign member variable in constructor method.
* Remove something if its not being used. Do not comment and keep it for the future reference.
* Always use arrowType function.
* Always use es6 advanced inbult functions like - findIndex, find etc. If you are using something old js style that is no problem but if you found later on that this can be replaced with es6 then please replace it.

# FrontEnd

frontend guidelines

### Frameworks 

* [Vue](vue.md)

## Naming

* variable should be in camelCase
* global constant variables like configuration etc should be in CAPITAL_SNAKE_CASE 
* Class name must be in PascalCase
* Class member must be in camelCase

```
class Person {
    name:string;

    constructor(name){
        this.name = name;
    }

    sayMyName(){
        const message = `your name is ${this.name}`; 
    }
}
```

### Component

* A component should be loose coupled or no coupled. So that it can work independently.
* All dependencies should be passed using props except some states which are global like logged in user id, is authenticated etc.
* Always use store - you will end up using tomorrow, so it's better to start with store. 

#### Component naming

Use PascalCase for component naming inside html code. This helps us to identify custom made component when debugging.

```
<template>
    <MyComp/>
</template>
<script>
import MyComp from "@/component/my_comp";
export default{
    children: {
        MyComp
    }
}
</script>
```

## HTML

html codes should not exceed more than 50 lines. If exceeding, please try to break your code & create components.

## Script

script codes should not be more than 100 lines. It is natural for script codes to be large , in that case refactor your code by using inheritance, mixins.

## Style

* Use [BEM](http://getbem.com/introduction/) syntax 
* Use scoped css if possible. Vue provides scopped css.
* Use mobile first approach
* Use max-width for big screen - so that you are focusing on particular width. Now a days we have large resolution devices, where adjusting content is kinda of time consuming. So its better to make your content in center and leave the space for rest of screen. This is how most of company like fb, twitter etc. does.

## Layers

layers helps us to refactor our app into different layers.

There are three layers of any front end app - 

1. Component (UI)
2. Store (state store)
3. Service (API calls)

### 1. Component

Component contains ui code and it needs state in order to renders the value in UI. So component is generally coupled with store layer.

### 2.Store

Store contains states and it uses service layer to get the data and then store into states.

* Store layer is coupled with components.
* All Service call should be implemented in store actions.

### 3. Service

Service layer is responsible for calling API. It is independent layer and most of the function is pure i.e it receives arguments, call apis and return the result.

### Component <-> Store

Component should communicate to Store and viceversa.

### Store -> Service

Store should communicate to service layer and store the results in states. All Service call should be implemented in store actions.

All service call should be made from actions, nothing from Component. So component know only stores, it doesn't need to know the service layer.


## Error Handling

Proper error handling is very important for any app. It helps us to show good user friendly error message to users and also help us debug the error.

* create a enum `ERROR_TYPE`
* create a error helper class which will create the error based on type.
* create a UI for showing error.
* Service layer interacts with outer entity which is api and there is big probability of error from api calls like 500, api is down etc. So every service call should be wrapped in try catch and user should be shown proper error. 

A generic message should be shown in case we have no idea about error like - "Sorry for inconvenience, please try later" etc. Please consult UX team for message.

* use sentry or similar tools for error tracking. Configure sentry with message platform like sentry, teams etc. 



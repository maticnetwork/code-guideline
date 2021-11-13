# Vue

## Stores (Vuex)

### naming

* state should be in camelCase
* mutations should be in CAPITAL_SNAKE_CASE
* action should be in camelCase
* getter should be in camelCase

```
const store = {
    state:{
        firstName:'ujjwal',
        lastName:'gupta'
    },
    mutations:{
        SET_FIRST_NAME(state,value){
             state.firstName = value;
        },
        SET_LAST_NAME(state,value){
             state.lastName = value;
        }
    },
    actions:{
        fetchUser(){

        }
    },
    getters:{
        fullName(state){
            return state.firstName + state.lastName;
        }
    }
}
```

### Guideline

* use namespaced store
* create a seperate store by feature wise or category wise (seperation depends upon the product, so anything is permitted) and make it namespaced. 
* create a seperate folder for each store and keep state, action, getter , mutation inside seperat file. Import all the codes into a index.js file treating store as a module.
* state should be created by calling a method,  which will return the initial state. So that we are not getting into issue of object reference.
* A getter should be only created if it computes something out of state. Only returning state from getters is not allowed.
* Action should call service, store the result in state & return the response if required.
* Follow naming conventions defined in naming sections.
* Every store should implement action "reset" which will be used to reset the store.
* Every store should implement mutation "RESET" which will be used to reset the state & will be called by action "reset".


## Filters

* Use filters for formatting code. Define filters globally if formatting is something generic, otherwise keep it in local component.

* Use filters when you have nested object and showing it in html.

* Filters can be chained, so design your logic in a way so that you can use multiple filters.

## Computed

In a case when you have to compute any expression and show the value in html or use if else or for , then use computed. 

## data

Define variable inside data which needs reactivity otherwise initiate it in constructor or created hook.

## Style

No limit to style codes but try to refactor it and keep it in a seperate file, then import inside component.

## Accessing store

Always use map methods from store like mapGetters, mapState etc.

## Event naming

always use train-case for event naming & name should be something like a event.e.e.g - click, loaded, item-loaded etc

```
<MyComponent @deleted="" @newuser-created=""> </MyComponent>
```




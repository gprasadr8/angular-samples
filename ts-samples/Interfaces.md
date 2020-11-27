**Interfaces in Typescript:**

- Interface is the way of defining the contract
- In Typescript interfaces are used for implementing structural subtyping of objects
- interfaces can extend other interfaces
- It can be used to set properties as **optional** or **read only**
- can be used to enforce contracts for classes
- It doesn't have a runtime representation

```typescript
interface Human {
    readonly age: number;
    walk():void;
}

interface Person extends Human {
    firstName: string ;
    lastName?:string;
}

// For Objects

const user:Person = {
    firstName:"V",
    lastName:"RK",
    age: 23,
    walk: () => {return;}
}

console.log("user: ",user);
//we can't re assign value for age property because it's a readonly property
//user.age = 120;

//for Classes
class Employee implements Person{
    firstName = 'PR';
    age = 50;
    walk():void{
        return;
    }
   
}
```


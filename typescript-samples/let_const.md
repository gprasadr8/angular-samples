**let:** In typescript we use **let** keyword to declare the variables. we can declare first and define the value next.

**Examples:**

```typescript
let mynumber = 10;
let a; a = 20;
let name = "prasad"
let isUserEnabled = true

```

**const:** it is used to define the immutable constants where we can't reassign the variable.

- if it is a primitive data type the value can't be changed

- Internal state of the const can be modified for complex data type like arrays, objects,.. etc.

**Examples:**

```typescript
const num1 = 10; 
//we have to assign a value while declaration otherwise it gives an 
const num2;
//error: 'const' declarations must be initialized
const name = "Prasad"
name = "rahul"// error:Cannot assign to 'name' because it is a constant.

```

- we can change the internal state of the complex type

  ```typescript
  const user = {
      "first_name": "prasad"
  }
  //user = { "first_name":"vivek"} we cannot reassign
  
  user['last_name'] = "rama krishna" //we can modify by adding new property
  ```

  
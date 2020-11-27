**Primitive types:**

1. boolean
2. number
3. string 
4. null
5. undefined

**How to declare a variable with type in typescript?**

we have to use let keyword and variable name then colon(:) and type of the variable we want to assign. For example:

​		**let variable_name : type_of_vairable**



1. **boolean:** for a boolean type variable we can assign **true** or **false** or **null** or **undefined** or **a self calling function which returns a boolean type supported value.**

   **For Example:**

   ```typescript
   //boolean:
   let authorized: boolean;
   authorized = true;
   authorized = false;
   authorized = null;
   authorized = undefined
   authorized = (()=> true)();
   authorized = (()=> false)();
   authorized = (()=>null)();
   authorized = (()=>undefined)();
   //we cannot assign other than the above values
   authorized = 10 //Error: Type 'number' is not assignable to type 'boolean'
   authorized ="yes"//Error: Type 'string' is not assignable to type 'boolean'
   
   ```

2. **number:** for a number type variable we can assign **decimal** or **binary** or **octal** or **hexa decimal numbers** or **null** or **undefined** or **a self calling function which returns a number type supported  value.**

   ```typescript
   //2. number:
   let mynum: number;
   mynum = 10;
   mynum = -10;
   mynum = 10.123;
   mynum = 0b10101;
   mynum = 0o1725;
   mynum = 0x19ac;
   mynum = (()=>1023)();//any function which returns number
   mynum = null;
   mynum = undefined;
   mynum = (()=>null)();
   mynum = (()=>undefined)();
   //we cannot assign other than the above values
   mynum= true;//Error: Type 'boolean' is not assignable to type 'number'
   mynum= "Five hundred";//Error: Type 'string' is not assignable to type 'number'
   
   ```

3. **string:** for a string type variable we can assign value with **double quotes("")** or **single quotes('')** or **back ticks(``)** or **null** or **undefined** or **a self calling function which returns a string type supported value.**

```typescript
//3. string:
let first_name:string;
first_name = "vivek";
first_name = 'vivek';
first_name = `vivek`;
first_name = `vivek`.toUpperCase();//any function which returns string
first_name = null;
first_name = undefined;
first_name = (()=>null)();
first_name = (()=>undefined)();
//first_name = 10;//Error: Type 'number' is not assignable to type 'string'
//first_name = true;//Error: Type 'boolean' is not assignable to type 'string'

```

4. **null:** for a null type variable we can have **null** or **undefined** or **a self calling function which returns a null type supported value.**

```typescript
//4.null
let data:null;
data = null;
data = undefined;
data = (()=>null)();
data = (()=>undefined)();
data = 10; //Error: Type '10' is not assignable to type 'null'
data = true;//Error: Type 'true' is not assignable to type 'null'

```

5. **undefined:** for a undefined type variable we can have either **null** or **undefined** or **a self calling function which returns a undefined type supported value.**

```typescript
//5. undefined
let userData:undefined;
userData = undefined;
userData = null;
userData = (()=>null)();
userData = (()=>undefined)();
userData = 10;//Error: Type '10' is not assignable to type 'undefined'
userData = false;//Error: Type 'false' is not assignable to type 'undefined'

```



**Note:**

- base types: **null & undefined** can be assigned to any primitive types like boolean, number and string. 

**Reference types:**

1. void
2. Array<type>
3. tuple
4. objects
5. enum
6. any

1. **void:** void type is generally assigned to a function that returns nothing.

   ```typescript
   function logToConsole(): void{
    console.log("This is a logToConsole functions");
    return;
   }
   
   function logToConsole(): void{
    console.log("This is a logToConsole functions");
    return;
    return 1;//Error: Type 'number' is not assignable to type 'void'
    return "hello";//Error: Type 'string' is not assignable to type 'void'
   }
   ```

   

2. **arrays:** we can create arrays based on the types.

   ```typescript
   //arrays:
   
   let names: string[];// we can add all the values allowed by string type
   names = ['vivek','ram','krishna','tuLaSi'.toLowerCase(),null,undefined];
   
   let cities: Array<String>;
   cities = [`Bangalore`,'Hyderabad',"Chennai",undefined,null,(()=>"Delhi")()];
   
   let generic_ary : Array<string | number | boolean>;
   generic_ary = ["Hello",10,true,null,undefined]
   ```

   

3. **tuple:** the syntax of the tuple is similar to arrays but the type declaration will vary. While declaring tuple will fix the size and type of it's values. generally we don't use much in angular

   ```typescript
   let coordinates: [number,number,number];
   coordinates = [10,20,null];//it will take only 3 values and 
   //values should be number type supported values
   
   let generic_tuple: [string,number,boolean];
   generic_tuple = ["Hello",25,false];//it will take only 3 values and 
   //the first value should be string type supported value and 
   //second should be number type supported value and
   //third value should be boolean type supported value
   
   ```

   

4. **objects:** An **object** is an instance which contains set of key value pairs. The values can be scalar values or functions or even array of other objects. The syntax is given below

   ```typescript
   syntax:
   let object_name = { 
      key1: “value1”, //scalar value 
      key2: “value”,  
      key3: function() {
         //functions 
      }, 
      key4:[“content1”, “content2”] //collection  
   };
   
   Example:
   //objects:
   let todoUser = {
       first_name: "vivek",
       last_name: "rama krishna",
       username: "vivekrk",
       getUsername: function(){
           return this.username;
       }
   };
   console.log(`firstname: ${todoUser.first_name}`);
   console.log(`username: ${todoUser.getUsername()}`);
   
   ```

   

5. **enum:** Enums allow a developer to define a set of named constants. Using enums can make it easier to document intent, or create a set of distinct cases. TypeScript provides both numeric and string-based enums.

   ```typescript
   //enum
   enum Days {
   MONDAY="mon",
   TUESDAY="tue",
   WEDNESDAY="wed"
   };
   
   let today: Days;
   today = Days.MONDAY;
   console.log(`today: ${today}`)
   //by default it assigns to numbers from 0
   enum Directions{
       UP,
       DOWN,
       LEFT,
       RIGHT
   }
   console.log(`UP value:${Directions.UP} `)
   ```

   

6. **any:** If we don't want to specify the variable as yet then we can use **any** as type. if we have javascript and slowly migrate to typescript then this type will be useful or we can use when we are not concerned about the type. one of the problem with this is we won't get any intellisence from IDEs.

   ```typescript
   //If we don't specify any type then by default it's any type
   
   // any:
   let msg;
   msg = "hello";
   msg = {
       body:"updated"
   }
   msg = false;
   
   let author:any;
   author = "prs";
   author = null;
   author = undefined;
   author = {
       id:123,
       name:"gprs"
   }
   ```

   


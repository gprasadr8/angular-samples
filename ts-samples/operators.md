**Operators:**

1. spread(**...**) operator
2. Backticks(**``**) operator
3. Destructure(**{}**)
4. Rest Params (**...args**)



1. Spread(...) Operator:  

   - It uses to spread the elements of an array or Object
- merging multiple arrays/objects into one flat array/object
   - Denoted by triple dots(...)
   
   **Examples:**
   
   ```typescript
   //spread(...) examples:
   console.log("spread(...) examples:")
   //Array
   let fruits: Array<string> = ['Apple','Mango','Grapes'];
   let food: string[] = ['Pizza','Burger','chocos'];
   let edibles: string[] = [...fruits,...food];
   
   console.log("edibles:",edibles);
   
   //Object
   let user = {
       "firstName":"Vivek",
       "secondName":"RK"
   }
   
   let userDetails = {
       ...user,
       "username":"vrk",
       "email":"vrk@gmail.com"
   }
   
   console.log("User Details: ",userDetails);
   
   //Functions
   //here ? is for Optional params
   //we have to make function params optional to get rid of  compilation error during spread usage
   function add(x?:number,y?:number,z?:number){
       return x+y+z;
   }
   
   let numbers: number[] = [10,20,30]
   console.log("sum",add(numbers[0],numbers[1],numbers[2]));
   console.log("sum",add(...numbers));
   ```
   
2. **Backticks(``):** Backticks was introduced as part of ES6

   - It is used to wrap around strings
   - Used with ${variable} to append the value of the variable to the string
   - Stringifies Arrays and Objects
   
   For example if we want to log some details to console then generally will do concatenating multiple strings using **'+'** operator
   
   ```typescript
   let user = {
       "firstName":"Vivek",
       "secondName":"RK"
   }
   //without backticks we should be careful to maintain spaces and + operator
   console.log("First Name:"+user.firstName+" and Second Name: "+user.secondName);
   
   //with backticks we don't need to add concatenation operator  to display values
   console.log("With Backticks:");
   console.log(`First Name:${user.firstName} and Second Name: ${user.secondName}`);
   ```
   
   - Problem with backticks is it always stringfy the arrays and objects
   
   ```typescript
   let fruits: Array<string> = ['Apple','Mango','Grapes'];
   let user = {
       "firstName":"Vivek",
       "secondName":"RK"
   }
   console.log(`with backticks`);
   console.log(`fruits: ${fruits}`);
   console.log(`user: ${user}`)
   console.log(`without backticks`);
   console.log(`fruits:`, fruits);
   console.log(`user:`, user)
   ```



3. **Destructure Operator({}):**

   - Breaks up the structure of an array or object
   - Plucking elements of an array or Object
   - Variable wrapped in **{} for object** and **[] for arrays**
   - Generally used in import statements

   ```typescript
   // Destructure {}
   
   let {firstName, lastName} = userDetails;
   console.log(`First Name:${firstName} and Last Name: ${lastName}`);
   //destructre with alias
   let {firstName: fname, lastName:lname} = user;
   console.log(`fname:${firstName} and lname: ${lastName}`);
   // object destructuring will be done based on the property name 
   let {username, email} = userDetails;
   console.log(`username: ${username} and email: ${email}`)
   
   // below gives an error because there is no property with name a and b
   //let {a, b} = userDetails;
   
   // For array elements will be destructured based on index
   let [x, y] = fruits;
   console.log(`x: ${x}`);
   console.log(`y: ${y}`);
   ```

   

4. **Rest params (...args):**

   - Allows us to represent indefinite number of arguments as an array
   - It can be used only as a function's last parameter
   - The last parameter can be prefixed with triple dot **...**
   - Remaining arguments to the function are placed within a "standard" javascript array

   ```typescript
   // rest params (...args)
   //Arrays
   console.log(`Before rest params edibles: ${edibles}`);
   // first value will be assigned to p which is Apple
   // rest of the array values are assigned to variable to q
   let [p, ...q] = edibles;
   console.log(`p:${p}`);
   console.log(`q:${q}`);
   
   // Objects 
   
   console.log(`Before rest params User Details:`, userDetails);
   let {email:mailId, ...restUser} = userDetails;
   // email:mailId email is property name and mailId is alias name for property
   // destructures the object by setting email property value to mailId alias variable and 
   // rest of the object properties will be created an object and assign it to restUser variable
   console.log(`mail Id: ${mailId}`);
   console.log('restUserDetails',restUser);
   
   // Functions:
   console.log(`Before function rest params Edible:`, edibles);
   function getEdibles(firstEdible?, ...restEdibles){
       console.log(`getEdibles function with rest params:`);
       console.log(`firstEdible: ${firstEdible}`);
       console.log(`restEdibles: ${restEdibles}`);
   }
   
   // spreading the edibles to functional args
   // first index value will be assigned to firstEdible
   // rest of the array elements will be assigned to restEdibles
   getEdibles(...edibles);
   ```

   
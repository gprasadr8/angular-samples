**How to create fake data:**

In this Notes we are going to use faker.js file to generate fake data. faker.js doc: https://github.com/marak/Faker.js/

faker.js - generates massive amounts of fake data in the **browser** and **node.js**



### Steps to create fake data:

1. Open **command prompt** and go to the folder where you want to create fake data
2. run : **$ npm init** to create a project
3. run: **$ npm install faker** to add faker.js dependency to the project
4. create a **one-record-generator.js** file add the below code.

 **one-record-generator.js**

```js
var faker = require('faker');

var randomName = faker.name.findName(); 
var randomEmail = faker.internet.email(); 
var randomJobTitle = faker.name.jobTitle();
console.log("Name: "+randomName +" Email: "+ randomEmail +" Job: "+ randomJobTitle);
```

5. run the file using cmd: **$ node one-record-generator**  or add this cmd to **scripts** property inside the **package.json** file and then run using **npm** cmd: **$ npm run generate**

   ```json
   "scripts": {
       "generate":"node one-record-generator.js",
       "test": "echo \"Error: no test specified\" && exit 1"
     }
   ```

6.  to write console output to file then update **generate script** in `package.json` like below:

   ```json
   "scripts": {
       "generate":"node one-record-generator.js > one-record.json",
       "test": "echo \"Error: no test specified\" && exit 1"
     }
   ```

   

7. now run: **$npm run generate**. it creates a `one-record.json` file with log data. 

   **For Example:** one-record.json

   ```json
   Name: Cathy Schmeler Email: Pauline6@yahoo.com Job: Senior Functionality Analyst
   ```



### How to create thousands of records by using faker?

1. create `thousand-records-generator.js` file

   ```js
   var faker = require('faker');
   
   var users = [];
   
   for(i=1;i<=1000;i++){
       users.push({
           id: i,
           name: faker.name.findName(),
           jobTitle: faker.name.jobTitle(),
           email:faker.internet.email(),
           salary:"$"+faker.commerce.price()
       });
   }
   
   console.log(JSON.stringify(users));
   ```

   

2. add **generate script** in `package.json`

   ```json
    "scripts": {
       "generate":"node thousand-records-generator > thousand-records.json",
       "test": "echo \"Error: no test specified\" && exit 1"
     }
   ```

   

3. Then run command: **$npm run generate**

4. After completion of this command node will generates the `thousand-records.json` file with thousand objects.

5. 

   


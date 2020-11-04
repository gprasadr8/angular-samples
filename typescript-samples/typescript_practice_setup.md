

**How to do setup to practice typescript in localhost?**

1. create a folder where you want typescript samples to place

2. go to cmd prompt and execute **npm init** command then it will ask few questions to created npm project and enter appropriate details

3. you can see **package.json** file will be created with the details of what you've entered during the npm init

4. now lets create a typescript file **index.ts** and write some code like

   ```typescript
   console.log("Hello World..!");
   ```

5. **Note:** browsers can understand only java script, so we have to convert this typescript to java script. To do that we have to run a cmd **tsc filename** in our example it will be **tsc index.ts**

6. once we execute this one we can see there is a index.js file created on the same folder.

7. To check whether the generated java script works or not,  we have to run it on web browser for that we have to create a html file and need to add this java script file in the script tag.

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Index page</title>
   </head>
   <body>
       
   </body>
   <script src="index.js"></script>
   </html>
   ```

8. after creating the html file open it on browser

9. once you open you don't see anything on the screen because we haven't written anything on the html body. To check with java script either do **Right Click and open Inspect element** or click on **F12** or **Ctrl+Shift+I** after that click on **console** tab there you can see our **Hello World..!** message on the log.



**For Online typescript env setup:**

- we can use https://stackblitz.com/edit/typescript



**Additional Notes:**

- If we run with -w cmd option in tsc then it will watch for the changes on ts file without terminating the tsc cmd  **tsc index.ts -w**

- we can setup the tsc command to run by using **npm start**. For that we have to add tsc cmd inside the scripts object of package.json file. for example

  ```json
  "scripts": {
      "start": "tsc index.ts -w",
     }
  ```

- When we run **npm start** it will execute cmd inside the **start** property

 
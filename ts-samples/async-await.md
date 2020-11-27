**async/await:**

- **async/await** is a sort of syntactic sugar used with **Promises**

- a function that returns a **Promise** can be called with a **await** keyword

- a function in which the function returning the Promise is awaited must be declared with the **async** keyword otherwise will get an error " **'await'** expressions are only allowed within **async** functions and at the top levels of modules."

  ```typescript
  //Example:
  function getUserViaFetch() {
      return fetch("https://jsonplaceholder.typicode.com/users/1")
      .then(response => response.json());
      
  }
  
  async function init(){
      const user  = await getUserViaFetch();
      console.log("Got the user as: ",user);
  }
  
  init();
  ```

  
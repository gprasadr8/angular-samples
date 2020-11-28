**Application bootstrap mechanism in Angular:**

- An Angular application just doesn't run on the browser, it also runs on various other environments like in the Server when it comes to server side rendering and also on web workers. So there are many ways to bootstrap the angular application depending on the how we want to compile it and where exactly we want to run it
- There are basically two ways of compiling the application the Ahead of Time(AOT) compilation as well as JIT compilation. By default in the **serve** mode and in the **build** mode we use the JIT compilation but we can provide the flag --aot for Ahead of Time compilation
- For now consider we want to compile our application dynamically by using JIT compiler and run it on the browser.
- An angular application has a configuration file `angular.json`. This file will be used to determine the entry point of an angular application as well as an entry point for the templates which would be the index.
- Overall an Angular application needs:
  - A browser platform for our dynamic JIT compilation
  - An execution environment for our App to run on.
  - the above functionality is mentioned on `main.ts` file.



```typescript
// if we see there is a main property in the angular.json file which is used to mention the entry-point file for the angular application which is main.ts file
// index property is used to mention entry for the templates which is index.html file

{
    "architect": {
            "build": {
              "builder": "@angular-devkit/build-angular:browser",
              "options": {
                "outputPath": "dist/my-test-app",
                "index": "src/index.html",
                "main": "src/main.ts",
                "polyfills": "src/polyfills.ts",
                "tsConfig": "tsconfig.app.json",
                "aot": true,
              }
           }
}
```

- if we see there is a **main** property in the angular.json file which is used to mention the entry-point file for the angular application which is **main.ts** file

- **index** property is used to mention entry  point for application index file which is **index.html** file

  ```html
  <!doctype html>
  <html lang="en">
  <head>
    <meta charset="utf-8">
    <title>MyTestApp</title>
    <base href="/">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="icon" type="image/x-icon" href="favicon.ico">
  </head>
  <body>
    <app-root></app-root>
  </body>
  </html>
  
  ```

  

- initially Angular doesn't have any idea about what is the <app-root></app-root> tag.

- Then it starts executing `main.ts` file



```typescript
import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';
import { environment } from './environments/environment';

if (environment.production) {
  enableProdMode();
}

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));

```

- `platformBrowserDynamic()` this method is responsible for creating the browser platform that have the dynamic JIT compilation to work with and an execution environment to run the application

- `bootstrapModule(AppModule)` here we are mentioning the root module for bootstrapping  the application by convention root module will be AppModule

  ```typescript
  import { BrowserModule } from '@angular/platform-browser';
  import { NgModule } from '@angular/core';
  
  import { AppRoutingModule } from './app-routing.module';
  import { AppComponent } from './app.component';
  
  
  @NgModule({
    declarations: [
      AppComponent
    ],
    imports: [
      BrowserModule,
      AppRoutingModule    
    ],
    providers: [],
    bootstrap: [AppComponent]
  })
  export class AppModule { }
  ```



- while instantiating the AppModule will have a bootstrap array which should be bootstrapped during the module bootstrapping.

- bootstrap array has AppComponent, So angular starts executing the AppComponent class

  ```typescript
  import { Component } from '@angular/core';
  
  @Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.scss']
  })
  export class AppComponent {
    title = 'my-test-app';
  }
  ```

  

- while executing the AppComponent it identifies the `app-root` CSS selector and a `templateUrl` which points to the template of the app.component.html

- Now angular has an idea of what is the `<app-root></app-root>` tag all about in `index.html` . 

- Now it's basically injects the template of the `<app-root></app-root>` inside of the opening(<app-root>) and closing(</app-root>) tag

  ```html
  <!doctype html>
  <html lang="en">
  <head>
    <meta charset="utf-8">
    <title>MyTestApp</title>
    <base href="/">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="icon" type="image/x-icon" href="favicon.ico">
  </head>
  <body>
    <app-root>
     	<!-- here Angular will injects the AppComponent template --> 
     </app-root>
  </body>
  </html>
  ```

  

- When we run the application we will see the template wrapped with <app-root> tag

- 

- 

  


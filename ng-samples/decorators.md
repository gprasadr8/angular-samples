**Decorators:**

- What are the decorators?
- Different decorators in Angualr
- Angular Modules and the @NgModule decorator
- @NgModule decorator metadata
  - declarations
  - imports
  - exports
  - providers
  - bootstrap
  - entryComponents
- 



1. **What are decorators?**

   - ​	Angular is completely filled with decorators.

   - decorators will be mentioned on Classes and  Properties. So will have Class and Property decorators.

   - decorators are stage 2 proposal for JavaScript

   - experimental feature of TypeScript

   - we can think of decorators as a functions or higher order functions if they accept arguments

   - it will be prefixed with @ symbol

   - In Angular, almost everything is essentially a class . But these decorators transform them into a module, component, service, pipe or directive.

   - Following few commonly used decorators in Angular

     ​		**@NgModule 		@Component			@Directive			@Pipe**

     ​		**@Injectable			@Inject						@Input					@Output**

     ​		**@ViewChild			@ViewChildren		  @ContentChild	   @ContentChildren**

     ​		**@HostListener	   @HostBinding**	

2. **Angular Module:**

   - ​	in case of Angular module is  considered as cohesive block of code dedicated to an application domain, a workflow or a closely related set of capabilities

   - Angular apps are modular 

   - Angular has its own modularity system called NgModules

   - An Angular app must have at least on one module that is NgModule class, that is root module

   - conventionally the root module is named as AppModule

   - Modules are great way to organize an application and extend it with capabilities from external libraries

   - Many Angular libraries are modules themselves such as **FormsModule, HttpClientModule and RouterModule**

   - Many third party libraries are available as NgModules such as **AngularMaterial, Ionic and AngularFire**

     2.1 **How to create an Angular Module?**

     ```reStructuredText
     Recommended to use Angular CLI
     cmd: ng g m module-name
     1. it creates a folder with module-name
     2. creates a file module-name.module.ts under folder module-name like below
     	/app/module-name/module-name.module.ts	
     3. Based on the Angular CLI will get the description on the CLI
     	
     
     ```

     ```typescript
     //ng g m core
     //it's created a file /app/core/core.module.ts
     import { NgModule } from '@angular/core';
     import { CommonModule } from '@angular/common';
     
     
     @NgModule({
       declarations: [],
       imports: [
         CommonModule
       ]
     })
     export class CoreModule { }
     
     //Module is a plain TypeScript class with @NgModule decorator
     
     ```

3. **@NgModule:**

   - Angular Module is plain Typescript class which has @NgModule decorator
   - @NgModule decorator will have metadata object with properties: declarations, imports, exports, providers, entryComponents, bootstrap
   - Those are the properties which are  used to configure an Angular Module

   ```typescript
   //AppModule
   import { BrowserModule } from '@angular/platform-browser';
   import { NgModule } from '@angular/core';
   
   import { AppRoutingModule } from './app-routing.module';
   import { AppComponent } from './app.component';
   
   @NgModule({
     declarations: [
       AppComponent
     ],
     exports:[], 
     imports: [
       BrowserModule,
       AppRoutingModule
     ],
     providers: [],
     bootstrap: [AppComponent]
   })
   export class AppModule { }
   ```

   1. **Declarations Array:**

      - declarations are a list of components, directives, and pipes that belong to this module.
      - declarations array is used to register an Angular **Component, Pipe or Directive** on an Angular Module
      - Component, Pipe and Directives are also called as **declarables**
      - declarations is an array which contains components, pipes and directives
      - declarations accepts a set of declarables to be registered on the Angular Module
      - It doesn't accept:
        - @NgModule
        - @Injectable
        - A non-angular classes i.e plain typescript classes are not accpeted
        - Declarable registered on any other Angular Module
      - We cannot use any declarable without registering/adding it to declarations array. 

   2. **Imports Array:**

      - imports array is an way of extending the capabilities exported by some other Angular Module into our own Angular Module

      - imports are a list of modules to import into this module. Everything from the imported modules is available to `declarations` of this module.

        ```typescript
        // app.module.ts
        import { BrowserModule } from '@angular/platform-browser';
        import { NgModule } from '@angular/core';
        
        import { AppRoutingModule } from './app-routing.module';
        import { AppComponent } from './app.component';
        import { UserComponent } from './user/user.component';
        import { TransformDirective } from './transform.directive';
        import { SafePipe } from './pipes/safe/safe.pipe';
        
        @NgModule({
          declarations: [
            AppComponent,
            UserComponent,
            TransformDirective,
            SafePipe
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

      - In the above AppModule imports array will have BrowserModule and AppRoutingModule

      - Once we add a module into imports then the exported members of those modules will be available in our module, so that we can use them.

      - imports accepts only a set of Angular Modules

      - declarables and Angular Modules that are exported by other modules can used inside our Angular Module

   3. **Exports Array:**

      - exports array means to expose the declarables and imorted Angular Modules from an Angular Module to Some other Angular Module
      - exports a list of components, directives, and pipes visible to modules that import this module.
      - So whatever we export from Angular Module those only will be available to import in other module
      - export array accepts set of :
        - **declarables** registered on an Angular Module which are **components, pipes and directives**
        - Angular Modules imported by it can be exported from it
      - whatever is exported from an Angular Module it will be available as module's public API
      - Angular Module (Module A), if added to the exports of another Angular Module(Module B) then whatever exported by Module A will be available as part of the Module B's public API

   4. **Providers Array:**

      - providers array is used to register a set of Injectable objects on an Angular Module
      - prividers is a list of dependency injection providers visible both to the contents of this module and to importers of this module.
      - providers accepts a set of Injectable objects
      - Adding these injectable objects here make them available on the injector of this Angular Module
      - So we can add these injectable objects as dependencies to the components, directives or any other building blocks
      - Make these dependencies available to inject in the declarables or services is the responsibility of Module's Injector
      - **what is Module's Injector?**

   5. **Bootstrap Array:**

      - bootstrap accepts a set of components that we want Angular to bootstrap when this module is bootstrapped.

      - It tells the Angular what are the components to be bootstrapped while bootstrapping the Angular Module

        ```typescript
        @NgModule({
          declarations: [
            AppComponent,
            UserComponent
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

      - In the above sample whenever Angular bootstraps the AppModule then It has to bootstrap the AppComponent which  is mentioned on bootstrap array that's why AppComponent template will be added in **index.html** as `<app-root></app-root>`. If we add any other component tags it will be ignored because those component will not instantiated during bootstrapping the module.

      - Generally bootstrap array will be present only on Root Module which is AppModule by convention

      - i.e only RootModule will have bootstrap array.

      - For Demo: we can add user component into bootstrap array and then add `<app-user></app-user>` tag in **index.html** . Now we can see both AppComponent and UserComponent templates in the index.html page 

      - whatever the components we add into the bootstrap array, those will be added to the **entryComponents** array

      - 

        

   6. **EntryComponents:**

      - EntryComponents array is mean to register the components that we want Angular to be able dynamically loaded into the view
      - entry component array accepts a set of components that we want to Angular to compile when the Angular Module is defined
      - components which are listed here can be dynamically loaded into the view
      - ComponentFactory created for each Component listed in this array and then it stores then in ComponentFactoryResolver
      - By adding components to this array, we are telling Angular that we want to bootstrap this components in an imperative way  

   7. 

      

      

      

      

      

      

      


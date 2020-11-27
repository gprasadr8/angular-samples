**Modules:**

- JavaScript wasn't built with modularity in mind

- Modularity was introduced using:

  **IIFE  	CommonJS 	Asynchronous Module Definition(AMD)**

- ES6 Modules provide modularity to the code

- ES6 modules were introduced to overcome issues with constructs **IIFE CommonJS and AMD**

- One of the major reason is to keep the global scope clean

- to provide a better way to share the code 

- To work with Dependencies in JavaScript

- One of the major characteristic of Modules is **import/export**

- import the module in other module

- export specific functionality out of a particular module which can be imported by some other modules

- Generally in JavaScript one file corresponds to one Module

- If we want to include a **.js** file as a module then we have set the type="module" in script tag

  ```html
  <!-- Based on the type attribute browser is going to consider myscript.js as a module and it's going to determine it's Dependency graph and so on -->
  <script src="myscript.js" type="module"/>
  ```

- Export from a module:

  ```typescript
  //to export some functionality then we have to use export keyword
  export const namedExport = function(){ ... }
  export const someSecrKey = "@dh%3#!";
  // we can export multiple things at once
  function myfunc(){ .... }
  class SomeClass {}
  interface MyInterface { ... }
  // to export all of above at once
  export {myfunc, SomeClass, MyInterface };
  // default export
  //default export will be only one export per module cannot have multiple default //exports
  function sampleFunction() { ... }
  export default sampleFunction;
  
  ```

- How to import functionality from other modules

  ```typescript
  import { namedExport } from '@some/module';
  import defaultExport from './some/other/module';
  import defaultExport, {nameExport} from '../module/outside/folder';
  // if two libraries have same name for exported functionality then use alias to import those
  import defaultExport as defaultAliasExport, {namedExport as namedAliasExport} from '../module/outside/folder';
  
  // to import everything that a module is exported 
  import * as aliasedExport from './relative-path/to-module';
  ```

- By default everything is private in nature inside the module, if you want to use something outside of the  module then we have to export by using **export** keyword

- name need not be the same for default export.

  ```typescript
  //For example:
  
     //in dashboard.component we have exported Dashboard class as a default export
     //while importing default export we don't need to use same name Dashboard.
     // we can use any name to import default export
  ```

  




- For samples please look into  ts-basics/module under ts-projects git repo
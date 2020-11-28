**How to create an Angular Application:**

**Angular CLI:**

- It's recommended to create an Angular App by using Angular CLI
- install Angular CLI -> npm install -g @angular/cli
- check if it installed properly -> ng --version
- generate Angular App -> ng new app-name
- serve generated app. Navigate to project folder and then -> ng serve
- change default host and port -> ng serve --host 0.0.0.0 --port 4201
- run unit tests  => ng test
- run E2E tests  => ng e2e
- run lint checks => ng lint
- generate build => ng build 
- extract i18n messages from templates  => ng i18n
- for more info follow https://angular.io/cli

```reStructuredText
$ ng new my-first-app
$ cd my-first-app
$ code .
It will open project in VS Code 
1. Open package.json file which contains the scripts property and it will have all the commands which we can run
2. "scripts": {
    "ng": "ng",
    "start": "ng serve", // it will do the local dev setup and serves on port: 4200
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e"
  }
3. ng serve 
4. to specify different port then ng serve --port 4242
5. Demo project: C:\dg\git-repo\angular\angular-projects\ng-projects\my-first-app

```


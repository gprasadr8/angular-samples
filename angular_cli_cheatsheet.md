# Cheatsheet: Angular CLI Reference



## Checking the Version

See which version of the CLI you’re using:

```bash
ng --version
```



### Updating the Version

Run this:

```bash
npm uninstall -g @angular/cli cache clean
npm install -g @angular/cli@latest
```



## Help

Get general help:

```bash
ng help
```

Or get help for a specific command:

```bash
ng help generate
```



## New Project

Generate a new project:

```bash
ng new my-app
```



And here are a few flags you can use:

- `--dry-run`: See which files would be created, but don’t actually do anything.
- `--verbose`: Be more chatty.
- `--skip-install`: Don’t `npm install`, useful when offline or with slow internet.
- `--skip-tests`: Don’t create spec files.
- `--skip-git`: Don’t initialize a git repo.
- `--source-dir`: Name of the source directory
- `--routing`: Add routing to the app.
- `--prefix`: Specify the prefix to use for components selectors.
- `--style`: Defaults to `css`, but can be set to `scss`.
- `--inline-style`: Use inline styles for components instead of separate files.
- `--inline-template`: Use inline templates for components instead of separate files.

Here’s an example with a few flags:

```bash
ng new my-app --prefix yo --style scss --skip-tests --verbose
```



## Generate All The Things

| Type                                | Command               |
| ----------------------------------- | --------------------- |
| Component                           | ng g c component-name |
| Directive                           | ng g d directive-name |
| Pipe                                | ng g p pipe-name      |
| Service                             | ng g s service-name   |
| Class (for creating model classess) | ng g cl class-name    |
| Guard                               | ng g g guard-name     |
| Interface                           | ng g i interface-name |
| Enum                                | ng g e enum-name      |
| Module                              | ng g m module-name    |



The `--dry-run` and `--verbose` flags can be used with any generate command.

Angular CLI is going to generate a folder only for Compoent and Module. 



## Serving

Serve your project

```bash
$ ng serve or ng s
```

Serve and open in your default browser automatically:

```bash
ng s -o
```

Serve to a different port:

```bash
ng s --port 5555
```



## Running Your Tests

```bash
ng test
```

And some flags you can use with the `test` command:

- `--watch`: Retest when some files change.
- `--code-coverage`: Add a coverage report.
- `--progress`: Show the progress while running the tests.
- `--browsers`: Specify which browsers to use.
- `--colors`: Use colors in the output or not.



## Linting

Run the linter:

```bash
ng lint
```

A few flags for the linter:

- `--fix`: Apply fixes for linting errors.
- `--force`: Force success even when linting fails.



## Building Your App

Build your app with the `build` command:

```bash
ng build
```

And here are some flags that you can use with **build**:

- `--target`: Specify the target for the build (e.g.: `--target production`).
- `--aot`: Use ahead of time compilation.
- `--base-href`: Specify the base href to use.
- `--deploy-url`: Specify the deployment url.
- `--extract-css`: Put the global styles in a CSS file instead of keeping it in the JavaScript.
- `--watch`: Rebuild every time a file changes.
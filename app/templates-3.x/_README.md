# <%- app_name %>

## Run

If you haven't done so already, install the [Tabris CLI](https://www.npmjs.com/package/tabris-cli) on your machine:

```
npm i tabris-cli -g
```

Then in the project directory, type:

```
npm start
```
<% if (ide_type === 'vsc') { %>Or choose "npm: start" from the Visual Studio Code task runner to make compile errors appear in the "Problems" view.<% } %>

This will start a Tabris.js code server at a free port and print its URL to the console. The app code can then be [side-loaded](<%- tabris_doc_url %>/developer-app.html#run-your-app) in the [developer app](<%- tabris_doc_url %>/developer-app.html) by entering that URL.

Alternatively you can also call the Tabris CLI directly:
<% if (proj_type === 'ts') { %>
```
tabris serve -a -w
```

This the same as running `npm start`. The `-w` switch starts the compiler in watch mode, meaning you do not have to re-start the server after each code change, and `-a` causes the app to reload automatically as well.
<% } else { %>
```
tabris serve -a
```

This the same as running `npm start`. The `-a` switch enables automatic reload whenever a source file changes.
<% } %>
## Test
<% if (tests === 'mocha') { %>
You can run compiler, linter and all unit tests with a single command:
```
npm test
```

Unit tests are executed with [Mocha](https://mochajs.org/) and located in the `test` directory. They can be run explicitly via:

```
npm run mocha
```

<% if (ide_type === 'vsc') { %>With the [Mocha Test Explorer](https://marketplace.visualstudio.com/items?itemName=hbenl.vscode-mocha-test-adapter) extensions individual tests can be triggered and monitored directly in Visual Studio Code.

<% } %>This project also includes a ESLint configuration that helps preventing common mistakes in your code. Most IDEs can display ESLint-based hints directly in the editor, but you can also run the tool explicitly via:

```
npm run lint
```
<% } else { %>
This project includes a ESLint configuration that helps preventing common mistakes in your code. Most IDEs can display ESLint-based hints directly in the editor, but you can also run the tool explicitly via:

```
npm test
```

<% if (proj_type === 'ts') { %>This will also check for compile errors.

<% } %>The initial rules defined in `.eslintrc` are supposed to warn against problematic patterns, but not enforce a strict code style. You may want to [adjust them](https://eslint.org/docs/rules/) according to your taste.<% if (proj_type === 'ts') { %> TypeScript specific rules are documented [here](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin) and JSX-Syntax specific rules [here](https://github.com/yannickcr/eslint-plugin-react). These can only be used in the dedicated `override` section of `.eslintrc`.<% } %>
<% } %>
## Debugging


### Android

<% if (ide_type === 'vsc') { %>To debug your application running on an Android device, first click the debug icon on the Visual Studio Code activity bar. This opens the debug side bar where you can launch the configuration "Debug Tabris on Android" and enter the device's IP address.<% } else { %>Tabris on Android supports any debugger that uses the V8 inspector protocol. This includes Visual Studio Code, WebStorm and the Chrome Browser.<% } %> More information can be found [here](<%- tabris_doc_url %>/debug.html#android).

### iOS

On iOS, the Safari developer tools [can be used for debugging](<%- tabris_doc_url %>/debug.html#ios).<% if (tests === 'mocha') { %>

Tabris.js unit tests support any debugger that works with Node.js.<% if (ide_type === 'vsc') { %> In Visual Studio Code, the focused unit test file can be debugged by launching "Mocha Current File" in the debug sidebar.
<% } %><% } %>
## Build

The app can be built using the online build service at [tabrisjs.com](https://tabrisjs.com) or locally using [Tabris.js CLI](https://www.npmjs.com/package/tabris-cli).

See [Building a Tabris.js App](<%- tabris_doc_url %>/build.html) for more information.

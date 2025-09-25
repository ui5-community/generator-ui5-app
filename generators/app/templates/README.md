# UI5 Application <%= namespace %>

Insert the purpose of this project and some interesting info here...

## Description

Insert the description here...

## Requirements

Either [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/) for dependency management.

## Preparation

Use `npm` (or `yarn`) to install the dependencies:

```sh
npm install
```

(To use yarn, just do `yarn` instead.)

## Run the App

Execute the following command to run the app locally for development in watch mode (the browser reloads the app automatically when there are changes in the source code):

```sh
npm start
```

As shown in the terminal after executing this command, the app is then running on http://localhost:8080/index.html. A browser window with this URL should automatically open.

(When using yarn, do `yarn start` instead. Also for all commands below, you can just replace `npm` by `yarn` in this case.)

## Build the App

### Unoptimized (but quick)

Execute the following command to build the project and get an app that can be deployed:

```sh
npm run build
```

The result is placed into the `dist` folder. To start the generated package, just run

```sh
npm run start:dist
```

Note that `index.html` still loads the UI5 framework from the relative URL `resources/...`, which does not physically exist, but is only provided dynamically by the UI5 tooling. So for an actual deployment you should change this URL to either [the CDN](https://sdk.openui5.org/#/topic/2d3eb2f322ea4a82983c1c62a33ec4ae) or your local deployment of UI5.

### Optimized

For an optimized self-contained build (takes longer because the UI5 resources are built, too), do:

```sh
npm run build:opt
```

To start the generated package, again just run:

```sh
npm run start:dist
```

In this case, all UI5 framework resources are also available within the `dist` folder, so the folder can be deployed as-is to any static web server, without changing the bootstrap URL.

With the self-contained build, the bootstrap URL in `index.html` has already been modified to load the newly created `sap-ui-custom.js` for bootstrapping, which contains all app resources as well as all needed UI5 JavaScript resources. Most UI5 resources inside the `dist` folder are for this reason actually **not** needed to run the app. Only the non-JS-files, like translation texts and CSS files, are used and must also be deployed. (Only when for some reason JS files are missing from the optimized self-contained bundle, they are also loaded separately.)

(When using yarn, do `yarn build:opt` and `yarn start:dist` instead.)

## Test the App

### Run the Tests

To run all tests, do:

```sh
npm test
```

This includes linting and running the unit and integration tests. After the tests have completed, the task ends, so this can be used for automated tests in a continuous integration scenario.

### Run Specific Tests Manually

You can manually open test pages by running `npm start` and then opening one of the following URLs in your browser:
<% if (lt1_124_0) { %>

- Unit tests: http://localhost:8080/test/unit/unitTests.qunit.html
- Integration tests: http://localhost:8080/test/integration/opaTests.qunit.html
- Both kinds of tests: http://localhost:8080/test/testsuite.qunit.html
  <% } else { %>
- Unit tests: http://localhost:8080/test/Test.qunit.html?testsuite=test-resources/com/myorg/myapp/testsuite.qunit&test=unit/unitTests
- Integration tests: http://localhost:8080/test/Test.qunit.html?testsuite=test-resources%2Fcom%2Fmyorg%2Fmyapp%2Ftestsuite.qunit&test=integration%2FopaTests
- Both kinds of tests: http://localhost:8080/test-resources/sap/ui/qunit/testrunner.html?testpage=%2Ftest%2Ftestsuite.qunit.html&autostart=true
  <% } %>

### Check the Code

To lint the code, do:

```sh
npm run lint
```

## License

This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.

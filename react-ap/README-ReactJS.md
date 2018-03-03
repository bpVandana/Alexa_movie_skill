

Below you will find some information on how to perform common tasks.
Updating to New Releases

Create React App is divided into two packages:

    create-react-app is a global command-line utility that you use to create new projects.
    react-scripts is a development dependency in the generated projects (including this one).

You almost never need to update create-react-app itself: it delegates all the setup to react-scripts.

When you run create-react-app, it always creates the project with the latest version of react-scripts so you’ll get all the new features and improvements in newly created apps automatically.

To update an existing project to a new version of react-scripts, open the changelog, find the version you’re currently on (check package.json in this folder if you’re not sure), and apply the migration instructions for the newer versions.

In most cases bumping the react-scripts version in package.json and running npm install in this folder should be enough, but it’s good to consult the changelog for potential breaking changes.

We commit to keeping the breaking changes minimal so you can upgrade react-scripts painlessly.
Folder Structure

After creation, your project should look like this:

ReactJS/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.js
    index.css
    index.js

Available Scripts

In the project directory, you can run:
npm start

Runs the app in the development mode.
Open http://localhost:3000 to view it in the browser.

The page will reload if you make edits.
You will also see any lint errors in the console.
npm test

Launches the test runner in the interactive watch mode.
See the section about running tests for more information.
npm run build

Builds the app for production to the build folder.
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.
Your app is ready to be deployed!

See the section about deployment for more information.
Supported Browsers

By default, the generated project uses the latest version of React.

You can refer to the React documentation for more information about supported browsers.
Changing the Page <title>

You can find the source HTML file in the public folder of the generated project. You may edit the <title> tag in it to change the title from “React App” to anything else.

Note that normally you wouldn’t edit files in the public folder very often. For example, adding a stylesheet is done without touching the HTML.

If you need to dynamically update the page title based on the content, you can use the browser document.title API. For more complex scenarios when you want to change the title from React components, you can use React Helmet, a third party library.

If you use a custom server for your app in production and want to modify the title before it gets sent to the browser, you can follow advice in this section. Alternatively, you can pre-build each page as a static HTML file which then loads the JavaScript bundle, which is covered here.
Installing a Dependency

The generated project includes React and ReactDOM as dependencies. It also includes a set of scripts used by Create React App as a development dependency. You may install other dependencies (for example, React Router) with npm:

npm install --save react-router

Alternatively you may use yarn:

yarn add react-router

This works for any library, not just react-router.
Code Splitting

Instead of downloading the entire app before users can use it, code splitting allows you to split your code into small chunks which you can then load on demand.

This project setup supports code splitting via dynamic import(). Its proposal is in stage 3. The import() function-like form takes the module name as an argument and returns a Promise which always resolves to the namespace object of the module.

Here is an example:
moduleA.js

const moduleA = 'Hello';

export { moduleA };

App.js

import React, { Component } from 'react';

class App extends Component {
  handleClick = () => {
    import('./moduleA')
      .then(({ moduleA }) => {
        // Use moduleA
      })
      .catch(err => {
        // Handle failure
      });
  };

  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Load</button>
      </div>
    );
  }
}

export default App;

This will make moduleA.js and all its unique dependencies as a separate chunk that only loads after the user clicks the 'Load' button.

You can also use it with async / await syntax if you prefer it.
Something Missing?

If you have ideas for more “How To” recipes that should be on this page, let us know or contribute some!


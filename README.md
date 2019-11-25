# React SpinUp.
## Prerequisites.
* `node`, `npm`, and `create-react-app` are installed.
## Adding React To an Existing Project.
1. `cd` into the project and run `npx create-react-app app`.
2. Rewrite the dependencies object in `/app/package.json` with the content below.
```
  "@fortawesome/fontawesome-svg-core": "^1.2.17",
    "@fortawesome/free-solid-svg-icons": "^5.8.1",
    "@fortawesome/react-fontawesome": "^0.1.4",
    "axios": "^0.18.0",
    "bootstrap": "^4.3.1",
    "formik": "^1.5.4",
    "http-proxy-middleware": "^0.19.1",
    "react": "^16.9.0",
    "react-dom": "^16.9.0",
    "react-bootstrap": "^1.0.0-beta.10",
    "react-redux": "^7.1.0",
    "react-router": "^5.0.1",
    "react-router-bootstrap": "^0.25.0",
    "react-router-dom": "^5.0.0",
    "react-scripts": "^3.1.1",
    "redux": "^4.0.4",
    "redux-thunk": "^2.3.0",
    "yup": "^0.27.0"
```
3. Run `rm -rf node_modules package-lock.json` in `/app`.
4. Run `npm install` in `/app`.
5. Delete every file in `app/src`.
6. Create a new file called `app/src/index.js` with the content below.
```
import React from 'react';
import ReactDOM from 'react-dom'
import 'bootstrap/dist/css/bootstrap.css';

const App = () => ( <h1 className="text-info">hello world</h1> );
ReactDOM.render(<App/>, document.querySelector('#root'));
```
* __Optional__ run `npm run start` in `/app` to see if the setup was successful.
## Setting Up The Dev Server.
1. Rewrite `/.gitignore` with the content below.
```
.DS_Store
/.sync-config.cson
/.idea
/vendor
/node_modules
/app/node_modules
/php/vendor
/app/src/setupProxy.js
/npm-debug.log
```
2. Create the file `/app/src/setupProxy.js` with the content below.
    * Each team member must do this step.
   * Make sure to update the target to match your _username_ and _project_ .
```
const proxy = require('http-proxy-middleware');
module.exports = function(app) {
   app.use(proxy('/apis', {
      logLevel: 'debug',
      target: "https://bootcamp-coders.cnm.edu/~username/project/php/public_html/",
      changeOrigin: true,
      secure: true, }));
};
```
## Adding React Router To A Project.
1. Create a new Component called Home in `/app/src/pages` with the content below.
```
import React from "react"

export const Home = () => {
   return (
      <>
         <h1>Home</h1>
      </>
   )
}
```
2. Create a new component called FourOhFour in `/app/src/pages` with the content below.
```
import React from "react"

export const FourOhFour = () => {
   return (
      <>
         <h1>Y U NO FIND</h1>
      </>
   )
};

```
3. Rewrite `/app/src/index.js` with the content below.
```
import React from 'react';
import ReactDOM from 'react-dom'
import 'bootstrap/dist/css/bootstrap.css';
import {BrowserRouter} from "react-router-dom";
import {Route, Switch} from "react-router";
import {FourOhFour} from "./pages/FourOhFour";
import {Home} from "./pages/Home";

const Routing = () => (
   <>
        <BrowserRouter>
         <Switch>
            <Route exact path="/" component={Home}/>
            <Route component={FourOhFour}/>
         </Switch>
      </BrowserRouter>
   </>
);
ReactDOM.render(<Routing/>, document.querySelector('#root'));
```

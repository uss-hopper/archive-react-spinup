# React SpinUp 
## Adding React To an Existing Project
### React Spinup must be completed by one member of the team but it is recommended that it is done as a group with the rest of the team members  watching/looking for missing semi colons.
1. cd into the project and run `npx create-react-app app`
2. add the following packages to package.json in the dependencies object
```
"@fortawesome/fontawesome-svg-core": "^1.2.17",
"@fortawesome/free-solid-svg-icons": "^5.8.1",
"@fortawesome/react-fontawesome": "^0.1.4",
"axios": "^0.18.0",
"bootstrap": "^4.3.1",
"formik": "^1.5.4",
"http-proxy-middleware": "^0.19.1",
"jquery": "^3.4.1",
"popper": "^1.0.1",
"react-redux": "^7.0.3",
"react-router": "^5.0.1",
"react-router-bootstrap": "^0.25.0",
"react-router-dom": "^5.0.0",
"redux": "^4.0.1",
"redux-thunk": "^2.3.0",
"yup": "^0.27.0"
```
3. run `npm install` in the /app directory
4. delete every file in `app/src`
5. create a new file called `app/src/index.js` and add the content below
```
import React from 'react';
import ReactDOM from 'react-dom'
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/js/bootstrap.bundle.min';


const App = () => ( <h1 className="text-info">hello world</h1> );
ReactDOM.render(<App/>, document.querySelector('#root'));
```
* __Optional__ run npm start in `/app` to see if the setup was successful
## Setting up the Dev Server.
1. add `/app/src/setupProxy.js` to the `/.gitignore` file
2. create the file `/app/src/setupProxy.js` and add the content below
	* make sure to update the file to match your _username_ and _project_ each team member must do this step
```
const proxy = require('http-proxy-middleware');
module.exports = function(app) {
	app.use(proxy('/apis', {
		logLevel: 'debug',
		target: "https://bootcamp-coders.cnm.edu/~username/project/php/public_html/",
		changeOrigin: true,
		secure: true,

	}));
};
```
## Add React Router To The 
1. create a new 





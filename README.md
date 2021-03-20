### React & Laravel Application
A fresh Laravel application comes with vue.js also in the Laravel community, vue.js is preferred to use as a JavaScript framework. Looking for using React instead? Yes, there is a convenient way of using React in the Laravel application.
We will be looking at how to do it in minutes of time.



##### This blog assumes the following :
Basic knowledge of PHP and Laravel
Basic knowledge of JavaScript and React
PHP, Composer, Laravel installer installed on your computer

##### Let's take a look at some step that we will be following: 
- Creating fresh Laravel application
- Creating wildcard route
- Installing react in the Laravel application
- Preparing a component to render.


So, let get started from the first step.

---

### A fresh Laravel application
At first, we need to create a fresh application. we will do it by using the Laravel installer.
```
$ laravel new reactapp
```
Once, the given command executes successfully, it's time to change the default route for rendering the single view file for all our application routes.
### Wildcard route
For creating a wildcard route in Laravel application. open routes/web.php and paste the given code. Basically, we will render a single blade file for all routes in the application.
```
// routes/web.php

    Route::view('/{path?}', 'app');
```
The given code will render app.blade.php for all requests in the application. Doing that will let us inject React components into the blade file. Now, create app.blade.php in paste the following in the blade file.
```
// resources/views/app.blade.php

    <!DOCTYPE html>
    <html lang="{{ app()->getLocale() }}">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <!-- CSRF Token -->
        <meta name="csrf-token" content="{{ csrf_token() }}">
        <title>React App</title>
        <!-- Styles -->
        <link href="{{ asset('css/app.css') }}" rel="stylesheet">
    </head>
    <body>
        <div id="app"></div>

        <script src="{{ asset('js/app.js') }}"></script>
    </body>
    </html>
```
This file contains a basic blade file boilerplate. The certain things which should be considered are : 
CSRF token
A single div with an id attribute
asset('js/app.js') within a script tag. 

### Installing React
Now, it's time to install react in our application. To do so there is a preset artisan command. Basically, we will be swapping vue.js with React.js. the preset command allows us to specify the javascript framework of our choice. The command is :
```
$ cd reactapp
$ php artisan preset react
```
In Laravel 8 - - There is no preset command available. so we need to install laravel/ui package at first and the use ui command for scaffolding react. for doing it the command is :
$ composer require laravel/ui
Once the package is installed we are ready to use ui command for installing react in our application.
$ php artisan ui react
Installing react in the Laravel application (ver 8.x)

This will create a basic react component Example.js inside resources/js/components also resource/js/app,js is update to use React in our application. 
React component file

Next, we will need to install our dependencies and watch the change in the js file for building the react components. for that, run the following command in the new terminal inside the same project folder.
$ npm install && npm run watch
Compiling JS files

### React Component
Once we are all done with the installation part, we will need to prepare our react component for rendering in app.blade.php. For that paste the following code inside resources/js/components/Example.js.
```
import React from 'react';
import ReactDOM from 'react-dom';
function Example() {
return (
<div className="container">
  <div className="row justify-content-center">
     <div className="col-md-8">
        <div className="card">
          <div className="card-header">ReactJS Example Component</div>
          <div className="card-body">I'm an example componen in React JS!</div>
      </div>
     </div>
  </div>
</div>
);
}
export default Example;
if (document.getElementById('app')) {
ReactDOM.render(<Example />, document.getElementById('app'));
}
```
This file basically renders a functional component in the blade file using ReactDOM. once you do this, you are now ready to serve the Laravel application. after serving, you can react component on your browser.
Rendering React componentYou can manually create a react component file and render them. you just have to edit the resources/js/app.js. initially, app.js looks something like this
resources/js/app.jsOn line 15, you should replace Example with your own component name.
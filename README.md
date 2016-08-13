# NODEJS

* ### IMPORTANT! Create a package.json very first 
```ssh
 $npm init // it will create a package.json file
```

* ### Download Express.js
```ssh
 $npm install express --save // it will download express.js locally
```

* ### Install nodemon module
```ssh
 $npm install -g nodemon
```
 * #### Start
```ssh
 $npm nodemon app.js
```

* ### Install 'ejs' template engine and setup

 * #### 1. Download ejs file locally
```ssh
 $npm install ejs --save
```
 * #### 2. Include in an 'app.js' file
```javascript
 var express = require("express");
 var app = express();
 app.set("view engine", "ejs");
```
 * #### 3. Create a 'views' folder and include every html-related files under this folder with '.ejs' extension.

* ## Rendering

 * ### 1st Method

   ```javascript
   app.get("/", function(request, response) {
     response.render("index", { //index can be any file that is under views folder
       title: "Example title"
     });
   });
   ```

 * ### 2nd Method - Routing
   >Using this Method, it will allow decrease size of app.js file and organize sources more effectively.

   1. create a /routes folder
   2. create a 'index.js' file // this is to export function
   3. Write functions to export ex)
   ```javascript
   exports.home = function(request, response) {
     response.render("home", {
       title: "Title to render"
     });
   };
   ```
   4. Require a the 'index.js'
   ```javascript
   //in case there is only one file to include
   var routes = require(./routes/index.js);
   //in case there are more than one files to include
   var routes = require(./routes);
   ```
   5. Usage Example
   ```javascript
   app.get("/", routes.home);
   ```

 * ## Static assets
 > Add codes at the top part of app.js

  ```javascript
  var path = require("path");
  app.use(express.static(path.join(__dirname, "public")));

  ```
* #### Create "public" folder and create "images", "javascripts" and "stylesheets" subfolders

* ## Forever
 1. Install
```ssh
 $npm install -g forever
```
 2. Go to the directory that has app.js
 3. Initiate
 ```ssh
 $forever start app.js
 ```

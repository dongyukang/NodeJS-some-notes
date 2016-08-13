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
# NODEJS INSTALLATION

Automated node.js installers for OS X and Ubuntu

**node.js only** (no dev tools)

```bash
# install node.js without development dependencies
curl -fsSL bit.ly/nodejs-min | bash

# using wget instead of curl (Ubuntu)
wget -nv bit.ly/nodejs-min -O - | bash
```

**node.js + dev tools**

Install node.js and basic development tools - git, node, gcc, pkg-config, etc

```bash
curl -L bit.ly/nodejs-dev-install -o ./node-dev; bash ./node-dev
```

<!-- bit.ly/easy-install-node -->

## Screencast

[How to Setup a VPS for node.js Development](https://www.youtube.com/watch?v=ypjzi1axH2A) - [(3:06 installing node.js](https://www.youtube.com/watch?v=ypjzi1axH2A#t=186))

## Choosing a specific version

```bash
echo "Current node.js version is $(curl -fsSL https://nodejs.org/dist/index.tab | head -2 | tail -1 | cut -f 1)"
```

```bash
# To install a specific version rather than defaulting to latest
# latest version at time of writing are v4.4.1 and v5.9.1
echo "v5.9.1" > /tmp/NODE_VER
```

## Notes

* [OS X](#apple-os-x)
* [Ubuntu Linux](#ubuntu-linux)
* [Important Notes](#other-things-you-should-know)

### Apple OS X

First you need to **Install XCode Command Line Tools**

```bash
xcode-select --install
```

Then you need to **Accept the XCode License** by running any command installed by Xcode with sudo. We'll use git.

```bash
sudo git --version
```

You can scroll to the bottom by hitting shift+G (capital G).

Type `agree` and hit enter to accept the license.

Now you can install node.js

```bash
curl -fsSL bit.ly/nodejs-dev-install -o /tmp/node-dev.sh; bash /tmp/node-dev.sh
```

*TODO*: Make it easier to accepting the license (automatic?)

### Ubuntu Linux

```bash
wget -nv bit.ly/nodejs-dev-install -O /tmp/node-dev.sh; bash /tmp/node-dev.sh
```

### Other things you should know

This is what gets installed:

* rsync
* curl
* wget
* git
* xcode / brew / build-essential / pkg-config / gcc
* node (including npm)
* jshint

**NOTE**: If `fail2ban` is not already securing ssh, you will be asked to install it.


Front-End Extras
================

These are **not installed**, but you may wish to use them if you're doing front-end work as well

* bower
* uglifyjs
* yo
* jade
* less

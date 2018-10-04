# Shopping Cart Project

#### using Node.js, Express, Handlebars, and MongoDB
source: [Shopping Cart Academind](https://www.youtube.com/watch?v=riSKBb7KbFI&list=PL55RiY5tL51rajp7Xr_zk-fCFtzdlGKUp&index=3)
##### Part 1: Intro and setup
---
First we need to use express to generate a new project:

```
Terminal: express shopping-cart --view=hbs
```
Then we navigate to the project folder and run __npm install__ to install all dependencies.

Now just by accessing __http://localhost:3000/__ at chrome we can see Express is already installed.

We need to do some cleanup. we delete users.js under routes. and inside app.js we delete some lines related to users route.

Then we import Bootstrap cdn and jquery into layout.hbs and we are all set. 

##### Part 2: Product Index View
---
Now we want to import a navbar from bootstrap. We make a folder called partials and paste navbar code inside it and call it nav.hbs.

In order to include it in layout.hbs we need to install another handlebar package that has more features than the built-in handle bar. 

```angularjs
Terminal: npm install --save express-handlebars
```
Now we have to import it to app.js on the top:
```angularjs
var expressHbs = require('express-handlebars');
```
Then in app.js we need to add another line to the "view engine setup" section and it should look like this:
```angularjs
app.set('views', path.join(__dirname, 'views'));
```
with
```angularjs
app.set('views', path.join(__dirname, 'views'));
app.engine('.hbs', expressHbs({
    defaultLayout: 'layout', 
    extname: '.hbs', 
    layoutsDir: __dirname+'/views/layouts', 
    partialsDir:__dirname+'/views/partials'}));
app.set('view engine', '.hbs');
```
_This part didn't entirely match to the tutorial and I had to research myself)_

Now we can include the header partial into layout.hbs file liek this:
```angularjs
{{> nav}}
```
Then we make a new folder called "shop" under views and its important to go to rotues/index.js and change the route to index.hbs file including the shop folder.

Now its time to make the index file and style it and make a thumbnail of products inside it using bootstrap, etc.
##### Part 3: MongoDB
---
First we make sure we installed MongoDB. 
Then we run mongodb server by running this :
```angularjs
Terminal: mongod
```
Now we need to install Mongoose extension into the app. simply:
```angularjs
npm install --save mongoose
```
Then we go to app.js and require mongoose.
```angularjs
var mongoose = require('mongoose');
```
Then we need to connect to the database using the localhost port 27017 which is the default mongodb port.
Here is what we have to add to app.js for connecting to server:
```angularjs
mongoose.connect('localhost:27017/shopping');
```
__Important__: There is no need to create the database, when we define it in app.js, it will be automatically made if its not already made.

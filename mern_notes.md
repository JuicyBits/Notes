## Useful command line commands
`npm init`  
- Initialize a Node project

`npm i *package name* --save`  
`npm i *package name* --save-dev`  
`npm i *package name* -g`  
`bower init`  

##  Express
`app.use(express.static('public'));`
- Pass the name of the directory that contains the static assets to the express.static middleware function to start serving the files directly.

`app.use((req, res, next) => {})`  

`app.all((req, res, next) => {})`  
- Used for loading middleware functions at a path for all request methods
- Not derived from any HTTP methods  

`res.sendFile()`  
- Serve static files (e.g. an HTML page)

`res.redirect()`

## Bower
```
"overrides": {
    "*dependency name*"{
        "main": [
            "requiredFile.js"
            "requiredFile.css"
        ]
    }
}
```
- override bower dependencies for use with wiredep if dependencies' own bower.json does not display all required files (or if you would prefer a different file)


#### .bowerrc
- The file where Bower looks for its configuration information

## Gulp
> "A Task Manager for your web projects"

#### wiredep
- Searches bower.json for dependencies  
```
<!-- bower:js -->  
<!-- endbower -->
```

#### gulp-inject
- Inject local dependencies
```
<!-- inject:css -->  
<!-- endinject -->
```

#### nodemon
- Restart server upon file changes ('watch' files can be chosen)

## Mongo
- **MongoD** is the server
- **Mongo** to access mongo commands from command line  

#### Terminal Commands
`show dbs`
- View all databases  

`show collections`
- View all collections in current DB  

`use [db name]`
- Set active DB  

`db.[collection name].find().pretty();`
- View *pretty* form of all data in collection

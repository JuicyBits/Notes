# Little Book of ASP.NET Core
## What is ASP.NET Core?
- Open Source
- Runs on microsoft's .NET runtime
  
## Why ASP.NET Core?
- **Speed**
    - Compiled code (faster than interpreted code)
    - Optimized for multithreading and asynchronous tasks
- **Thousands of packages**
- **Security**
    - Out of the box `Cross-Site Request Forgery (CSRF)` prevention

## Note for .NET 4 Devs
- ASP.NET Core is a complete ground up re-write of ASP.NET 
- Decoupled from System.Web, IIS, and Windows

## ASP.NET Core Project Parts
- **Program.cs** and **Startup.cs**
    - `Startup` class is where middleware can be added
- **Model**, **View**, **Controller** directories store MVC Components
- **wwwroot** directory contains static assets like CSS, JS, image files
    - Can be bundled and minified automatically
- **appsettings.json** contains configuration settings ASP.NET Core will load on startup
    - Can be used to store Database Connection Strings 

## MVC Basics
### Common pattern for MVC Code:
- The **Controller** receives a request and looks up some info in the DB
- The **Controller** creates a model with the information and attaches it to a **view**
- The **view** is rendered and displayed in the user's browser
- The user clicks a button / submits a form, which sends a new request to the controller and the cycle repeats

## Controllers
- Store **action** methods that handle routing within a controller
    - Can return JSON, views, or HTTP status codes

## Models
### Two Types:
- **Entity Models** which represent a database item, or entity
- **View Models** which are combined with a view and sent back to the user's browser
  
Simple models can be referred to as **POCO**s, or *Plain Old C# Object*
- This means they are database agnostic

## Views
- Built using the **Razor** templating language
    - Combination of C# and HTML
  
## Entity Framework Core
- Database-agnostic
- Uses the **Database Context** and **Connection Strings** to establish a connection to a DB
  
## Security and Identity
- The `MVC + Individual Authentication` template comes with user registration / login out of tbe box
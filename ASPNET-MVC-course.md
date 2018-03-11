### *Section 1:* Getting Started
#### MVC Architectural Pattern
- Model View Controller
- Widely adopted as an architecture for web applications
- Better separation of concerns

**Model**
- Application data and behavior in terms of its problem domain
- Independent of the UI
- A class that includes the application data and rules
- Independent of persistence (can be stored in any databases)

**View**
- HTML markup displayed to users

**Controller**
- Responsible for handling HTTP requests

**Router**
- Selects the right controller to handle the request

**Action**
- A method in a controller responsible for handling a request

**NuGet**
- A package manager similar to `NPM` and `Bower`
- Used to manage dependencies of app
- Used to upgrade existing dependencies when newer versions are available

#### Plugins
- Productivity Power Tools
- Web Essentials
- ReSharper

#### Shortcuts
- `ctrl + F5` -> Start without debugging
- `F2` -> rename selected
- `ctrl + m + m` -> collapse selected code block / html tag
- When hovering over action name within a view (ReSharper): `Alt + Enter` -> `Create Action`
#### Snippets
- `prop` -> `public TYPE Type { get; set; }`
- `ctor` -> create constructor
- `mvcaction4` -> create action template

#### Files
- `App_Start` -> `BundleConfig.cs`
    - Defines various bundles and client side assets

#### C# Syntax
- Add `?` after argument data type to make it nullable:
    `public void functionName(int? intVar){}`
- Write `C#` code within a `.cshtml` file by prefixing with an `@`

| Function | Definition |
|-------|---------|
|`Enumerable.Any()`|Determines whether a sequence contains any elements.|
|`Enumerable.SingleOrDefault()`|Returns the only element of a sequence that satisfies a specified condition or a default value if no such element exists; this method throws an exception if more than one element satisfies the condition.|


**IEnumerable, ICollection, List**

| Interface | Scenario |
|-------|--------|
|IEnumerable|You only want to iterate over the elements in a collection|
|IEnumerable< T >|You only need read-only access to that collection|
|ICollection|You want to modify the collection or you care about its size|
|ICollection< T >| |
|IList|You want to modify the collection and you care about the ordering and / positioning of elements in that collection|
|IList< T >| |
|List| Since in object oriented design you want to depend on abstractions instead of implementations, you should never have a member of your own implementations with the concrete type List/List. |

#### Examples
**A request to /customers/delete/1 by convention is handled by**
    `CustomersController.Delete(int id)`

#### Conventions
- Name `partial views` with an `_` prefix
- Name `ViewModels` with a `ViewModel` suffix
- `EntityFramework` recognizes foreign key convention `[MODEL NAME]Id`
- Name `DbContext`s with a `_` prefix

#### Misc
- ASP.NET uses `bootstrap` by default as its front end framework
- Use `bootswatch.com` for bootstrap templates
- `Navigation Properties` allow for navigating between / linking multiple model types and objects together


### Course Layout
- ASP.NET MVC Fundamentals
- Entity Framework (Code-first)
- Forms
- Validation
- Build RESTful Services
- Client-side Development
- Authentication and Authorization
- Performance Optimization
- Building a Feature Systematically
- Deployment

### *Section 2:* ASP.NET MVC Fundamentals
#### Action Results
```
namespace Vidly.Controllers
{
    public class MoviesController : Controller
    {
        // GET: Movies
        public ActionResult Random()
        {
            var movie = new Movie() { Name = "Shrek!" };

            return View(movie);
        }
    }
```
- Actions performed within controller methods in response to HTTP requests

| Type | Helper Method |
|-----|:---------:|
| ViewResult | `View()` |
| PartialViewResult |` PartialView()` |
| ContentResult | `Content()` |
| RedirectResult | `Redirect()` |
| RedirectToRouteResult | `RedirectToAction()` |
| JsonResult | `Json()` |
| FileResult | `File()` |
| HttpNotFoundResult | `HttpNotFound()` |
| EmptyResult | `HttpNotFound()` |

#### Action Parameters
- Parameter passed to controller from request can be linked to a controller action with the same name

**Parameter Sources**
- In the URL: `/movies/edit/1`
- In the query string: `/movies/edit?id=1`
- In the form data: `id=1`

#### Convention-based Routing
- `routes.MapRoute()` order matters, so specify from most-to-least granular
- `routes.MapRoute([Route Name], [URL Pattern], [Defaults])`
```
routes.MapRoute(
    "MoviesByReleaseDate",
    "movies/released/{year}/{month}",
    new { controller = "Movies", action = "ByReleaseDate" }
    );
```

**Limiting Route Parameters**
```
routes.MapRoute(
    "MoviesByReleaseDate",
    "movies/released/{year}/{month}",
    new { controller = "Movies", action = "ByReleaseDate" },
    new { year = @"\d{4}", month = @"\d{2}"}
    );
```
- Fourth argument to `MapRoute` is for parameter constraints

#### Attribute Routing
- Activate Attribute Routes in `RouteConfig.cs`:
    `routes.MapMvcAttributeRoutes();`
- Add route template to controller:
    `[Route("movies/released/{year}/{month:regex(\\d{2}):range(1, 12)}")]`
    - Apply a constraint using `:`

**Constraints**
- min
- max
- minlength
- maxlength
- int
- float
- guid

#### Passing Data to Views
- Avoid using `ViewData` or `ViewBag` when possible
- Use `controller`'s `view` method:
    `return view(data)`

#### View Models
- Used to import and access multiple models within one view

#### Razor Views
- Can use `<text></text>` tags to render markup with no enclosing tags
- Use `@{}` to write C# code blocks within views
- Add comments with:
    ```
    @*
        comment text
        on multiple lines
    *@
    ```

#### Partial Views
- Not only for re-using markup, but also for breaking up large views into manageable chunks
- Access partials with `@Html.Partial("_PartialName")`
- Unless specified, model passed to parent view will be passed to partial view
    - To specify, pass a second parameter to `@Html.Partial()`

### *Section 3:* Working with Data
#### Entity Framework
- Object Relational Mapper (O/RM)
- Maps data from Relational DB into usable objects  
- `DbContext` -> Class representing Database
- `DbSet` -> Classes representing tables

#### LINQ
- Used to query `DbSet`s and automatically generate `SQL` queries to DB on runtime
- Entity Framework keeps track of add / modify / deletes on DbSet and automatically generates `SQL` queries reflecting changes

#### Workflows
- Database First
- Code First

#### DbFirst vs CodeFirst
**DbFirst**  
[Domain Classes] <-- [Entity Framework] <-- [Database]

**CodeFirst**  
[Domain Classes] --> [Entity Framework] --> [Database]
- Increases productivity
- Full versioning of database
- Much easier to build an integration test db

**CodeFirst Myths**  
- Does not give you full control over the Database

#### Code-first Migrations
**Package Manager Console Commands**  
- `enable-migrations`
- `add-migration [MIGRATION MODEL NAME]`
- `add-migration [MIGRATION MODEL NAME] - force`
    - Overwrite last migration
    - Treat like `git` commits for Db model
- `update-database`
    - Run migration and generate database
- Allows for a consistent, trackable way to version database through migrations

#### Changing the Model
- Aim for small migrations
    - Many developers struggle with code-first development because they push 'atomic commits' that are far too large

#### Seeding the Database
- In `code-first` workflow, data should not be added to DB directly, but through `migrations`
- Exception is for arbitrary test data that serves no integral function in app  
- `Sql("INSERT INTO ...")`

#### Overriding Conventions
- Use `DataAnnotations` to override property requirements:
    ```
    public class Customer
        {
            public int Id { get; set; }
            [Required] //DataAnnotation
            [StringLength(255)] //DataAnnotation
            public string Name { get; set; }
            public bool IsSubscribedToNewsletter { get; set; }
            public MembershipType MembershipType { get; set; } // Navigation property
            public byte MembershipTypeId { get; set; }
        }
    ```
- Requires `using System.ComponentModel.DataAnnotations;`
**Data Annotations**
- `[Display(Name = "[DISPLAY TEXT]")]`
- `[Required]`
- `[StringLength(255)]`


#### Querying Objects
- Controllers must have access to `DbContext`:
    ```
    private ApplicationDbContext _context;

        public CustomersController()
        {
           _context = new ApplicationDbContext();
        }
    ```

- Remember to dispose of DbContext when done:
    ```
    protected override void Dispose(bool disposing)
            {
                _context.Dispose();
            }
    ```

- `var customers = _context.Customers;`
    - Entity Framework does **NOT** immediately query database after this line
    - DB query occurs when iterating over `customers`
    - Use `var customers = _context.Customers.ToList();` to execute db query

#### LINQ Extension Methods
- `_context.Movies.Where(m => m.GenreId == 1)`
- `_context.Movies.Single(m => m.Id == 1);`
- `_context.Movies.SingleOrDefault(m => m.Id == 1);`
- `_context.Movies.ToList();`

#### Eager Loading
- When a `DbSet` is joined with another, Entity framework does not query linked DbSet by default -- solve with `Eager Loading`
- `_context.Movies.Include(m => m.Genre);`
- Requires `using System.Data.Entity;`

### *Section 4:* Building Forms
#### Create Form
```
@using (Html.BeginForm("Save", "Customers"))
{
    <div class="form-group">
        @Html.LabelFor(m => m.Customer.Name)
        @Html.TextBoxFor(m => m.Customer.Name, new { @class = "form-control" })
    </div>
    <button type="submit" class="btn btn-primary">Save</button>
}
```

#### HTML Helper Methods
- `Html.BeginForm`
- `Html.LabelFor`
- `Html.TextBoxFor`
    - Inherits constraints from `model` (e.g. `StringLength`, `Required`)
- `Html.CheckBoxFor`
- `Html.DropDownListFor`
- `Html.HiddenFor`

#### Model Binding
- Use `[HttpPost]` before an action to handle `POST` requests
```
[HttpPost]
    public ActionResult Create(Customer customer)
    {
        ...
    }
```

#### Saving Data
```
_context.Customers.Add(customer);
_context.SaveChanges();
```
- Changes to `_context` do not modify database until `.SaveChanges()`
- When `.SaveChanges()` is called, `SQL` statements for all modifications to `_context` are generated and DB is modified

#### Edit Form
**Microsoft Suggests:**
```
var customerInDb = _context.Customers.Single(c => c.Id == customer.Id);
TryUpdateModel(customerInDb);
```
- Issues with this approach:
    - Security vulnerabilities.  What if user should not have permission to update **All** customer attributes?

**Microsoft workaround:**
```
var customerInDb = _context.Customers.Single(c => c.Id == customer.Id);
TryUpdateModel(customerInDb, "", new string[]{ "Name", "Email" });
```
- Why this is worse
    - If attribute name changes, code breaks

**Best Solution**
```
customerInDb.Name = customer.Name;
customerInDb.Birthdate = customer.Birthdate;
customerInDb.MembershipTypeId = customer.MembershipTypeId;
customerInDb.IsSubscribedToNewsletter = customer.IsSubscribedToNewsletter;
```
- Can be done automatically with `AutoMapper`
    - Maps property names of source and target and maps them by convention
    - `Mapper.Map(customer, customerInDb)`

**Addressing Security Risk**
- Can create a `dto` class (Data Transfer Object) with only 'update-safe' properties:
    - `UpdateCustomerDto`
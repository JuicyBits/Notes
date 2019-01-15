# ASP.NET Core - Beginner
## Terminal Commands 
- `dotnet --version`
- `dotnet [option] --help`
- `dotnet new [template name]`
- `dotnet new web -o mywebapp`
    - Create web app template and new directory 
  
## Razor Pages and CRUD
```
[BindProperty]
public Customer Customer { get; set; }
```
- `[BindProperty]` tells the page that `Customer` should be filled with posted form information

```
public async Task OnGetAsync()
    {
        Customers = await _db.Customers.AsNoTracking().ToListAsync();
    }
```
- `AsNoTracking()` is useful for read-only data
- Does not keep track of entity changes, so `SaveChanges()` is not an option

```
// Razor Page
<button type="submit" asp-page-handler="delete" asp-route-id="@customer.Id" class="btn btn-danger">Delete</buttonı>

// Codebehind
public async Task<IActionResult> OnPostDeleteAsync(int id)
    {
        ...
    }
```
- Handler verbage / name does not matter as long as handler declaration and method match (e.g `asp-route-handler="tacobell"` and `public async Task<IActionResult> OnPostTacobellAsync(int id)`)

## Logging and Diagnostics
- Variables can be shared between models, provided they have the same `name`, `data-type`, and `attribute`
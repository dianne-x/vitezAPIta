--- Visual Studio 2022 ---
project template: ASP.NET Core Web API
[x] place solutioon and project in the same directory
framework: .NET 8.0
[x] configurate for https
[x] enable Open API Support (swagger)
[x] use controllers (for MVC...)

--- view ->  SQL Server Object Explorer --- 
localdb\MSSQLLocalDb -> new Querry
<magic>make the database</magic> 

--- to package manager console ---
Install-Package Microsoft.EntityFrameworkCore.SqlServer
Install-Package Microsoft.EntityFrameworkCore.Design
Install-Package Microsoft.EntityFrameworkCore.Tools

Scaffold-DbContext "Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=nascar;Integrated Security=True;Connect Timeout=30;Encrypt=False;Trust Server Certificate=False;Application Intent=ReadWrite;Multi Subnet Failover=False" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -Context NascarDbContext -DataAnnotations

## az adatbazist kikell valasztani, LENYITNI es onnan a propertisbol meglehet talalni a dbcontext connection stringet

## NascarDBContext helyett lehet akarmi csak ne utkozzon semmi massal


--- to appsettings.json: ---
"ConnectionStrings": {
    "DefaultConnection": "Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=nascar;Integrated Security=True;Connect Timeout=30;Encrypt=False;Trust Server Certificate=False;Application Intent=ReadWrite;Multi Subnet Failover=False"
  },

(tetjére)


--- to program.cs ---
## builder.Services.addcontroller fölé mindenféle képpen különben az utan mar read-only futtatasnal.


var connectionString = builder.Configuration
	.GetConnectionString("DefaultConnection");
builder.Services
	.AddDbContext<_MyDbContext_>
	(opt => opt.UseSqlServer(connectionString));
	
--- Controllers forlder -> Add -> new scaffolded item... ---

-> API Controller with actions using EF ->
model class::: _MyModel_
dbcontext class::: _MyDbContext_
controller name::: _MyModel_s (default)

--- allow CORS (to program.cs) ---


builder.Services.AddCors(
    options => options.AddDefaultPolicy(
        builder => builder
        .AllowAnyOrigin()
        .AllowAnyHeader()
        .AllowAnyMethod()));

// add this BEFORE app.UseHttpsRedirection();
app.UseCors();

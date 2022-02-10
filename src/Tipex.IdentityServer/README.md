
# The project

To replace Auzre Identity Platfom using IdentityServer4 managed by Duende

- Version: 6.0.4 (.NET 6.0.1)
- Use Visual Studio 2022 as it is the only editor that support NET6.

# How this project was created

The IdentityServer templates (by  Duende) for the dotnet CLI are a good starting point for the quickstarts. To install the templates open a console window and type the following command:

> dotnet new -i IdentityServer4.Templates

This ``Tipex.IdentityServer`` use **Duende IdentityServer with ASP.NET Core Identity** template (e.g. ``isaspid``)

> dotnet new isaspid -n Tipex.IdentityServer

Then replace `Microsoft.Entity.FramworkCore.SqlLite` with  `Microsoft.Entity.FramworkCore.SqlServer`. This include correcting database data type from `sqllite` to `mssql` for `.cs` under **Migrations** folder.

# Configurations

Use this section to setup your applicaiton settings with the use of [user-secrets](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0&tabs=windows#enable-secret-storage). Don't check in secrets in the `appsettings.json` for application settings.

## Serilog


```
{
  ...
  "Serilog": {
    "MinimumLevel": {
      "Default": "Debug",
      "Override": {
        "Microsoft": "Warning",
        "Microsoft.Hosting.Lifetime": "Information",
        "Microsoft.AspNetCore.Authentication": "Debug",
        "System": "Warning"
      }
    }
  }
 ...
}
```

## ConnectionStrings (for user store)

`DefaultConnection` is pointing to MSSQL instance for user store, application store, scope/permission to resources

```
{
  ...
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=AspIdUsers.db;"
  }
 ...
}
```


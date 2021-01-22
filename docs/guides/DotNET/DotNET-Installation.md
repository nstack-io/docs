---
currentMenu: DotNET-Installation
---

The .NET SDK is available from the NuGet gallery and is written in .NET Standard, so it can be used in both .NET Framework, .NET Core, and .NET 5. The package is called `NStack.SDK`, you can install it by searching for it through the Visual Studio Package Manager or by running the following command in the Package Manager Console

```PowerShell
Install-Package NStack.SDK
```

Or if you're using the dotnet CLI, run the following command:

```PowerShell
dotnet add package NStack.SDK
```

## DI setup
The SDK is built with DI support in mind and can be quickly set up in your `startup.cs` file in `ConfigureServices`:

```C#
services.AddSingleton<NStackConfiguration>(r => new NStackConfiguration
{
    ApiKey = "MyApiKey",
    ApplicationId = "MyApplicationId",
    BaseUrl = "MyBaseUrl"
});
services.AddTransient<INStackRepository, NStackRepository>();
services.AddTransient<INStackLocalizeService, NStackLocalizeService>();
```

Best practice is to not hard code the configuration values but to fetch them from your application settings.
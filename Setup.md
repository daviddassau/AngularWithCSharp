# Setup

1. Set up new .NET project 
2. Right-click on project title in click on NuGet Package Manager. Install the `AngularJS.Route` package.
3. Right-click on `Controllers` and add a new controller. Name it `HomeController`.
4. Open up the `Global.asax` file, and paste in the following inside the `protected void Application_Start()` method:
```C#
// webapi config
GlobalConfiguration.Configure(WebApiConfig.Register);

//mvc config
RouteConfig.RegisterRoutes(RouteTable.Routes);
FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
BundleConfig.RegisterBundles(BundleTable.Bundles);
```

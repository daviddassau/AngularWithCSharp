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
5. Right-click on the `Views` folder and add a new folder called `Home`. In that new Home folder, add a new View called `Index`, with Template set to Empty (without model), Use a layout page by clicking on the dots, navigate to Views > Shared, and click on `_Layout.cshtml`.
6. In the new `Index.cshtml` you can delete everything except the `<h2>` tags.
7. In the `App_Start > RouteConfig.cs` on the `defaults` line, replace it with this:
```C#
defaults: new { action = "Index", controller="Home", id = UrlParameter.Optional }
```
8. Right-click on your project name, and go to Proerties. Under the Web tab, in the Start Action section, select the "Don't open a page" radio button. This will prevent a new window from popping up every time you run your program.
9. Navigate to your `BundleConfig.cs` file, and underneath the Bootstrap stuff, add the following:
```C#
bundles.Add(new ScriptBundle("~/bundles/angular").Include(
          "~/Scripts/angular.js",
          "~/Scripts/angular-route.js",
          "~/app/app.js"),
          .IncludeDirectory("~/app/controllers","*.js",true));
```
10. Navigate to the `_Layout.cshtml` and add this underneath the Bootstrap Scripts down at the bottom: `@Scripts.Render("~/bundles/angular")`. Then inside the opening body tag (probably somewhere around line 10) and add `ng-app="NameOfYourApplication"`.
11. Create a new folder in your project called `app`. Inside that folder, make two more folders, called `partials` and `controllers`.
12. In the `app` folder create a new JS file called `app.js`. Inside that file, put this line of code:
```JavaScript
var app = angular.module("NameOfYourApplication",["ngRoute"]);

app.config(["$routeProvider", function ($routeProvider) {
    $routeProvider.when("/",
    {
        templateUrl: "/app/partials/index.html",
        controller: "HomeController"
    })
}]);
```
13. In the `Index.cshtml` file, delete the `h2` tags, and put the following:
```HTML
<div ng-view>
          
</div>
```

#### That's pretty much it for setting up AngularJS with your .NET project. Below are additional steps you can take to get things to show up in your browser when you run the program.

1. Add an `index.html` file to the `partials` folder. Put these lines of code in:
```HTML
<h2>
    {{message}}  
</h2>
```
2. Add a `HomeController.js` to the `controllers` folder. Put these lines of code in:
```JavaScript
app.controller("HomeController", ["$scope", 
    function ($scope) { 
        $scope.message = "Hello World"; 
    }
]);
```
3. If you build and run the program now, you should be able to see "Hello World" in the browser

### Optional things
- In `_Layout.cshtml` around line 19 that starts with `@Html.ActionLink...`, you can change `"Application name"` to your actual application name.
- At the footer, change `My ASP.NET Application` to your app name.

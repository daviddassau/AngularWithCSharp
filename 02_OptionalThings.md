# Optional Steps

### Below are additional steps you can take to get things to show up in your browser when you run the program.

1. In the `index.html` file in the `partials` folder, put these lines of code in:
```HTML
<h2>
    {{message}}  
</h2>
```
2. In the `HomeController.js` in the `controllers` folder, put these lines of code in:
```JavaScript
app.controller("HomeController", ["$scope", 
    function ($scope) { 
        $scope.message = "Hello World"; 
    }
]);
```
3. If you build and run the program now, you should be able to see "Hello World" in the browser

### Other Optional Things
- In `_Layout.cshtml` around line 19 that starts with `@Html.ActionLink...`, you can change `"Application name"` to your actual application name.
- At the footer, change `My ASP.NET Application` to your app name.

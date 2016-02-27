---
layout: page
title: Angular
permalink: /angular/
---

## Bootstrap Angular application

```html
<div ng-app="appName"></div>
```

## Modules

Create a module that depends on module1 and module2

```js
angular.module('app', ['module1', 'module2']);
```

Get reference of a module named app

```js
var app = angular.module('app')
```

## Filters


```js
angular.module("myModule").filter("squareNumber", function(){
    return function(num){
        return num * num;
    };
});
```

Usage:

```html
<span> {% raw %}{{value || squareNumber }} {% endraw %}</span>
```

### Options

* currency - Formats a number as a currency.
* date - Formats a number as a date.e.g. {{1288323623006 | date:'yyyy-MM-dd HH:mm:ss Z'}}
* html - Prevents the input from getting escaped by angular.
* json - Converts a JavaScript object into JSON string.
* lowercase - lowercases a string.
* number - formats a number as text

## Controllers

```js
angular.module("myModule").controller("SampleController", function($scope){
    $scope.songTitle = "Hand of Doom";
});
```

In the view

```html
<div ng-controller="SampleController">
    {% raw %}<div>{{songTitle}}</div>{% endraw %}
</div>
```

## Services

Services in Angular are singletons. Only one instance of the service is created in the Angular application's lifetime.

```js
angular.module("myModule").service("sampleService", function(){
    var svc = this;
    var songTitles = ["Here Comes The Pain", "South of Heaven", "Raining Blood", "Skeleton Christ"];

    svc.addSong = function(song){
        songTitles.push(song);
    };
    svc.getSongTitles = function(){
        return songTitles;
    }
});
```

## Directives

```js
myModule.directive("directiveName", function (injectables) {
    return {
        restrict: "A",
        template: "<div></div>",
        templateUrl: "directive.html",
        replace: false,
        transclude: false,
        scope: false,
        require: ["someOtherDirective"],
        controller: function($scope, $element, $attrs, $transclude, otherInjectables) { ... },
        link: function postLink(scope, iElement, iAttrs) { ... },
        priority: 0,
        terminal: false,
        compile: function compile(tElement, tAttrs, transclude) {
            return {
                pre: function preLink(scope, iElement, iAttrs, controller) { ... },
                post: function postLink(scope, iElement, iAttrs, controller) { ... }
            }
        }
    };
})
```

//Update this section based on docs.angularjs.org
### Built-in Directives

+ **ng-app**: To auto-bootstrap the application
+ **ng-controller**: To attach a controller to a view
+ **ng-view**: To render the template of the current route to the main layout (`index.html`). Requires `ngRoute` module to be installed
+ **ng-show / ng-hide*: Shows/hides content within the directive based on boolean equivalent of value assigned</li>
+ **ng-if**: Places or removes the DOM elements under this directive based on boolean equivalent of value assigned</li>
+ **ng-model**: Enables two-way data binding on any input controls and sends validity of data in the input control to the enclosing form</li>
+ **ng-class**: Provides an option to assign value of a model to CSS, conditionally apply styles and use multiple models for CSS declaratively
+ **ng-repeat**: Loops through a list of items and copies the HTML for every record in the collection</li>
+ **ng-options**: Used with HTML select element to render options based on data in a collection</li>
+ **ng-href**: Assigns a model as hyperlink to an anchor element</li>
+ **ng-src**: Assigns a model to source of an image element</li>
+ **ng-click**: To handle click event on any element</li>
+ **ng-change**: Requires ng-model to be present along with it. Calls the event handler or evaluates the assigned expression when there is a change to value of the model</li>
+ **ng-form**: Works same as HTML form and allows nesting of forms</li>
+ **ng-non-bindable**: Prevents AngularJS from compiling or binding the contents of the current DOM element</li>
+ **ng-repeat-start and ng-repeat-end**: Repeats top-level attributes</li>
+ **ng-include**: Loads a partial view</li>
+ **ng-init**: Used to evaluate an expression in the current scope</li>
+ **ng-switch**: conditionally displays elements</li>
+ **ng-cloak**: to prevent Angular HTML to load before bindings are applied

## Routes

```js
myModule.config(function($routeProvider){
    $routeProvider.when("/home", {templateUrl:"templates/home.html",
                                  controller: "HomeController"}).when("/details/:id", {template: "templates/details.html",                                       controller:"ListController"})
                .otherwise({redirectTo: "/home"});
});
```
## Register Services

```js
Service: module.service( 'serviceName', function );

Factory: module.factory( 'factoryName', function );

Provider: module.provider( 'providerName', function);
```

## Utility Functions

* angular.copy - Creates a deep copy of source
* angular.extend - Copy methods and properties from one object to another
* angular.element - Wraps a raw DOM element or HTML string as a jQuery element
* angular.equals - Determines if two objects or two values are equivalent
* angular.forEach - Enumerate the content of a collection
* angular.toJson - Serializes input into a JSON-formatted string
* angular.fromJson - Deserializes a JSON string
* angular.identity - Returns its first argument
* angular.isArray - Determines if a reference is an Array
* angular.isDate - Determines if a value is a date
* angular.isDefined - Determines if a reference is defined
* angular.isElement - Determines if a reference is a DOM element
* angular.isFunction - Determines if a reference is a Function
* angular.isNumber - Determines if a reference is a Number
* angular.isObject - Determines if a reference is an Object
* angular.isString - Determines if a reference is a String
* angular.isUndefined - Determines if a reference is undefined
* angular.lowercase - Converts the specified string to lowercase
* angular.uppercase - Converts the specified string to uppercase


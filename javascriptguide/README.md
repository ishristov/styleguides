# JavaScript Guide

## Config

- Strict mode

  - Start every JavaScript file with the line *'use strict';*. This will make the parser more strict and should throw more errors into the browser console. E.g. using a variable without declaring it first will throw an error. This will force you to write better code and will minimize the bugs tremendously.

    ```javascript
    'use strict';
    /* rest of the code */
    ```

## General Formatting

- Spacing

  - Always use 2 spaces (soft tabs) for indentation. Tabs might be rendered differently on different environments. Using 2 spaces also helps in making the lines shorter if there is a lot of nesting.

  - Put the opening curly brace on the same line, separated by a single space. The closing brace must be on a new line.

  - The expression in the if statement should be separated by a single space from each side.

  - Leave one empty line after blocks for improved visibility.

    ```javascript
    // no
    var x;
    if(condition){
      x = 1;
    }else{
      x = 2;
    }
    return x;

    // yes
    var x;
    if (condition) {
      x = 1;
    } else {
      x = 2;
    }

    return x;
    ```

  - Never skip braces.

    ```javascript
    // no
    if(something)
      return x;

    // yes
    if (something) {
      return x;
    }
    ```

- Quotes and semicolons

  - Use single quote marks for variables. Using single quotes in JavaScript and double quotes in HTML allows us to copy HTML blocks safely from HTML to JavaScript and vise versa easily without breaking anything. Using double quotes is allowed for nested quotes.

    ```javascript
    // yes
    var name = 'Michael';
    var weirdMarkup = '<a href="//google.com">Google</a>';
    ```

  - Always use semicolons at the end of assignments. The history behind this is that it was known that if the semicolon is omitted, the line break might not end the statement and that would break the code or cause hard to debug proplems. Partialy that is true, but only for very few scenarios that are not used often. Lately there is even a [movement](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding) against the semicolons but currently still most of the coders are using them and we want to use what most of the people are using. 

    ```javascript
    // no
    var someFunction = function () {
      /* ... */
    }

    // yes
    var datetime = new Date();
    var Car.prototype.extras = function () {
      /* ... */
    };

    function foobar () {
      /* ... */
    } // semicolon not needed because this is not an assigment
    ```

- Naming

  - Use camelCase for functions, variables, methods and instances but use PascalCase for classes. All filenames should be in lowercase.

    ```javascript
    var Person = function (firstName, age) {
      this.firstName = firstName;
      this.age = age;
      this.isTeenager = this.isTeenager(age);
    };

    Person.prototype.isTeenager = function (age) {
      return age > 12 && age < 20;
    };

    var someGuy = new Person('Peter', 25);
    ```

  - Use namespaces for the global code. Don't clutter the global window object with random variables. Use a namespace to store all variables instead.

    ```javascript
    // for todo app
    var todo = {};

    todo.isEditing = false;

    todo.utils = {
      getCurrentUser: function () {
        /* ... */
      }
    };

    todo.settings = {

    };

    todo.currentUser = todo.utils.getCurrentUser();
    ```

- Arrays and objects

  - Use array and object literals instead of constructors. Using Array for constructor might return wrong length depending on the elements.

    ```javascript
    // no
    var arr = new Array();
    var obj = new Object();

    // yes
    var arr = [];
    var obj = {}; // for consistency with []
    ```

  - Use .spice method for copying an array. It is usually the fastest, doesn't change the original array and is simple enough.
    ```javascript
    // yes
    var copied = arr.slice(0);
    ```

  - Don't use reserved words. Use synonyms in their place. [List of reserved words](http://es5.github.io/#x7.6.1).

    ```javascript
    // no
    var car = {
      class: 'family'
    };

    // no
    var car = {
      klass: 'family'
    };

    // yes
    var car = {
      type: 'family'
    };
    ```

- Other guidelines

  - Use shortened code where possible

    ```javascript
    // no
    if (x != '') {

    }

    if (arr.length > 0) {

    }

    // yes
    if (x) {

    }

    if (arr.length) {

    }
    ```

  - Try to use === and !== instead of == and !=. The === and !== compare both the value and the type, whereas the == and != compare the values after their types are conversed to be the same. The problem is that the logic that JavaScript uses to make this coercion is not what one would always expect. For more info, check [this thread](http://stackoverflow.com/a/359509/582865).

  - Don't use eval() for data that contains user input as it introduces serious security risks.

  - Use string concatenation if you have to add a long string.
  
    ```javascript
    var longString = 
      'Some string that is super long ' +
      'to be fitted into one line can be safely concatenated ' +
      'because it will be more easier to read and it won\'t be ' +
      'affecting performance';
    ```

  - Use /** .. */ for multiline comments and // for single line comments and always put an empty line between comment blocks.

  - Declare assigned variables first and unassigned variables last. In any case, declare all variables at the top of their scope.

    ```javascript
    function () {
      var items = getItems();
      var people = [];
      var allCosts;
      var x;

      /* other code here */
    }

  - Use setter and getter functions for retrieving and setting values.

    ```javascript
    var personName = person.getName();
    person.setName('Jack');
    ```

## jQuery

- Prefix jQuery object variables with $. This helps making the jQuery objects easily distinguishable from plain JavaScript objects/variables.

  ```javascript
  // no
  var nav = $('.nav');

  // yes
  var $nav = $('.nav');
  ```

- If a selector is used more than once, cache it into a variable.

  ```javascript
  $('body').on('click', '.nav li', function () {
    var $clicked = $(this);

    $clicked.addClass('active');

    $('.breadcrumb').text($clicked.text());
  });
  ```
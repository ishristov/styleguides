# CSS Guide

## Preparation

- Learn and use [SASS](http://sass-lang.com/) or other preprocessor. This greatly improves the workflow and the readability and gives the tools to accomplish more with less code. The following guide suggests you are familiar with it.

- Feel free to normalize the CSS vendor styles with [normalize.css](https://necolas.github.io/normalize.css/). This CSS file targets only what needs to be targeted in order to achieve improved consistency across different browsers and devices. It fixes some bugs but also keeps the usefull vendor styles instead of erasing everything (like CSS resets do).

## General Formatting

- Spacing

  - Always use 2 spaces for indentation. Tabs might be rendered differently on different environments. Using 2 spaces also helps in making the lines shorter if there is a lot of nesting.

  - Remove trailing white spaces.

  - Put each selector on a new line and separate it from other selectors by 1 empty line. If a new context of selectors is started, put a comment for additional separation.

    ```css
    /* Header */
    .nav {
      ...
    }

    .logo {
      ...
    }

    /* Main content */
    .page {
      ...
    }

    .title {
      ...
    }
    ```

  - Put 1 space between the selector and the { and put the } on a new line.
    ```css
    h1 {
      ...
    }
    ```

  - Put each declaration on a new line.

  - Put the column immediately after the property and put 1 space after the column.
    ```css
    .section {
      padding: 20px;
      border: 1px solid #aaa;
    }
    ```

  - If a grouping of selectors is used, place each selector on a new line. 
    ```css
    .header,
    .content,
    .footer {
      padding: 20px;
    }
    ```

- Use hyphen for a separator between the words in the selector name.
  ```css
  // no
  .contentWrapper

  // no
  .content_wrapper

  // yes
  .content-wrapper
  ```

- Use lowercase for CSS selectors, properties and values.
  ```css
  // no
  TABLE {
    BORDER: 1PX SOLID #AAA;
  }

  // yes
  table {
    border: 1px solid #aaa;
  }
  ```
- Don't specify units for zero values
  ```css
  // no
  .element {
    margin: 0px;
    border-width: 0px;
    top: 0px;
  }

  // yes
  .element {
    margin: 0;
    border-width: 0;
    top: 0;
  }
  ```

- Don't add the zero for values between -1 and 1.
  ```css
  // no
  small {
    font-size: 0.75em;
  }

  // yes
  small {
    font-size: .75em;
  }
  ```

- Keep the nesting to a reasonable level. When a preprocessor is used (like SASS), this can easily get out of hand, but try not to go over 3-4 levels max as this should be enough for almost anything. Just name properly, group blocks of similar content and add comments if appropriate.
  ```css
  // no, no, no
  .page-wrapper{
    .header {
      .header-inner {
        .header-nav {
          li {
            a {
              span {
                ...
              }
            }
          }
        }
      }
    }
  }

  // yes
  /* Generic layout */
  .page-wrapper {
    ...
  }

  /* Header styles */
  .header {
    ...
  }

  .header-inner {
    ...
  }

  .header-nav {
    li {
      ...
    }

    a {
      span {
        ...
      }
    }
  }
  ```

## Naming Conventions

- Use mostly classes and avoid using IDs for styling.

- Never reference js- classes in the CSS, as they should be used only for JavaScript hooks.

- Use class names that show the *purpose* of the element and avoid using strictly presentational or meaningless class names. It is allowed to use a presentational class name but only if it is a generic class that might be applied to different elements as a modifier or a helper. Try to write as reusable CSS as possible.
  ```css
  // no
  .red-heading {
    /* heading styles */
    color: red;
  }

  // yes
  .heading {
    /* heading styles */
  }

  .red {
    color: red;
  }

  // yes
  .left /* helper */
  .hidden /* helper */
  .disabled /* helper */
  ```

- Use as short class names as possible but long enough to be instantly clear what they are used for.
  ```css
  // no
  .navigation {}
  .button {}

  // yes
  .nav {}
  .btn {}
  ```

- If elements share the same styling, move it to another class and use modifiers if some of the elements needs additional styling.
  ```
  // no
  .btn {
    color: #fff;
    background: #333;
    border: 1px solid #aaa;
  }

  .btn-big {
    padding: 5px 10px;
    font-size: 16px;
    color: #fff;
    background: #333;
    border: 1px solid #aaa;
  }

  // yes
  .btn {
    color: #fff;
    background: #333;
    border: 1px solid #aaa;

    &.big {
      padding: 5px 10px;
      font-size: 16px;
    }
  }
  ```

- Avoid using selectors that are a combination of an element and a class unless necessary. If the class name is obvious enough, the additional element selector won't add any value but will only make the rule unnecessary longer. Such use is allowed if the class that is used is a modifier or a helper class.
  ```css
  // no
  ul.nav {}
  h1.main-heading {}
  div.section {}

  // yes - obvious enough
  .nav {}
  .main-heading {}
  .section {}

  // yes - modifier or helper class used
  input.disabled {}
  li.active {}
  ```

- Avoid using !important at any cost unless for a modifier or helper class that should ALWAYS overwrite other styles. !important is very powerful but it can easily be abused if not understood corectly so don't use it if you don't know what you are doing. It would be a better approach to rewrite your other rules so its use is not required.
  ```css
  // yes - used only for modifier classes 
  .hidden {
    display: none !important;
  }

  .error {
    color: red !important;
  }
  ```

- Sort the property declarations by importance - positioning properties first, box-model second, followed by typography and visual styling. This way you'll always know where to find a specific property.
  ```css
  .recommended-order {
    /* positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1;
    /* box-model */
    display: block;
    float: left;
    width: 100px;
    height: 100px;
    padding: 0;
    margin: 0;
    /* typography */
    font: normal 16px Arial;
    color: #aaa;
    text-align: left;
    /* visual */
    background-color: #eee;
    border: 1px solid #333;
  }
  ```

- If you want more strict rules, consider using the BEM or [BEM-like](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) methodology. It's just a naming methodology and it will force you to look at your elements as being blocks (.search), elements (.search__btn) and modifiers (.search--full). In the BEM, the CSS selectors will contain enough information about the HTML structure as well - in the classes given as a an example, the .search__btn will always be a child of the .search and ..search--full will be additional class for the .search to modify it somehow.

## File Organization

- Use any file and folder organization that you like, as long as it is not super weird. Feel free to use the example from below.
  ```
  /build
  /images
  /js
  /scss
    /components
      _buttons.scss
      _lightbox.scss
      _table.scss
      ...
    /globals
      _colors.scss
      _layout.scss
      _variables.scss
    /plugins
      _jquery.something
      _jquery-ui.2.0.3
    /pages
      dashboard.scss
      login.scss
      settings.scss
    app.scss
  ```

- The app.scss will import all SCSS partials that are used accross the site. Every other page will have a specific file - pages/pagex.scss that will be used for that page only.
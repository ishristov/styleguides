# CSS Guide

## Preparation

- Learn and use [SASS](http://sass-lang.com/) or other preprocessor. This greatly improves the workflow and the readability and gives the tools to accomplish more with less code.

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

## Naming Conventions
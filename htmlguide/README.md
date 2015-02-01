# HTML Guide

## Meta Tags and Settings

- Use HTML5. Just put the following line at the top of your HTML document.
  ```html
  <!DOCTYPE html>
  ```

- Write valid HTML according to http://validator.w3.org/nu/ if possible. This guarantees that you'll see less bugs than if you write messy code.

- Make sure the file is encoded with UTF-8 (without BOM) by checking the encoding settings in your editor. Also put the following line at the top of the head element - before the title and other content elements.
  ```html
  <meta charset="utf-8" />
  ```

- Use a viewport meta declaration to improve the default visibility on mobile devices.
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  ```

- Include CSS files at the top of the document (in the head element) and JavaScript files at the bottom (before closing the body element). This is required for better performance and faster loading times.

- Omit the protocol when using URLs in the code. This can prevent issues with unloaded content when one of the sites is using SSL and the other is not.
  ```html
  // no
  <script src="http://code.jquery.com/jquery-2.1.3.min.js"></script>

  // yes
  <script src="//code.jquery.com/jquery-2.1.3.min.js"></script>
  ```

- Omit type attributes when including CSS and JavaScript files with link and script elements.

## General Formatting

- Always use 2 spaces for indentation. Tabs might be rendered differently on different environments. Using 2 spaces also helps in making the lines shorter if there is a lot of nesting.
  ```html
  // yes
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
  ```

- Remove trailing white spaces.

- Use a new line for all block level elements (headings, div, table, ul) for both the opening and the closing tag and always indent child elements. It is also acceptable to put inline elements on new line too if that improves the readibility or the line is becoming too long.
  ```html
  // no
  <table><tr><td>Cell 1</td><td>Cell 2</td></tr></table>

  // no
  <p>Paragraph text
  </p>

  // yes
  <table>
    <tr>
      <td>Cell 1</td>
      <td>Cell 2</td>
      <td>
        <span class="btn btn-edit"></span>
        <span class="btn btn-delete"></span>
      </td>
    </tr>
  </table>

  // yes
  <span>Text with <b>important</b> meaning</span>
  ```

- Use double quote marks for attribute values. Using double quotes in HTML and single quotes in JavaScript allows us to copy HTML blocks safely from HTML to JavaScript in vise versa easily without breaking anything. 
  ```html
  // no
  <div class=main></div>

  // no
  <div class='main'></div>

  // yes
  <div class="main"></div>
  ```

- Don't omit opening or closing HTML tags, even if HTML5 allows it for some elements.
  ```html
  // no
  <p>Paragraph element without closing

  // yes
  <p>That's more likely</p>
  ```

- Use lowercase for HTML tags, attributes and values. Data attributes are even case sensitive when used in JavaScript.
Capital letters can be used for user defined strings, e.g. alt and value attributes.
  ```html
  // no
  <INPUT TYPE="Button" data-action="Edit" value="Edit User" />

  // yes
  <input type="button" data-action="edit" value="Edit User" />
  <img src="alfa.png" alt="Alfa Romeo car" />
  ```

## Semantics

- Use semantic HTML. That is using a for anchors, h1-h6 for headings, p for paragraphs, etc. This is good for accessibiity and reusability.
  ```html
  // no
  <div class="heading">Main heading of the page</div>

  // no
  <span onclick="changePage('settings')">Open Settings</span>

  // yes
  <h1>Main heading of the page</h1>

  // yes
  <a href="/settings">Open settings</a>
  ```

- Use HTML markup only for the structure and the content, not for presentational layers and visual elements that are not part of the content.
  ```html
  // no
  <div>Content section</div>
  <br/>
  <hr/>
  <br/>
  <div>Content section</div>

  // yes
  <div class="section">
    Content section
  </div>
  <div class="section">
    Content section
  </div>

  .section {
    margin-top: 20px;
    border-top: 1px solid #666;
    padding-top: 20px;
  }
  ```

- Provide alternative content for images
  ```html
  // yes
  <img src="logo.png" alt="Company Logo" />
  ```

## Forms

- Every form input or other element should have a label for it. This is absolutely mandatory for checkboxes and radio buttons - placing the form element as a child of the label will automatically associates them without the need to use for and id attributes.
  ```html
  // no
  <p>Enter Username</p>
  <input type="text" name="username" />

  // yes
  <label for="username">Enter Username</label>
  <input type="text" name="username" id="username" />

  // yes
  <label>
    Enter Username
    <input type="text" name="username" />
  </label>
  ```

- Don't set values for the boolean attributes (disabled, selected, checked).
  ```html
  // no
  <input type="text" name="company" disabled="disabled" />

  // no
  <input type="text" name="company" disabled="true" />

  // yes
  <input type="text" name="company" disabled />

  // yes
  <select>
    <option value="0" selected>Check option</option>
    ...
  </select>
  ```
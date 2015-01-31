# HTML Guide

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

- Don't omit opening or closing HTML tags, even if HTML5 allows is for some elements.
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

- Use semantic HTML. That is using <a> for anchors, <h1>-<h6> for headings, <p> for paragraphs, etc. This is good for accessibiity and reusability.
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

	. section {
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

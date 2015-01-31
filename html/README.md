# HTML Guide

## General

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
	```
	.

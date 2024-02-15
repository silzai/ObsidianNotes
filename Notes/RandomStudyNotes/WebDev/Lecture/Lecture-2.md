# 3 ways to embed `css` in HTML:
- Inline:
	- with `style=""` attribute inside a tag
- Embedded:
	- will put a `<style>` tag inside the head, and in the`<head>` we will add styles to relevant like this: `p {style=""}` , this will apply the style to all the `<p>` 
- External:
	- different files for CSS and HTML
	- will link the file using this syntax, if I have a CSS file named `main.css` like this:
```html
<head>
	<link rel="stylesheet" href="main.css">
</head>
```
## Cascading
- can add multiple `<link>` to the `<head>`, but the last `<link>` will be used
- 
# HTML 

## Block and Inline Tags

### Block Tags

Block tags will display one on top of the other. They take up the entire width of the page. Example tags:

```html
<p>

This is a paragraph

</p>


<p>

This is another paragraph

</p>

```

### Inline Tags

Inline tags will display one after the other in a line. Example tags:

```html

<a href="https://link1.com">link1</a>
<a href="https://link2.com">link2</a>

```
## Structure

```html
<!DOCTYPE html> <!-- Every html file needs this-->

<html> 

	<head>

		<!-- Meta tags define metadata. Inside the meta tags are attributes that the meta tags need -->
		
		<meta charset="UTF-8">
		<meta name="description" content="This is an awesome website.">
		
		
		<title>Website</title> 
	
	</head>
	
	<body>
		
		<!-- Defines a header for the body. <h1> being the largest and <h6> the smallest -->
		
		<h1>
			<p>
			
			<!-- This is a paragraph tag -->
			
			</p>
		
			<nav>
			
			<!-- Put navigational links here: home page, links, contacts, etc. -->
			
			<nav/>
		
		</h1>
		
		<main>
		
			<article> 
			<!-- Could be used for a blog, article, etc. -->
			
				<section>
				
				<!-- Section 1 of blog post -->
				
				</section>
				
				<section>
				
				<!-- Section 2 of blog post -->
					
					<aside>
					
					<!-- Content not directly related to the website content, i.e., advertisements. -->
				
				</section>
			
			
			</article>
		
		</main>
		
		<footer>
		
		</footer>
	
	</body>

</html>


```

## Modifying Tags

```html
<br/> <!-- <br/> will add white space -->


<hr/> <!-- <hr/> creates a horizontal line -->

<big>big</big>  <!-- makes the word big -->

<small>small</small> <!-- makes the word small -->

<b><i>paragraph</b></i> <!-- bolds and italicizes -->

H<sub>2</sub>O <!-- makes the character a subscript -->

10<sup>2</sup> <!-- makes the character a superscript -->

```

## Links

```html
<!-- Adds a link with title Andrew's github -->

<a href="https://www.github.com/alackie3" ><h1>Andrew's Github</h1></a>

<!-- Adds a link with a header title. It can be text, a header, etc. The target clause will open the link in a new tab --> 


<a href="https://www.github.com/alackie3" target="_blank">Andrew's Github</a> 

<!-- Link to page 2 to navigate website for a file in the same directory. -->

<a href="page2.html">Page 2</a>

<!-- Link to page 2 to navigate website for a file in a different directory. -->

<a href="dir1/page2.html">Page 2</a>
```

## Images

```html

<!-- This links to an image on the internet -->

<img src="https://cdn.picpng.com/dinosaur/dinosaur-picture-33674.png" alt="A really scary dinosaur."/>

<!-- This links to a locally stored image. -->

<img src="cat.jpg" alt="A really cute cat."/>

<!-- Resize image in pixel (could change aspect ratio)

Note: You can choose to set the width OR heigh and HTML will automatically adjust the aspect ratio -->

<img width="100" height="100" src="cat.jpg" alt="A really cute cat."/>

<!-- Embed a link within an image -->

<a href="https://catvills.com/wp-content/uploads/2021/01/tabby-cat-names.jpg">
	<img width="100" height="100" src="cat.jpg" alt="A really cute cat."/>
<a/>

```

## Videos

```html

<!-- Displays unplayable video -->

<video src="video.mp4"></video>

<!-- Adds controls and size-->

<video src="video.mp4" controls width="300"></video>

<!-- Adds thumbnail -->

<video src="video.mp4" poster="thumb.jpg" autoplay controls width="300"></video>

<!-- Adds autoplay and loops video -->

<video src="video.mp4" poster="thumb.jpg" autoplay loop controls width="300"></video>

```

## Lists

### Unordered

```html
<ul>

	<li><a href="www.apples.com">Apples</a></li>
	<li><Oranges</li>
	<li><Bananas</li>

</ul>
```

### Ordered

```html

<!-- Lists, embedded lists, links in lists -->

<ol type="A"> <!-- Or type="a", type="I", type="i" -->

	<li><a href="www.apples.com">Apples</a></li>
	<li><Oranges</li>
	
		<ol>
			<li>Mandarin</li>
			<li>Tangerine</li>
		</ol>
		
	<li><Bananas</li>

</ol>


```

### Description List

```html
<!-- List items with a description -->

<dl>

	<dt>Apples</dt>
	<dd>- They are red</dd>
	
</dl>
```

## Tables

```html

<table>

	<caption><h2>List of numbers</h2></caption>
	
	<thead>
	
		<tr> <!-- Table row with table data -->
		
			<th>one</th>
			<th>two</th>
			<th>three</th>

		</tr>
	
	</thead>		
	
	<tbody>
	
		<tr> <!-- Table row with table header -->
		
			<td colspan="2">four</td> <!-- colspan will span the value an n number of columns -->
			<td>five</td>
			<td>six</td>
		
		</tr>
	
	</body>
		


</table>
```

## Divs and Spans

Spans are inline elements and divs are block elements.

```html

<span>span1</span> <!-- Will be inline -->
<span>span2</span>

<div>div1</div> <!-- Will be blocks -->
<div>div2</div>


```

## Input Tags

User input tags can be defined, but JavaScript is required to make them interactive.

```html

<!-- Creates box to input text -->

<input type="text" />

<!-- Will add text to the box -->

<input type="text" value="This is a text box"/>

<!-- Will hide input for password entry -->

<input type="password" />

<!-- Creates box to input date -->

<input type="date" />

<!-- Creates box to input email -->

<input type="email" />

<!-- Creates slider -->

<input type="range" />

<!-- Creates file input box -->

<input type="file" />

<!-- Creates checkbox -->

<input type="checkbox" />

<!-- Creates radio button -->

<input type="radio" />

<!-- Creates submit button -->

<input type="submit" />

<!-- Will create textbox with 10 rows and 30 cols -->

<textarea rows="10" cols="30">

<!-- Text are can be resized -->

This is a paragraph. <!-- This will be displayed in the text box -->

</textarea>


```

## Forms

```html

<form>
	<input type="submit"/>
</form>

```

## iframe

Embed websites inside websites.

```html

<!-- Creates an iframe and displays the website in src. If the iframe can't be displayed then the message (sorry) is. Can also define the size and border. Some websites can't be used for iframes-->

<iframe src="https://www.github.com/alackie3" frameborder="0" width="1000" height="800">Sorry</iframe>

```

## Meta Tags

Defining data about data.

```html

<meta charset="UTF-8">
<meta name="description" content="Your Description"
<meta name="author" content="Andrew">
<meta name="keywords" content="HTML, Tutor">
<meta name="viewport" content="width=device-width, inital-scale=1.0"

```

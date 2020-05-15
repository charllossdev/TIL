# Create Css in Javascript

### Task

Complete the code in the editor so that it creates a clickable button satisfying the following properties:

* The button's id is btn.
* The button's initial text label is . After each click, the button must increment by . Recall that the button's text label is the JS object's innerHTML property.
* The button has the following style properties:
  + A width of 96px.
  + A height of 48px.
  + The font-size attribute is 24px.

### Submissions

This is a new style of challenge involving Front-End rendering. It may take up to  seconds to see the result of your code, so please be patient after clicking Submit. The Submissions page contains screenshots to help you gauge how well you did.

# Dev
```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Button</title>
        <style>
          #btn {
              width: 96px;
              height: 48px;
              font-size: 24px;
          }
        </style>
    </head>
    <body>
        <button id="btn">0</button>
        <script type="text/javascript">
        /* Create a button */
        var buttonCounter = document.getElementById('btn');

        /* What to do when the button is clicked */
        buttonCounter.addEventListener('click', function() {
            /* Increment number on button's label by 1 */
            buttonCounter.innerHTML = +(buttonCounter.innerHTML) + 1;
        });
        </script>
    </body>
</html>

```

# Css Basics in Javascript
In this article, we discuss some basics of writing JS (JavaScript) and CSS code in an HTML file. Note that we assume a certain level of basic HTML knowledge.

## Templates

### Basic Format
We use the following template to write JavaScript and CSS code to an HTML file:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>

        <style>
            /* Write CSS styles here */
        </style>
    </head>
    <body>
        <script>
            /* Write JS code here */
        </script>
    </body>
</html>
```

We write our CSS style code between the <style> and </style> tags, and our JS code between the <script> and </script> tags.

Note: Any text between <!-- and --> is considered to be an HTML comment. These comments won't render on the webpage, but we can read them if we view the page's source code. For content between tags that contain actual code (i.e., style and script), we enclose comments between `/* and */`

### Working with Separate Documents
In an instance where all our code is located in separate files (i.e., we have a .html file with our HTML, a .css file with our CSS, and a .js file with our JS code), we use this template to tell our HTML file where to find the JS and CSS files:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>

        <!-- Link to the style sheet in the 'head' section -->
        <link rel="stylesheet" href="css-file-path" type="text/css">
    </head>

    <body>
        <!-- Link to the JS code in the 'body' section -->
        <script src="js-file-path" type="text/javascript">
        </script>
    </body>
</html>
```
Let's look at what this code does:

* By putting `<link rel="stylesheet" href="css-file-path" type="text/css">`, where css-file-path is the path of the .css file, in the head section (i.e., between the <head> and </head> tags), we're telling the document to use the style sheet at the location referenced by the href attribute.
* By putting `<script src="js-file-path" type="text/javascript">`, where js-file-path is the path of the .js file, in the body section (i.e., between the <body> and </body> tags), we're saying that we want to run a script using the JS code at the location referenced by the src attribute.

### Create css basic in Javascript with button tag

We use the `<button>` tag to create a clickable button that has the following optional attributes:

* id: the button's unique identifier within the page
* class: the CSS class(es) used to style the button

The text enclosed between the button's opening `(<button>) and closing (</button>)` tags is the label that displays on the button. We can also access this text using the innerHTML property of the JS button object (see the JavaScript section below). The basic syntax for an HTML button looks like this:
```html
<button id="buttonIdentifier" class="buttonStyleClass">Click Me</button>
```


Consider the following code:
```js
var clickMeButton = document.createElement('button');
clickMeButton.id = 'myButton';
clickMeButton.innerHTML = 'Click Me';
clickMeButton.style.background = '#4FFF8F';
document.body.appendChild(clickMeButton);
```

Now, let's walk through what it does:

1. document.createElement('Button') creates a clickable button object (createElement('Button')) referenced by the variable name .
2. `clickMeButton.id` = 'myButton' sets the button's id to be myButton.
3. clickMeButton.innerHTML = 'Click Me' sets the button's inner HTML (i.e., the label we normally see between the HTML button tags) to say "Click Me".
4. clickMeButton.style.background = '#4FFF8F' sets the button's background color to green. To style multiple attributes of our button using a style class, we would write clickMeButton.className = 'myStyleClassName' instead.
5. document.body.appendChild(clickMeButton) appends  to the body of the document as a child.
Let's say we want to modify the label on an HTML button element with the id myButton. We simply use the getElementById method and pass the desired element's id as an argument:

### Styling Buttons with Css
First, we want to define the style constraints for our button. We can do this in either of the two ways below.

1. Using an ID Selector
For instances where we want to apply a style to a single element within an HTML page, we use a CSS id selector using the syntax #identifier (where  is the id of the element to style within the page). We then follow it with a pair of curly braces that contain the desired style constraints for all elements within the container that has that identifier. For example:
```Css
#myButtonId {
    /* Set the background color to a shade of green */
    background: #4FFF8F;
    /* Center-align the text */
    text-align: center;
    /* Set the cursor to be a pointer */
    cursor: pointer;
}
```

2. Using a Class Selector
For instances where we want to apply the same styling to multiple elements, we define a CSS class using the syntax .className (where  is the name of our class). We then follow it with a pair of curly braces that contain the desired style constraints for all elements of that class. For example:
```css
.myStyleClass {
    /* Set the background color to a shade of green */
    background: #4FFF8F;
    /* Center-align the text */
    text-align: center;
    /* Set the cursor to be a pointer */
    cursor: pointer;
}
```

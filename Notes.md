
# What happens when you connect to a url on your laptop browser?

The answer can be broken down into 2 domains:dw
1. **Application level**
2. **Network level**

Application level :
A request to the server representing the ip/domain space the
name represents is sent. In the case of Spring application, the first
file that gets hit is web.xml. web.xml defines where the dispatcher servlet
 which redirects again to a handler. This handler is tasked with calling
 the right method by checking controller annotation corresponding to the
 url path. Controller forwards the request to services (model) which performs
 operation on database using DAO and returns control to controller which
defines which page gets loaded and with what information (cookies, session key,
 etc). This page is returned to view controller which returns a JSP/HTML page
 to the client populated with correct values.

Network level:
The request is first sent to ISP which knows a DNS server that
can map the web address to IP address of server machine. A port
 is kept open and listening to request sent by server, on the
client machine. The server returns with a page with a proper
 response code and the browser renders it.

---


# Implement sum(3)(4)(5)=12 with javascript
```javascript
function Sum(arg0) {
  function Inner1(arg1) {
    function Inner2(arg2) {
      return arg0 + arg1 + arg2;
    }
    return Inner2;
  }
  return Inner1;
}
console.log(Sum(3)(4)(5));
```
---

# Write code on the whiteboard that could take user input and determine if it is a palindrome.

```javascript
function is_palindrome(input) {
   return (input === input.split('').reverse().join('');
}
```

---

# Take two arrays and compare them to find duplicates. Only list each duplicate once.

```javascript
  var Array1 = ['a', 'b', 'c', 'd', 'e', 'f', 'c'];
  var Array2 = ['c', 'x', 'y', 'f', 'c'];
  let hash = {};
  let result = [];

  // loop over the largest
  for (let i = 0; i < Array1.length; i++) {
    if (!hash[Array1[i]]) {
        hash[Array1[i]] = 1;
    }
  }

  for (let i = 0; i < Array2.length; i++) {
  if (hash[Array2[i]]) {
    result.push(Array2[i]);
    delete hash[Array2[i]];
  }
  }
```
---

# What is the importance of CSS selectors? Where do you use them?

CSS selectors are the part of a CSS rule set that actually selects
the content you want to style and have a rule set based on
specificity that you can calculate where:

**Memorize how to measure specificity.** �Start at 0, add 1000 for style attribute,
add 100 for each ID, add 10 for each attribute, class or pseudo-class,
add 1 for each element name or pseudo-element.

---

# Make an accordion where when clicked, text expands from it and
# when another item is clicked, the first one collapses and the
# second one expands.

HTML
---
```html
<body onload="init()">
<div class="accordionItem">
  <h2>About accordions</h2>
  <div>
    <p>JavaScript accordions let you squeeze a lot of content into a small space in a Web page.</p>
    <p>This simple accordion degrades gracefully in browsers that don't support JavaScript or CSS.</p>
  </div>
</div>
</body>
```

CSS
---
```css
body { font-size: 80%; font-family: 'Lucida Grande', Verdana, Arial, Sans-Serif; }
.accordionItem h2 { margin: 0; font-size: 1.1em; padding: 0.4em; color: #fff; background-color: #944; border-bottom: 1px solid #66d; }
.accordionItem h2:hover { cursor: pointer; }
.accordionItem div { margin: 0; padding: 1em 0.4em; background-color: #eef; border-bottom: 1px solid #66d; }
.accordionItem.hide h2 { color: #000; background-color: #88f; }
.accordionItem.hide div { display: none; }
```

JS
---
```javascript
var accordionItems = new Array();
function init() {

      // Grab the accordion items from the page
      var divs = document.getElementsByTagName( 'div' );
      for ( var i = 0; i < divs.length; i++ ) {
        if ( divs[i].className == 'accordionItem' ) accordionItems.push( divs[i] );
      }

      // Assign onclick events to the accordion item headings
      for ( var i = 0; i < accordionItems.length; i++ ) {
        var h2 = getFirstChildWithTagName( accordionItems[i], 'H2' );
        h2.onclick = toggleItem;
      }

      // Hide all accordion item bodies except the first
      for ( var i = 1; i < accordionItems.length; i++ ) {
        accordionItems[i].className = 'accordionItem hide';
      }
    }

function toggleItem() {
      var itemClass = this.parentNode.className;

      // Hide all items
      for ( var i = 0; i < accordionItems.length; i++ ) {
        accordionItems[i].className = 'accordionItem hide';
      }

      // Show this item if it was previously hidden
      if ( itemClass == 'accordionItem hide' ) {
        this.parentNode.className = 'accordionItem';

      }
    }

function getFirstChildWithTagName( element, tagName ) {
      for ( var i = 0; i < element.childNodes.length; i++ ) {
        if ( element.childNodes[i].nodeName == tagName ) return element.childNodes[i];
      }
    }
```
---

# Write a function to flatten an array in Javascript
```javascript
function flatten(array) {
   array.reduce(function(flat, toFlatten) { return flat.concat(Array.isArray(toFlatten) ? flatten(toFlatten) : toFlatten); }, []); }
```
---

# Vertically and horizontally center an element on the screen using css.

```css
#center{width: 100px; height: 50px; position: fixed; top: 0; left: 0; right: 0; bottom: 0; margin: auto;}
```
## With Flexbox:

**Flexbox. Flexbox is the answer.** If you need older browser support
you can make it happen with faking-table layout using CSS 'display: table', you can then use the 'vertical-align' property.
```css
.centered-content {
  display: flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
}

.centered-content .centered-item {
  max-width: 50%; /* Really only here to not max-out the horizontal centering effect. */
  box-sizing: border-box;
}
```
---

# Write a tool that will display a todo list that is pulled from a database.
# When an item is checked off the list, have some action happen to indicate that item is done.

## HTML
---
<!--
   The following is a common layout you would see in an email client.

   When a user clicks a checkbox, holds Shift, and then clicks another
checkbox a few rows down, all the checkboxes in between those two checkboxes
should be checked.

  -->
  ```html
  <div class="inbox">
    <div class="item">
      <input type="checkbox">
      <p>This is an inbox layout.</p>
    </div>
    <div class="item">
      <input type="checkbox">
      <p>Check one item</p>
    </div>
    <div class="item">
      <input type="checkbox">
      <p>Hold down your Shift key</p>
    </div>
    <div class="item">
      <input type="checkbox">
      <p>Check a lower item</p>
    </div>
    <div class="item">
      <input type="checkbox">
      <p>Everything inbetween should also be set to checked</p>
    </div>
  </div>
  ```

CSS
---
```css
    html {
      font-family: sans-serif;
      background:#ffc600;
    }

    .inbox {
      max-width:400px;
      margin:50px auto;
      background:white;
      border-radius:5px;
      box-shadow:10px 10px 0 rgba(0,0,0,0.1);
    }

    .item {
      display:flex;
      align-items:center;
      border-bottom: 1px solid #F1F1F1;
    }

    .item:last-child {
      border-bottom:0;
    }


    input:checked + p {
      background:#F9F9F9;
      text-decoration: line-through;
    }

    input[type="checkbox"] {
      margin:20px;
    }

    p {
      margin:0;
      padding:20px;
      transition:background 0.2s;
      flex:1;
      font-family:'helvetica neue';
      font-size: 20px;
      font-weight: 200;
      border-left: 1px solid #D1E2FF;
    }
```

# JS(es6)
---
```javascript
fetch(url)
.then(renderHTML)
.catch(function catchErr() {
   // do error stuff
   console.Error('error occured');
});

function renderHTML(data) {
   let htmlString = "";
   let content = document.querySelectorAll('.inbox input[type="checkbox"]');

   for(i = 0; i < data.length; i++) {
      htmlString += "<p>" + data[i].todo + "</p>"
   }

   content.innerHTML = htmlString;
}

const checkboxes = document.querySelectorAll('.inbox input[type="checkbox"]');

let lastChecked;

function handleCheck(e) {
  // Check if they had the shift key down
  // AND check that they are checking it
  let inBetween = false;
  if (e.shiftKey && this.checked) {
    // loop over every single checkbox
    checkboxes.forEach(checkbox => {
      console.log(checkbox);
      if (checkbox === this || checkbox === lastChecked) {
        inBetween = !inBetween;
        console.log('STarting to check them inbetween!');
      }

      if (inBetween) {
        checkbox.checked = true;
      }
    });
  }

  lastChecked = this;
}

checkboxes.forEach(checkbox => checkbox.addEventListener('click', handleCheck));
```
---

# Understanding Accessibility Has a Seat at the Table

There are significant benefits for what you do for accessibility. 
And we have a resource that talks about that. 
It’s “Developing a Business Case for Your Organization“, and it outlines
 and describes the technical factors, the financial factors, the 
social factors, and the legal and policy factors in the business
 case for accessibility. It talks about looking at the return on investment.

If you really understand the business case and those additional 
benefits then web accessibility is a comparatively easy sell within most organizations.

Another aspect of that is the issue with getting accessibility 
integrated early on in the development process. When accessibility
 comes in at the end then it does cost more and it is seen as more 
of a burden – it really is more of a burden. But if instead
 accessibility can be integrated from the very beginning of a
 project, then it can have very little negative impact in terms
 of cost or time. And then you can just realise all the positive 
impacts in terms of better design and better products.



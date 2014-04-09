# Coding standards

## In general

### Indentation
Indentation is everything. If code is not indented properly, it is like trying to make sense of a book without punctuation. Indent with 4 spaces. This can be set in Sublime Text by opening settings (cmd+,) and adding the following lines:

```
"tab_size": 4,
"translate_tabs_to_spaces": true
```

Proper indentation should be practised religiously.

<!-- ### Use single or double quotes consistently
It does not matter whether single or double quotes are used, as long as they are used consistently. Double quotes has some advantages in PHP, so they should probably be preferred to single quotes. -->

## HTML
Not much to say here yet. Remember indentation. Nothing is worse than

```html
            <!-- 
                ...
                All kinds of nested divs and their content
                ...
            -->

        </div>    
</div>
    </div>
    </div>
</div>
```

Also, if your HTML contains lots of nested elements, it can be really helpful for others if a comment is added about what element is closed.
```
            </div> 
        </div>
    </div>
</div> <!-- closing .main -->
```

## CSS

### Only use classes
Never use ids as css-selectors. By using only classes it is so much easier to calculate specificity. Ids should be used for JavaScript only.

### Never use the same classes for JavaScript and CSS
When using frameworks such as jQuery, where classes are sometimes used to fetch a collection of elements, make sure that the same class isn't used as both a CSS and JavaScript selector. Instead, if an element needs to be used by some JavaScript code, give it an additional class that expresses that clearly:

```html
<div class="container js-container">
    ...
</div>
```

In this way there is no doubt that the container-element is needed in your JS somewhere.

### Spacing and indentation
There should be exactly one space between a property and a value:

```css
/* Wrong */
h1 {
    color:#abcdef;
}

/* Right */
h1 {
    color: #abcdef;
}
```

Notice the 4 space indentation? Indentation is good.

### Declaration order
This is a tough one and it really comes down to choice. For a long time, I alphabetized my declarations by property name:

```css
.container {
    background: #eaeaea;
    border: 2px solid #000;
    border-radius: 5px;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    color: #333;
    height: 200px;
    left: 40px;
    margin: 0 0 20px;
    padding: 20px;
    position: absolute;
    text-align: center;
    top: 30px;
    width: 400px;
}
```

Nice - you are never in doubt where to place a declaration. And a short time after you start to adhere to this rule, it's amazing how little time you spend looking for a specific declaration in a selector with many rules.

However, I was frustrated that this rule prevents the grouping of similar rules like width and height and position, left, right, top, bottom, etc.: 

```css
.container {
    width: 400px;
    height: 200px;

    position: absolute;
    left: 40px;
    top: 30px;
    
    background: #eaeaea;
    border: 2px solid #000;
    border-radius: 5px;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    color: #333;
    margin: 0 0 20px;
    padding: 20px;
    text-align: center;
}
```

What I do nowadays is combine the two above styles. I seperate all groups with a single line. The extra space between groups increases the readability, and as long as the css is minified, it doesn't have any impact on file size. Win.

In the example below, there are "natural" and "unnatural" groups. A natural group is a group that naturally occur because the declarations touch the same area. In the below example the only natural group is the border-group. Another natural group example could be something like font-size, font-family, font-weight. They all have to do with the font. The unnatural groups height/width, margin/padding and position/left/top. Even though the property names are matching in the same way as with natural groups, it feels right to group them. Width and height tells something about the dimensions of the selector, margin and padding tells about the box-model (arguably, box-sizing could belong in this group), and position, top and left tells something about the position.

```css
.container {
    background: #eaeaea;

    border: 2px solid #000;
    border-radius: 5px;
    
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;

    color: #333;

    /* None of the rules are more important than the other so sort alphabetically after h */
    height: 200px;
    width: 400px;
    
    /* None of the rules are more important than the other so sort alphabetically after m */
    margin: 0 0 20px;
    padding: 20px;

    /* left and top doesn't make sense without position, so sort alphabetically after p */
    position: absolute;
    left: 40px;
    top: 30px;
    
    text-align: center;
}
```
In the example, I have tried to explain the logic behind my sorting of groups.

## JavaScript

### Put everything in seperate files
As far as possible, all JavaScript should go in seperate files and be included from markup, rather than be nested in between markup.

### Avoid global namespace polution
In order to avoid potential naming collisions, it should be avoided to define variables and functions in the global namespace. Define an object that has a unique name in relation to your app and populate that with your variables and functions.

```javascript
// Bad example
var name = "John Doe";

function sayHello() {
    alert("Hello!");
}

// Better
var myAwesomeApp = {};

myAwesomeApp.name = "John Doe";

myAwesomeApp.sayHello = function () {
    alert("Hello!");
}
```
In this way, only a single global variable is introduced. And by giving it a unique name that has to do with your app, the risk of naming collisions are reduced greatly.


- Declare all variables at top of function

## PHP

### Quotes
In the PHP community it is generally said that it doesn't matter whether single or double quotes are used, as long as they are used consistently. However, there are some advantages to double quotes over single quotes, so double quotes should be preferred.

### Laravel
#### Extract similar view content to sub views



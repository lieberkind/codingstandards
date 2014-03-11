# Coding standards

## In general
Indentation is everything. If code is not indented properly, it is like trying to make sense of a book without punctuation. Indent with 4 spaces. This can be set in Sublime Text by opening settings (cmd+,) and adding the following lines:

```
"tab_size": 4,
"translate_tabs_to_spaces": true
```

Proper indentation should be practised religiously.

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


## CSS

### Only use classes
Never use ids as css-selectors. By using only classes it is so much easier to calculate specificity. Ids should be used for JavaScript only.

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


## JavaScript
- Everything in seperate files
- Avoid global namespace polution
- Declare all variables at top of function

## PHP
### Laravel
#### Extract similar view content to sub views

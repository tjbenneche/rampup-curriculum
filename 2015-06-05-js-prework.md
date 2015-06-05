# Intro to JavaScript: Prework

The first couple weeks of class will cover JavaScript basics (syntax, variables, loops, functions) and then we will dive into using JavaScript on the web. Since we'll cover the basics in class, you don't need to worry about practicing any of that just yet.

Instead, it would be helpful for you to review (or take a first look at!) HTML & CSS. We won't be writing _too much_ of either in this class, but they are the building blocks of the web that JavaScript calls home. Most of our interaction with HTML & CSS will be through **selectors**, so be sure to put most of your focus there.

## Exercises

Please take some time to go through the exercises in basic HTML & CSS [here](http://www.codecademy.com/tracks/web).

Here is some reading on how selectors play a part in the relationship between HTML, CSS, and JavaScript:

## Reading

Once you've done enough of the exercises to feel somewhat comfortable, give this material a quick read.
 
### Selectors
 
There are four distinct ways to select an HTML element in CSS: by inline styles, tag name, class, or ID (and various combinations of these). We use these "selectors" to tell the browser to which element the following style rules should be applied.
 
Let's take a closer look at each of these.
 
**Inline Styles**
 
An inline style is where you declare a style rule within the tag of the HTML element you are trying to style, like so:
 
    <p style="color:red;">This paragraph is red.</p>
    
It would be highly inadvisable to write HTML with inline styles, but they are useful in that they override _every_ other selector. This is why any styles applied via JavaScript will show up inline.
 
**Tag Name**
 
Selecting an element by its tag name will apply the following style rules to any element sharing that same tag. So, if in your CSS you have something like this:
 
    p{
        color:red;
     }
 
all "p" elements in your HTML document will be colored red. This method only makes sense if you are declaring a style you intend to be universal — perhaps you want to remove the default margin on all paragraphs, or make all headings the same font size. Otherwise, it is more effective to add some specifity to your selectors by including a class or ID.
 
**Class**
 
A class selector can be used to apply a set of style rules to multiple elements on the page. Let's say you had a long list of paragraph tags and wanted to alternate the background color of each, you could apply the class "odd" to the first and every other tag following, and likewise give all even tags the
class "even".
 
    <p class="odd">One</p>
    <p class="even">Two</p>
    <p class="odd">Three</p>
    <p class="even">Four</p>
 
Then in your CSS, rather than selecting the elements by their tag name, p, you can use their respective class selectors:
 
    .odd{
        background-color:blue;
    }
    
    .even{
        background-color:red;
    }
    
You'll notice that the class selectors in CSS have a dot before the name — this is the way of telling the browser that this word represents a class. A similar convention is used to denote when an ID is being used as well.
 
**ID**
 
An ID selector is used to apply a set of style rules to _one_ element on the page. As a rule, IDs should be used sparingly as they hold a much greater weight than classes, and as such are difficult to override. An ID should be applied to no more than one element per page, as having multiple instances of the same ID could cause problems in JavaScript and semantically an ID should be unique.
 
One of the more common usecases for an ID is as an anchor tag. If you've encountered a website where clicking on a navigation link scrolls you down to a different section of the page rather than directing you to a totally new page, the odds are this is being done using ID anchors. Anchor setups generally look something like this:
 
    <a href="#section2">Section 2</a>
    
    ...
    
    <div id="section2">
    ...
    </div>
 
The "href" attribute specifies the URL or path to which the link should take you. When an href value starts with a "#", the hyperlink will search the current document for an ID matching whatever text comes after. If no text is provided and we just have
 
    <a href="#">Link</a>
 
the link will take you nowhere. This is often used when a link's destination is the page you're currently on (i.e. a "Home" link on the homepage).
 
Another use for IDs is when there is truly something unique on the page that requires styling. Let's say you were building a blog, and wanted to have a different style treatment for the most recent post. All posts will share similar styles, but the most recent one will have a larger font size. Your HTML might look something like this:
 
    <article class="blog-post" id="most-recent">
    ...
    </article>
    
    <article class="blog-post">
    ...
    </article>
    
    <article class="blog-post">
    ...
    </article>
 
You'll notice each article tag is given a class of "blog-post", but only the first has the ID of "most-recent". This setup will allow us to write style rules shared by all posts and rules that only get applied to the most recent one, like so:
 
    .blog-post{
        color:blue;
        margin:20px 0;
        font-size:16px;
    }
    
    #most-recent{
        font-size:24px;
    }
    
In this setup, each article will have a font color of blue, some margin on the top and bottom for spacing, and a font size of 16px. The article with id="most-recent", however, will have its font size increased to 24px because IDs are weighted more heavily than classes.
 
 
### Specifity
 
A style rule's precendence is measured in specificity. Each of the selector types mentioned above has a _specifity value_.
 
An inline style, given that it is placed directly within the HTML tag, has the highest specifity value of all the selector types. When a style rule is changed via JavaScript, it is done with the inline style method, and as such will override any previously declared styles. The next highest value is an ID, followed by a class, and finally a tag name. Keep in mind that to make a style rule more specific, you can (and often should) use combinations of these selectors.
 
How do we calculate specifity?
 
An inline style has a specificity value of **1000**
An ID selector has a specificity value of **100**
A class selector has a specificity value of **10**
A tag name selector has a specificity value of **1**
 
Let's try setting some style rules for this paragraph:
 
    <html>
        <head>
        </head>
        
        <body>
            <div class="container">
                <p id="special">This is the paragraph to be styled</p>
            </div>
        </body>
    </html>
 
As we've done in the past, we could simply use the "p" tag name:
 
    p{
        color:red;
    }
    
This style rule has a specifity value of 1, since all we are using is the tag name. Let's make this a little more specific to override that style:
 
    div p{
        color:blue;
    }
 
By nesting the p selector within its parent div, we've increased the specifity value to 2, and the color will now show as blue. If we were to take this a step further and nest "div p" within all the remaining parent elements, "html body div p", the best we could do is a specificity value of 4. By using just one class selector, we can override that:
 
    .container p{
        color:green;
    }
    
Rather than selecting any p within a div, we are now specifiying that these rules should only apply to p tags within an element with the class "container", resulting in a specificity value of 11. Let's try using an ID:
 
    #special{
        color:yellow;
    }
    
By using an ID selector, we have increased our specifity value to 100, and the color of this paragraph will most certainly be yellow.
 
It is also important to note that because the browser interprets your CSS document from top to bottom, if two style rules have the same specificty value, whichever one comes later in the document will have precedence. So, if we have:
 
    div p{
        color: red;
    }
    
    div p{
        color: blue;
    }
    
the color will be blue.
 
Because there are so many different ways to select an element, the decision making process may seem a bit overwhelming at first. But, in reality, what matters is that you choose a system that makes sense to you. The only "rules" you want to keep in mind are these:
 
1. DRY - don't repeat yourself. Make an effort to minimize the lines of code you are writing. Use class selectors to write styles that can be shared across multiple elements.
2. KISS - keep it simple, stupid. Chris Coyer has a great application of this philosophy to CSS selectors: only be as specific _as it makes sense to be_. Don't write excessively long chains like "html body div.container .heading-box h1.primary" — instead, make it specific enough to work, and if you have to add more specificity later so be it.
3. Use IDs sparingly, and avoid inline styles altogether. Each of these has a tendency to break the "cascading" nature of CSS (cascading style sheets). When reading through code, it will be apparent which rules are more specific by the length of the selector chain preceding them. IDs and inline styles muddle these snap judgements that prove to be big time savers in debugging.


[Selectors Exercises](http://www.codecademy.com/courses/web-beginner-en-WF0CF/0/1?curriculum_id=50579fb998b470000202dc8b)

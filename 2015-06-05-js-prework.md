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

## More Exercises

Here are some extra exercises you can take a look at on **selectors**

[Selectors Exercises](http://www.codecademy.com/courses/web-beginner-en-WF0CF/0/1?curriculum_id=50579fb998b470000202dc8b)

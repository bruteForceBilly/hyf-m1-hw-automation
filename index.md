# HTML & CSS Module 1 Homework Review Templates 
A repository of templates explaining some common mistakes and anti-patterns commonly encountered on Trello while reviewing homework from students in Module 1, week 1 to week 3.

##### TO DO
 - [x] 1) Don't Repeat Yourself  (DRY) 
 - [x] 2) Magical Numbers
 - [x] 3) Non-descriptive css classnames
 - [x]  4) Prefer REM over PX
 - [x] 5) Don't use id selector for CSS
 - [x] 6) Don't use floats
 - [x] 7) Not responsive
 - [ ] 8) Better usage of CSS Grid
 - [x] 9) Wrong usage of HTML tags
 - [ ] 10) Use semantic HTML


## 1) Don't Repeat Yourself  (DRY)
When there is repeated code in different places. In example: when several CSS classes seek out to achieve the same thing, or accruing one css class to several html elements instead of letting them inherit from a one parent element and/or a pseudo-selector.

### Explanation 
Try to keep your code DRY. DRY is an acronym that stands for Don't Repeat Yourself, a principle that can aid you in writing more concise and clear code. The idea of DRY is that each objective of your code should only be declared once, and not be found in several places. The opposite of DRY code is WET, an acronym for "Write Every time". The opposite of DRY code is WET, an acronym for "Write Every time".  

#### Example
Here is an example of WET CSS code:

	h1 {
	    font-family:  "Helvetica", sans-serif;
	    font-size: 32px;
    }
    
    h2 {
	    font-family: "Helvetica", sans-serif;
	    font-size: 24px;
    }
    
    h3 {
	    font-family: "Helvetica", sans-serif;
	    font-size: 16px;
    }
    
   
You could consolidate your styles to make your code more DRY like this:

    h1, h2, h3, {
		font-family: "Helvetica", sans-serif;
	}
	
	h1 {
		font-size: 32px;
	} 
	
	h2 {
	    font-size: 24px;
    }
    
    h3 {
	    font-size: 16px;
    }

See how you only need to update your code in one place now if you want to change the font? The win of writing your code more DRY is that its easier to understand, maintain and develop. 

#### Resources 
You can learn more about DRY here:
https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
https://www.youtube.com/watch?v=IGH4-ZhfVDk&t=90s


## 2) Magical Numbers
A css unit value amount that is not in itself meaningful or doesn't make sense without an explanation, therefore obscuring the students original intent with the css rule.

### Explanation
Avoid using "Magical Numbers" in your css unit values. A magical number is any number that alone is not meaningful to another developer without an explanation. Instead try to use meaningful numbers. A meaningful number is a number that by itself can give another developer an idea of your intent of choosing that number. 

#### Example
An example of a meaningful number is: 

`width: 25%;` 

It gives another developer the idea that a fourth of something is being used. 

An example of magical number would be:

`width: 48.5%`

Here the need of decimals is not clear by itself. To make the number more meaningful, you can try to identify where the need for the decimals comes from. 

Let's say we realize that we want our width to be half the width of something, minus our font size to give some space. We could then preferable use the calc() function to achieve a more meaningful number:

`width: calc(50% - 1rem);`

Here is an example where you are using magical numbers in your css... 

To make your numbers more meaningful could try... 

 
#### Resources
You can learn more about magical numbers here:
https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants
https://www.codereadability.com/magic-numbers-in-css/

You can learn more about the css calc function here: 
https://developer.mozilla.org/en-US/docs/Web/CSS/calc()


## 3) Non-descriptive css classnames
When there is css class names that are not descriptive or meaningful to another developer. The names are missing context, using abbreviations or are named after a number.

### Explanation
Try to be more descriptive in your class names. For example the css classes ".first-section", ".second-section" or ".div" does not give another developer any information on what part of the page the css is intended to style, or what is the purpose of the style.

 Another thing to look out for here is the use of abbreviation in class names, i.e: instead of ."cntct-frm" use ".contact-form". Sometimes you will encounter the use of abbreviation in class names from css frameworks like Bootstrap, Materialize or Tailwind. These frameworks are very well documented and the css class names within them are standardized to its users who know these class names at heart. This cannot be expected when you are writing your own css and thus prefer using full descriptive names that signalises the context and purpose of the css. 

#### Example
Here's an example of non-descriptive css:
	
	.section-first {
	  background-color: yellow;
	  height: 10rem;
	}

	.headline {
		color: black;
		font-size: 3rem;
	}

	.section-second {
	  background-color: white;
	  padding: 0 5rem;
	}

    .section-last {
		background-color: black;
		width: 100%;
	}

	.section-last-links {
		background-color: black;
		width: 100%;
	}

Note how the class names with section in them does not give us any context for the style or its purpose. To make it more descriptive, give your names context: 

    .header {
	  background-color: yellow;
	  height: 10rem;
	}

	.header__titel {
		color: black;
		font-size: 3rem;
	}

	.main {
	  background-color: white;
	  padding: 0 5rem;
	}

    .footer {
		background-color: black;
		width: 100%;
	}

	.footer__link {
		background-color: black;
		width: 100%;
	}

Note how by using the name of the part of the page, the names are given a context. This way you can group style together by using dash or underscore. In the example above I have used underscore, a praxis from the BEM naming convention. Given names context makes it easier to group styles together and makes your CSS easier to understand for other developers.

#### Resources
You can read more about BEM naming convention here: 
http://getbem.com/naming/

## 4) Prefer REM over PX 
When there is use of PX, but REM would instead be greatly beneficial or when there is a mix of using REM and PX unit values. 

### Explanation
Try to avoid using PX in some places and REM in some other places . Try to stick to one type of unit values, or at least be consistent in your use of them. It will make your css easier to maintain and understand for other developers. Prefer using REM values when possible as it will make it easier for you to make your design responsive.

#### Example
Let's say we have a design for mobile and desktop

    @media all and (max-width: 375px) {
		body {
			font-size: 12px;
		}
		header {
			height: 60px;
		}
		h1 {
			font-size: 36px;
		}
    }
    
	 @media all and (min-width: 376px) {
	    body {
			font-size: 16px;
		}
		header {
			height: 80px;
		}
		h1 {
			font-size: 48px;
		}
    }

 You could preferably make this CSS easier to maintain and develop by adopting REM:

	.header {
	  height: 5rem;
	}
	
	h1 {
	  font-size: 3rem;
	}

    @media all and (max-width: 375px) {
		body {
		  font-size: 12px;
		}
    }
    
	 @media all and (min-width: 376px) {
	    body {
		  font-size: 16px;
		}
    }


#### Resources
You can learn more about REM values here:
https://www.24a11y.com/2019/pixels-vs-relative-units-in-css-why-its-still-a-big-deal/

Practise REM in CodePen:
https://codepen.io/bruteforcebilly/pen/eYzQjMV


## 5) Don't use id selector for CSS
When there is use of an id selector without the exercise calling for it specifically. 

### Explanation
A rule of thumb is to never use the ID selector in your CSS unless you are absolutely sure an element will not occur more than once on web page or in your app. Example of such elements could be a wrapper element for a cookie bar, or a modal pop up prompting user for their age. These examples can demand a tight coupling between the HTML and CSS. 

But besides these niche scenarios, you almost always will want to have a loose coupling HTML and CSS for the sake of making your CSS more modular and reusable. This is achieved by using css classes and a good naming convention. 

Another reason is to keep your specificity low. Different types of features in CSS gives your styles more or less priority by assigning them specificity. 

#### Example
For example, if you use `!important` in one of your styles, that style will always take effect, regardless of how your css normally would inherit styles. This can make your CSS more difficult to debug. Id  selectors have a higher specificity than Class, and it is therefore considered best practice to prefer class over id selectors .

#### Resources
https://css-tricks.com/strategies-keeping-css-specificity-low/
https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity

## 6) Don't use floats
When use floats in layout without the exercise specifically calling for it.

### Explanation
Avoid using floats do to your layout. Knowing about floats it important for the sake of being able to maintain older websites, but there is no need to use floats today when making a new website. Prefer using flexbox instead.

#### Resources
https://css-tricks.com/snippets/css/a-guide-to-flexbox/


## 7) Not responsive
When the project brakes upon resizing the window or trying different screen size. 

### Explanation
Your layout breaks when resizing the window or when trying to different mobile screen resolutions in devtools. It's important to ensure that your design scales gracefully for different window sizes. This can be achieved by constantly checking the changes you are making in Device Mode in DevTools (prefer using the devtools from Chrome or Firefox). Also make sure that your have set your media queries correctly and a tip is to use REM values to make your design easier to scale up and down for different screen sizes. And make sure you have set your media queries as you intended

#### Resources
Device Mode in Chrome DevTools
https://www.youtube.com/watch?v=M482RhQ8i1Q
https://developers.google.com/web/tools/chrome-devtools/device-mode#viewport

Responsive Design Mode in Firefox
https://developer.mozilla.org/en-US/docs/Tools/Responsive_Design_Mode

Using Media Queries
https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries

CodePen Media Query example:
https://codepen.io/saidac/pen/vYKpMbX?editors=1100

## 8) Better usage of CSS Grid
### Template
#### Example
#### Resources
The Joy of CSS Grid - Build 3 Beautifully Simple Responsive Layouts
https://www.youtube.com/watch?v=705XCEruZFs&t=248s

## 9) Wrong usage of HTML tags
When incorrect basic HTML markup

### Explanation
It can take a while before one gets use to how the skeleton of an HTML document should look like. A tip is to read a lot of other HTML documents of github (here is one good example: https://github.com/mrmrs/html/blob/master/index.html)

#### Examples

-- Make sure that your HTML Document has a `<title>` tag

-- When using list prefer using the unordered list element `<ul>`  and make sure it wraps you  `<li>` list elements as children.
 
-- Make sure you sure sticking to using one way of assigning your CSS to your HTML document. For example if your are importing your css via a link tag in your HTML head like so:

     <head>
    	 <link rel="stylesheet" href="style.css"> 
     </head>
     
 Do not then also use a `<style>` tag to add additional css to your html in your document.
       
-- Make sure you do not have multiple `<h1>` tags in your html. Search engines rely on your heading elements to index your page and show it in search results. Using multiple `<h1>` tags will make it more difficult for the search engine to determine what the page is about. Therefore its is advised to only use one `<h1>` tag per page.

#### Resources
https://www.hobo-web.co.uk/headers/

## 10) Use semantic HTML
When the students have not to used semantic html tags in their markup.

### Explanation
I've noticed that you could improve your use of semantic html tags. Semantic html tags are important as they make your code easier to read and maintain for other developers, as well as easier to index for search engines, giving you better search results!

#### Example
Instead of writing a header with div's like so:

    <div class="container" id="header">
        <div class="header header-main">Super duper best blog ever</div>
        <div class="site-navigation">
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/archive">Archive</a>
        </div>
    </div>

Prefer using semantic html:

    <header>
        <h1>Super duper best blog ever</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/archive">Archive</a>
        </nav>
    </header>

Notice how the second example is easier to read and probably easier to maintain? 

#### Resources
The examples given has been qouted from this article: 
https://dev.to/kenbellows/stop-using-so-many-divs-an-intro-to-semantic-html-3i9i

https://www.freecodecamp.org/news/semantic-html5-elements/

## 11)  Invalid HTML

### Template
#### Example
#### Resources

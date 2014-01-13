# Markdown CV
This is my fork of https://github.com/bitlyfied/markdown-cv. So at first thanks to @bitlyfied for the great work!

I'd noticed some issues with wkhtmltopdf and css so I changed this to phantomjs and Schrimp. As well as some css styling.

## Install

### Install GEM dependencies:

	bundle install

### Install phantomjs
I'm using [Shrimp](https://github.com/adeven/shrimp) to render the pdf from the html file. Shrimp is based on phantomjs. So use `npm install phantomjs` or `brew install phantomjs`. You don't know `brew` or `npm`? 

__Mac users__ please take a look at http://brew.sh/. To install brew to this:

	ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"

__All others__ please follow the instructions on http://nodejs.org/

## Build
To generate PDF you just need to use rake:

	rake build

Or, if you want to build and display the PDF in a single command, just use:

	rake

## Use

Put your CVs in the src folder. All files *.md are built by the rake task.
You can use the one provided as an example.

The build task is a three step process:
- convert Mardown to HTML
- render content inside a styled HTML template
- convert the HTML file to PDF using wkhtmltopdf

To tweak the style of the CV you can change the _template/base.css_ file with your own font and style.


## Enriched Markdown
Markdown CV is using Github-flavoured Markdown, and on top of that it's adding an extra feature.
You can mark blocks of content with the following syntax:

	[myblock]
	
	** Some content
	
	[/myblock]
	
The build process will replace **[myblock]** with **&lt;div class=&quot;myblock&quot;&gt;**

You can use this functionality to create asides and content formatted in a special way.

## Page breaks
Markdown has no knowledge of pages or page breaks. But you can use **page-break-** CSS to control them.

Use `[pagebreak]` to manually do a new page.
	
	my text
	
	[pagebreak]

	my text

Normally the breaks should be fine but I had noticed that sometimes phantomjs does a bad job on this. I'm trying to figure out what's going wrong there but currently if you're ran into this kind of problems try using your chrome print to pdf manually by opening the `build/your-name.html` file.

# Examples
Here are some examples of using special things of my version

## Your Picture aside the introduction

	Profile
	-------

	![picture](../img/john.png)
	- **Name** John Doe
	...

## Professional experience
The given CSS adds a nice coloured bottom border to the fourth heading. So you you can use this for your job title like this:

	Professional Experience
	-----------------------

	### My current awesome company _since Aug. 2012_
	#### Master of Awesomeness
	_some, of, my, main, topics_
	What I was doing here Lorem ipsum Consectetur in incididunt qui ut elit ea deserunt in aliquip. Lorem ipsum Adipisicing qui labore ea ad Duis est cupidatat esse quis do voluptate nulla cupidatat veniam reprehenderit enim consequat labore deserunt.

	- list of projects 
	- or
	- other things i would like to 
	- highlight here

	### My last awesome company _May 2004 - Aug. 2012_
	#### Principle of Awesomeness
	_some, of, my, main, topics_
	What I was doing here Lorem ipsum Consectetur in incididunt qui ut elit ea deserunt in aliquip. Lorem ipsum Adipisicing qui labore ea ad Duis est cupidatat esse quis do voluptate nulla cupidatat veniam reprehenderit enim consequat labore deserunt.

## Block Quotes
If you want to cite a reference just do a block quote like this:

	> Block quote, maybe a reference quote. Lorem ipsum Consequat labore adipisicing Duis Excepteur id Excepteur voluptate aute proident laborum sit voluptate eiusmod in officia ad magna consectetur veniam est est Duis labore ullamco reprehenderit in cillum culpa mollit eiusmod labore Ut Ut sed. _(Big Boss - CEO Himself)_

## More examples? Just look into the Markdown doc
- http://daringfireball.net/projects/markdown/syntax
- https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
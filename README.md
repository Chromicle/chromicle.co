# chromicle.github.io

My personal Website :flashlight: + blog :cherries:

This site was built using [Jekyll](https://jekyllrb.com/), a static site generator that allows you to create layouts for pages, menus, and the like using HTML, CSS, Javascript, and [Liquid](https://shopify.github.io/liquid/), then use those layouts to convert plain-text files into beautifully formatted web pages. The goal of this readme is to explain how to make some basic modifications to the site (for example, adding projects or team members). For a more comprehensive guide to using Jekyll, try the official documentation (linked above).

The site uses a modified version of the Hydejack Jekyll theme. Scroll down for the original theme documentation, which explains how to create new tags, change the background image and color on pages, etc.

# Modifying the site

To make and test changes to the site, you'll want to host and view it locally first, instead of directly modifying the live/online version. Using the command prompt, navigate to the directory where the site stored, then enter the following command:

```
bundle exec jekyll serve --baseurl ''
```

Then navigate to localhost:4000 in your browser to view the site. Note that the site is NOT being hosted online. For now, the files are being stored locally on your computer; you're just viewing them with your browser.

Once the site is being locally hosted, you should be able to save any changes you make to its code, wait for a few seconds for Jekyll to "regenerate" your site, then view your changes by refreshing the site in your browser. (If you change the config.yml file, you may need to stop serving the site and restart it.)

# Add a blog post

In a plain-text editor like Atom or TextEdit, create a .md file. The .md extension means that the file should be in Markdown, a simple markup language that lets you use things like bold and italic text, links, images, and headings. [If you need guidance, take a look at this Markdown cheat sheet.](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) Jekyll will also let you use some basic HTML in your .md files.

The file name should include the post date; the date will be automatically displayed at the top of the post. The date and any other text in the file name will be included in the post's URL.

Give your post a header that looks something like this:

```
---
layout: post
title: "Clever Title Here"
author: ajay prabhakar
tags: [blog]
description: > Fill in a description if you'd like; it will appear in a box at the top of the page.
---
```

Make sure the author name matches up with one that appears as a heading in the /data/authors.yml folder. (More on this below.) If it does, that person's formatted bio will appear automatically at the bottom of the post. If you don't want to credit an author, comment out the author field in the header.

Add your file to the site's /posts folder.

# Add an image

To host an image on the site, first make sure its file extension is visible, then place the image file in the /public/img folder. You can then display the image using Markdown:

```
![Alt-text](/public/img/yourfilenamehere.jpg)
```

Or HTML:

```
<img src="/public/img/yourfilenamehere.jpg" alt="alt-text here" />
```

# Add a project

Follow the same procedure you would to add a blog post, with a few changes:
+ Set its layout to "project" instead of "post"
+ Tag your file [project] instead of [blog] in its header
+ Place it in the /projects folder

You'll also need to associate an image with the project, to be displayed as its thumbnail on the Projects page. Place the image you choose in /public/img, then add a line to the header that looks like this:

```
img: yourfilenamehere.jpg
```

If you want the project to appear near the top of the page (essentially, to pin it), add the following to the header:

```
display-order: 1
```

The rest of the projects will be displayed in chronological order, from old to new. You can also customize project order further, if you'd like; see comments in /layouts/projects-ordered.html.

# Add a page

Create a .md file and place it in the main directory. Make your file title whatever you want the page's URL to be. Your header should look something like this:

```
---
layout: page
title: Your Title Here
---
```

# Add a page to the sidebar menu

Look in /includes for a file called nav.html. You'll see that each menu item is generated by the following code:

```
<li>
  <a class="sidebar-nav-item" href="{{ site.baseurl }}/PAGEURLHERE/">Page Title Here</a>
</li>
```

Fill in your page's URL and title and insert the new menu item at the point in the sequence where you'd like it to appear.

# Add a team member

I used a slightly modified version of [this code](http://www.codingpedia.org/ama/how-to-handle-multiple-authors-in-jekyll/) to modify the Hydejack theme to accept multiple authors.

To add a team member (which will then allow you to designate them as the author of a post, and cause their profile to appear on the People page), open data/authors.yml and add their information, using the same formatting as the other names. See the following example:

```
Chromicle:
  name:           ajay prabhakar
  position:       Jekyll Person and Cat Enthusiast
  year:           [2015, 2016]
  site:           http://chromicle.github.io
  avatar:         /public/img/chromicle.jpg <!-- If you have a photo of the person, copy it into /public/img and record the pathway and file name here. -->
  bio:            "ajay prabhakar wrote this readme. One day she will read 'Clarissa.'"
  twitter:        chromicle_3
```

You can fill out multiple years (separated by commas), or only one. If you want the person to appear on the Core Team page, fill in "corecontrib" as their year. If you want them to also appear on the team pages for specific years, their year field might look something like this:

```
year:           [corecontrib, 2015, 2016]
```

You can comment out or delete any fields you don't want to be displayed.

Once you've added this information to the .yml file, create a .md file in /profiles titled with the team member's name as it appears in the YAML heading (so, for this example, chromicle.md). Give it the following header:

```
---
layout: author-page
author-display: teammembernamehere
---
```

Other than the header, leave the page blank. Jekyll will populate it with the person's information and links to any posts or projects they've written.

## Important note about YAML (the markup language used in a .yml file)

YAML uses colons and double quotes as part of its syntax, so it will get confused if any of these things appear in a bio, title, etc. You can solve this problem by putting the full text inside double quotes. Make sure that only single quotes appear within the text.

If you want a feature like italics or a link to appear in a bio, you'll need to write that into the description in HTML (Markdown will not display properly). Make sure your HTML uses single quotes instead of double.

If you try to build your site and get an error related to YAML, the issue is probably with your spacing. Go through and check it, then try building your site again. Run your code through a [YAML validator](http://www.yamllint.com/) if you can't find the problem.

# Add a year to the People page

To, for example, add a page for the 2017 team:

Add a file called 2017.md to /years. Leave the body of the file blank, but give it the following header:

```
---
layout: team
year: 2016
---
```

The page should now be automatically added to the People page menu (generated by /includes/teammenu.html). Any team members with year: [2017] in authors.yml will appear in alphabetical order on the page.

# Make changes to layout/theme

Layouts for different page/post types are stored as HTML files in the /layouts folder. Most of these layouts also call on other HTML files stored in /includes. These are for things like menus, graphics, and author bio boxes that can be incorporated into different layouts.

Most of these HTML files also include a fair bit of Liquid, which you can recognize by its use of curly brackets and percent signs. You can find documentation for Liquid [here](https://shopify.github.io/liquid/) and [here](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).

Liquid essentially allows you to pull information from YAML files and your pages' YAML front matter and display it on a page, or incorporate it into HTML. Here is an example of some code using Liquid (taken from /includes/teammember.html, which generates the team member bios you can see on the People page).

A layout might call /includes/teammember.html with code that looks something like this:

```
{% for author in site.data.authors %}
  {% include teammember.html %}
{% endfor %}
```
This would tell Jekyll to look in the /includes folder for teammember.html. It will then go through data/authors.yml and, for each entry in the file, use teammember.html to create a short team member bio.

teammember.html looks like this:

```
<h3><a href="{{site.url}}/people/{{author[0]}}">{{ author[1].name }}</a></h3>
<h4>{{ author[1].position }}</h4>
{% if author[1].avatar %}
  <img src="{{site.url}}/{{author[1].avatar}}" alt="{{author[1].name}}" style="max-width:400px;max-height:300px;" />
{% endif %}
{% if author[1].bio %}
  {{ author[1].bio }}
  <br>
{% endif %}
```

The first lines use HTML to create a link, but fill in the URL for that link and the hyperlinked text by drawing information from the relevant entry in authors.yml. The double curly braces, `{{ }}`, mean that information should be filled in from the source given inside of the braces. This saves you from having to hand-code each bio.

Note that when dealing with a YAML file like authors.yml, author[0] will return the author's unique identifier (e.g. "chromicle") and author[1].fieldnamehere will return information from whatever YAML field you specify. So author[1].name would return "Yumi Dineen Shiroma", author[1].bio would return the text of my bio, and so on.

`{%  %}` denotes a Liquid statement, often an if/else command. See the official documentation for more examples of Liquid syntax.

To change the site's layout or add new elements, you can add files to /includes and /layouts, or modify existing ones. If you create a new layout, just put its title in the front matter of a page (e.g. "layout: team") to apply it to that page.

# Update gems/dependencies

For Github error message "We found potential security vulnerabilities in your dependencies":

Navigate to the directory where the site is stored and run "bundle update"


Documentation by Yumi Dineen Shiroma, 3/11/17
ydshiroma@gmail.com

---
# Ignore 'vendor' directory

If you are updating the site for the first time or from a new computer, you may need to install ruby or jekyll, which may create a "vendor" sub-directory within the directory. This is required to view the site locally but not for the site to run, so make sure you list it in the .gitignore or its template files could interfere with the build.

For Github error message: The symbolic link `/vendor/bundle/gems/ffi-1.9.25/ext/ffi_c/libffi-x86_64-darwin17/include/ffitarget.h` targets a file which does not exist within your site's repository.

Updated by Alice Tweedy McGrath, 10/25/18
atmcgrath@gmail.com

# Hydejack documentation

Hydejack is a pretentious two-column [Jekyll](http://jekyllrb.com) theme, stolen by [`@qwtel`](https://twitter.com/qwtel) from [Hyde](http://hyde.getpoole.com). You could say it was.. [hydejacked](http://media3.giphy.com/media/makedRIckZBW8/giphy.gif).

## Features
Unlike Hyde, it's very opinionated about how you are going to use it.

Features include:

* Touch-enabled sidebar / drawer for mobile, including fallback when JS is disabled.
* Github Pages compatible tag support based on [this post][tag].
* Customizable link color and sidebar image, per-site, per-tag and per-post.
* Optional author section at the bottom of each post.
* Optional comment section powered by Disqus.
* Layout for posts grouped by year
* Wide array of social media icons on sidebar.
* Math blocks via [KaTeX](https://khan.github.io/KaTeX/).

## Download
Hydejack is developed on and hosted with GitHub. Head to the [GitHub repository](https://github.com/qwtel/hydejack) for downloads, bug reports, and feature requests.

## Sidebar
I love the original Hyde theme, but unfortunately the layout isn't as great on small screens.
Since the sidebar moves to the top, the user has to scroll down just to read the title of a blog post.

By using a drawer component I was able to retain the original two column layout. It's possible to move the drawer via touch input (with the help of a little JavaScript).

Since the background image contributes to the feel of the page I'm letting it peek over the edge a bit. This also provides a hint to the user that an interaction is possible.

## Manual

### Configuration
You can configure important aspects of the theme via [`_config.yml`](https://github.com/qwtel/hydejack/blob/master/_config.yml). This includes:

* the blog description in the sidebar
* the (optional) author description and photo
* default image and link color of the blog
* the github and twitter usernames

### How to Change the Image and Color of a Post
In the manifest of a blog post, simply add an url as `image` and a CSS color as `color`:

~~~yml
layout: post
title: Introducing Hydejack
image: http://qwtel.com/hydejack/public/img/hyde.jpg
color: '#949667'
~~~

### How to Add a New Tag
Tags are possible, but they are not meant to be used #instagram #style: #food #goodfood #happy #happylife #didimentionfood #yougetthepoint. Each tag requires some setup work. I tend to think of it as categories that can be combined.

1.  Add an entry to `_data/tags.yml`, where the key represents a slug and provide at least a `name` value and optionally `image`, `color` and `description`.

    Example `/_data/tags.yml`:

    ~~~yml
    mytag:
      name: My Tag
    ~~~

2.  Make a new file in the `tag` folder, using the same name you've used as the key / slug and change the `tag` and `permalink` entries.

    Example `/tag/mytag.md`:

    ~~~yml
    layout: blog-by-tag
    tag: mytag
    permalink: /tag/mytag/
    ~~~

3.  Tag your blog posts using the `tags` key (color and image will only depend on the first tag).

    ~~~yml
    layout: post
    title: Introducing My New Tag
    tags: [mytag, othertag]
    ~~~

4. (optional) Add the tag to the sidebar, by adding it to `sidebar_tags` in `_config.yml`.
   They will appear in the listed order.

   ~~~yml
   sidebar_tags: [mytag, othertag]
   ~~~

[tag]: http://www.minddust.com/post/tags-and-categories-on-github-pages/

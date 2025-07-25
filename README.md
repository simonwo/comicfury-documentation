# ComicFury Template Engine Documentation

This is a (likely incomplete) list of the variables, conditionals, and loops available using ComicFury's templating engine. It is *not* a guide on *how* to create a layout using the engine-- simply a resource listing the things you can use to do so. This document was compiled by combing through 3-4 different ComicFury templates and extracting all of the templating engine parts individually (as well as by looking at forum threads such as [this one, "CF Layout Code Variable Reference", by MatthewJA](https://comicfury.com/forum/viewthread.php?id=12232#p289444).)

## Contents
- [Top](#comicfury-template-engine-documentation)
- [Contents](#contents) (You are here)
- [Preface](#preface)
- [How to Use](#how-to-use)
- [Overall](#Overall)
  + [Overall Variables](#overall-variables)
  + [Overall Conditionals](#overall-conditionals)
  + [Overall Loops](#overall-loops)
- [Comics Page](#comics-page)
  + [Comics Page Variables](#comics-page-variables)
  + [Comics Page Conditionals](#comics-page-conditionals)
  + [Comics Page Loops](#comics-page-loops)
    * [Quicknav Dropdown Loop](#quicknav-dropdown-loop)
    * [Author Notes Loop](#author-notes-loop)
    * [Comments Loop](#comments-loop)
- [Archive](#archive)
  + [Archive Page Variables](#archive-variables)
  + [Archive Page Conditionals](#archive-conditionals)
  + [Archive Page Loops](#archive-page-loops)
    * [Paginated Comics Loop](#paginated-comics-loop)
    * [Chapter Overview Loop](#chapter-overview-loop)
    * [Pagination Loop](#pagination-loop)
- [Overview](#overview)
  + [Overview Page Variables](#overview-variables)
  + [Overview Page Conditionals](#overview-conditionals)
  + [Overview Page Loops](#overview-page-loops)
    * [Quicknav Dropdown Loop](#quicknav-dropdown-loop)
    * [Latest Blog Posts Loop](#latest-blog-posts-loop)
- [Search](#search)
  + [Search Page Variables](#search-variables)
  + [Search Page Conditionals](#search-conditionals)
  + [Search Page Loops](#search-page-loops)
    * [Search Results Loop](#search-results-loop)
- [Blog Archive](#blog-archive)
  + [Blog Archive Variables](#blog-archive-variables)
  + [Blog Archive Conditionals](#blog-archive-conditionals)
  + [Blog Archive Loops](#blog-archive-page-loops)
    * [Blogs Display Loop](#blogs-display-loop)
    * [Pagination Loop](#pagination-loop)
- [Blog Display](#blog-display)
  + [Blog Display Variables](#blog-display-variables)
  + [Blog Display Conditionals](#blog-display-conditionals)
  + [Blog Display Loops](#blog-display-page-loops)
- [Error Page](#error-page)
  + [Error Page Variables](#error-page-variables)
  + [Error Page Conditionals](#error-page-conditionals)
  + [Error Page Loops](#error-page-loops)
- [Functions](#functions)
- [Other Useful Links](#other-useful-links)


## Preface

The ComicFury templating engine is a massively powerful engine that allows you to create exceptional websites with comparatively little effort. Using a combination of simple variables, conditions, and a small handful of loops, you are able to build a fully customized, dynamic layout in record time. Despite its impressive scale, the templating engine is not particularly difficult to learn or use... however, in order to take full advantage of what it has to offer, one has to know what is available! 

I was unable to find a full documentation reference of the ComicFury templating engine. I could find a few assorted lists of different variables, but it didn't always tell me what pages they could be used on (as some variables can be used on multiple pages for different things) or *exactly what* they output (some variables output  text; others, links; some output entire huge blocks of HTML code.) So I compiled this for myself, but figured it might be useful for somebody else as well.

[Back to Top](#comicfury-template-engine-documentation)

## How to Use

[The basics of the layout documentation can be found on ComicFury here](https://comicfury.com/layoutdoc.php?id=1), which provides the context necessary to understand this document.

This reference lists all of the variables (or conditions, or loops) I found being used on each page. For variables, I have described their output; for conditions, I have described what they output when the expected condition is met; for loops, I have described what the loop is for and what variables and conditions are found within the loop.

If a variable or condition is listed for a page without a description, it's been defined somewhere previously in the document. It is on the list of variables for the page because it is possible to use on that page.

I've taken the liberty of paring down a lot of the example code in the loops for the purpose of showing what is strictly necessary for the code to function. While you will likely need to add much, much more for style/display reasons, what is provided should be enough to get the ball rolling in terms of understanding how the code actually works.

I've also included a list of [#other-useful-links](other useful links) with code snippets I found while trawling the forums that I saved for myself that might also be useful for you.

**NOTE:** Variables and conditions can be used in the HTML **as well as** the CSS.

[Back to Top](#comicfury-template-engine-documentation)

## Overall

This is the HTML that appears on every single page. It is the base for the layout that all the pages are built on. The CSS for the other pages is inserted using `<!--layout:[css]-->` between an opening and closing `<style>` tag. The content of the other pages is added using `<!--layout:[content]-->` somewhere between the opening and closing `<body>` tags.

### Overall Variables
- `[v:lastupdatedmy]` - the last updated date in DD/MM/YYYY format [eg. `08/09/2023`]
- `[v:prevcomic]` - truncated URL to previous comic [eg. `/comics/5`]
- `[v:nextcomic]` - truncated URL to next comic [eg. `/comics/7`]
- `[v:webcomicname]` - the name of the webcomic [eg. `My Webcomic`]
- `[v:pagetitle]` - the name of the page (either the name of the comic page, or the actual page the website is on, eg. overview, blog, archive)
- `[v:permalink]` - the actual URL to the specific page requested
- `[v:comicimageurl]` - the actual URL to this specific comic image.
  * not to be confused with `[v:comicimage]`, which is the image contained within an `<img>` tag, among other things.
- `[v:comicnumber]` - the number of the comic according to the order in which it was published
- `[v:comicwidth]`, `[v:comicheight]` - the width and height of the comic
- `[v:cfscriptcode]` - inserts ComicFury's script code. Don't touch this. Requires no explanation, just don't touch it.
- `[v:banner]` - the actual URL to the uploaded banner if uploaded on the "Webcomic Banner" page.
- `[v:infinitescrolllink]` - if infinite scroll is enabled, contains the actual URL to the infinite scroll version of the comic. 
- `[v:addsubscriptionlink]` - the actual URL to the confirm page to subscribe to the webcomic.
- `[v:comicprofile]` - the actual URL to the Comic Profile.
- `[v:copyrights]` -  copyrights as set on the "Webcomic Info" page.
- `[v:lastupdate]` - the date of the last update, in the format specified in Comic Settings.
- `[v:comicsnum]` - the total number of comics you have posted.
- `[v:subscriptions]` - the number of subscribers to the comic.
- `[v:pageviewsnum]` - the total pageviews to the comic.
- `[v:visitsnum]` - the total unique visits to the comic.
- `[v:webcomicrating]` - sum of all ratings made on your comic.
- `[v:webcomicsub]` - subdomain of your webcomic.
- `[v:webcomicurl]` - the URL of your webcomic (NOT the permalink.)
- `[v:webcomicdescription]` - the Description of your webcomic.
- `[v:webcomicactivitystatus]` - the activity status of your webcomic (active/completed/on hiatus.)
- `[v:webcomicgenre]` - the genre of your webcomic.
- `[v:webcomicslogan]` - the slogan of your webcomic. 
- ~~`[v:banneradcode]` - the HTML for a banner ad for ComicFury.~~ Deprecated and currently does not work.
- ~~`[v:toweradcode]` - the HTML for a tower ad for ComicFury.~~ Deprecated and currently does not work.
  
### Overall Conditionals
- `[c:iscomicpage]` - renders if on a comic page.
- `[c:isfirstcomic]` - renders if the page is the page of the first comic.
- `[c:islastcomic]` - renders if the page is the page of the last comic.
- `[c:comicimageurl]` - renders if there is a comic image URL.
- `[c:banner]` - renders if a banner has been uploaded.
- `[c:infinitescrollenabled]` - renders if infinite scroll is enabled.
- `[c:hasblogs]` - renders if there are any blogs associated with the webcomic.
- `[c:isextrapage]` - renders if the page is an extra page added via "add website page."
- `[c:issearch]` - renders if the page is the page returning the results of a search.
- `[c:searchon]` - renders if the optional search option is on.
- `[c:hidefromhost]` - renders if the comic is hidden from the host. `[!c:hidefromhost]` can be used to wrap things that should only show if the comic is *not* private.
  
### Overall Loops
**Loop: Extra Pages** - this loop allows you to list the "extra pages" from your website pages without having to remember and link every single one. The loop contains two variables-- `[v:l.link]` and `[v:l.title]`, where `[v:l.link]` is the URL to the page and `[v:l.title]` is what the page is called.

```html
[l:extrapages]
  <li><a href="[v:l.link]">[v:l.title]</a></li>
[/]
```

[Back to Top](#comicfury-template-engine-documentation)

## Comics Page

These are all the pages that appear in the `/comics/` section of the website, eg `.../comics/5`.

### Comics Page Variables
- `[v:comictitle]` - the title of the comic as set when uploaded.
- `[v:posttime]` - the post time, including the date, year, and time [eg. 8 Sep 2023, 5:53 PM]
- `[v:chapterlink]` - the actual URL to the chapter collection the comic is in.
- `[v:chaptername]` - the name of the chapter collection the comic is in.
- `[v:comicimage]` - the URL to the comic image contained within an `<img>` tag, ready-to-use.
- `[v:comicimagetype]` - the type of comic uploaded (single page, multi-page, or html)
- `[v:comicnumber]` - the number of the comic according to the order in which it was published
- `[v:prevcomic]`
- `[v:nextcomic]`
- `[v:rating]` - the rating of the comic.
- `[v:votecount]` - the number of people who have rated the comic.
- `[v:ratelink]` - the actual URL to the comic rating page.
- `[v:comicid]` - the ID of your comic on ComicFury.
- `[v:permalink]`
- `[v:commentform]` - the HTML for posting a comment.
  
### Comics Page Conditionals
- `[c:usechapters]` - renders if "Use a chapter system" is turned on.
- `[c:haschapter]` - rendered if the comic is contained within a chapter.
- `[c:allowratings]` - renders if rating is allowed.
- `[c:isfirstcomic]`
- `[c:islastcomic]`
- `[c:allowratings]` - renders if ratings are enabled.
- `[c:rating]` - renders if a comic has a rating.
- `[c:showpermalinks]` - renders if "show permalinks" is set to "yes."
- `[c:authornotes]` - renders if there are author notes.
- `[c:showcomments]` - I... am admittedly not actually sure what this one does...
- `[c:comments]` - renders if there are comments.
- `[c:allowcomments]` - renders if comments are enabled in Webcomic Settings.
- `[c:allowguestcomments]` - renders if guests may add comments.
- ~~`[c:bannerads]` - renders if "Advertisement Settings" are set to "allow."~~ Deprecated and does not currently work.

### Comics Page Loops
#### Quicknav Dropdown Loop
This loop controls the quick navigation dropdown between the links to the previous or next comics. It is contained in a `select` field, which is necessary to get the comic to be able to "jump" to various pages from the dropdown. 

Within the `select` field, we have a loop: `[l:dropdown]`, containing 4 conditions, `[c:l.newgroup]` and `[c:l.endgroup]` for chapter management, and `[c:l.is_seleted]` and `[c:l.is_disabled]`, which contain values that are handled internally. (Though, for context, `[c:l.is_selected]` controls the "pre-selected option" for the dropdown-- the page you're currently on-- and [you can read a little more about how it works on W3Schools here](https://www.w3schools.com/tags/att_option_selected.asp). `[c:l.is_disabled]` is for if a page from the dropdown is disabled. It means you can't click on it. [W3Schools has an article about this as well](https://www.w3schools.com/tags/att_option_disabled.asp), if some context is necessary.)

In `[l:dropdown]`, we have 3 variables: 
- `[v:l.grouplabel]`, the name of the chapter, if your comic has chapters. 
- `[v:l.url]`, the URL to the page we want to access. It is appended with the `#content-start` anchor so that, when the page loads, the comic is front and center. 
- `[v:l.title]`, the title of the comic we are linking to.

```html
<select onchange="jumpTo(this.options[selectedIndex].value);">
  [l:dropdown]
    [c:l.newgroup]<optgroup label="[v:l.grouplabel]">[/]
        <option value="[v:l.url]#content-start" [c:l.is_selected]selected="selected"[/] [c:l.is_disabled]disabled="disabled"[/]>
          [v:l.title]
        </option>
    [c:l.endgroup]</optgroup>[/]
  [/]
</select>
```

As we can see in this code example, we start with the `select` field, with an `onchange` event attribute. The `onchange` attribute means that the moment the user selects something from the dropdown, it will execute the code contained in the `onchange` value, in this case `jumpTo(this.options[selectedIndex].value)`, which will cause the user to "jump" to the selected page.

We then call the `[l:dropdown]` loop, which allows us to create the `option`s within the `select` field. Each `option` is going to be a link that we can select to jump to. 

**If you have chapters, it will display a list of chapters, and the only individual comic links will be to the chapter the user is currently in.** The rest of the links will be to the first comic of the chapters without the individual comics listed. This is handled by the conditional `[c:l.newgroup]`, which holds the `optgroup` tag, which is used to hold related elements within a `select` element. [(More about that on W3Schools here.)](https://www.w3schools.com/tags/tag_optgroup.asp) 

The full `optgroup` tag is `<optgroup label="[v:l.grouplabel]">`, where `[v:l.grouplabel]` is the name of the chapter. This is wrapped in the `[c:l.newgroup]` condition so that it only renders if you have chapters in your comic. **If your comic has chapters, omitting the `optgroup` label will not show a link to every individual comic.** It will just display as it normally would but without groupings, which is visually confusing. 

**If you do not have chapters, the individual comics will be listed in full.** The `[c:l.newgroup]` condition will be false and the comics will simply be listed as each individual `option`.

As for the `option`s in the `select` field, the code is this: 

```html
<option value="[v:l.url]#content-start" [c:l.is_selected]selected="selected"[/] [c:l.is_disabled]disabled="disabled"[/]>
  [v:l.title]
</option>
```

This controls each thing we can select in the dropdown. The `value` tag contains `[v:l.url]#content-start`, which links to the comic page with the anchor of `#content-start`, which jumps straight to the comic. The `[c:is_selected]` and `[c:is_disabled]` conditions have been explained above. Then, within the `option` tag, we have what the option will be called: `[v:l.title]`, the name of the comic it links to.

This `option` tag is generated as many times as ComicFury needs to to fit all of your comics (either in each chapter, or overall) into the dropdown menu. A fully generated loop where the user is on page one of the first chapter may look like this:

```html
<select onchange="jumpTo(this.options[selectedIndex].value);">
    <optgroup label="Chapter One">
      <option value="/comics/1/#content-start" selected="selected">Page One</option>
      <option value="/comics/2/#content-start">Page Two</option>
    </optgroup>
    
    <option value="/comics/3/#content-start">Chapter Two</option>
    <option value="/comics/5/#content-start">Chapter Three</option>
    <option value="/comics/7/#content-start">Chapter Four</option>
</select>
```



#### Author Notes Loop
This one is a bit more complicated. The `authornotes` loop is constructed so that if you have more than one author note, each one is rendered. There are a few different conditions and variables in this loop.
Conditions: `[c:l.is_reply]`, `[c:l.is_last]`, `[c:l.isguest]`, `[c:l.avatar]`, and `[c:l.authorname]`.
Variables: `[v:l.commentanchor]`, `[v:l.avatar]`, `[v:l.profilelink]`, `[v:l.authorname]`, `[v:l.posttime]`, and `[v:l.comment]`.

Conditionals
- `[c:l.is_reply]` - renders if the comment is a reply to another comment.
- `[c:l.is_last]` - renders if it's the last comment in the comment chain.
- `[c:l.authorname!=Guest]Guest[/]` renders the phrase "Guest" next to the commentor's username if they did not select "Guest" as their username.
- `[v:l.commentanchor]` is the ID of the comment that allows you to link to it directly (eg .../comics/5#comment-3288362)

The rest of these should be self-explanatory, but here is the deal: the `l.` before each variable name is because it renders each time the loop runs, and it's the variable *unique to that loop.* So if you have three author comments, the loop runs three times, and needs to check the avatar, authorname, profilelink, posttime, etc every single time. 

```html
[l.comments]
  <div class="comment [c:l.is_reply]reply[/] [c:l.is_last]lastcomment[/]" id="[v:l.commentanchor]">
    [c:l.avatar]
      <div class="avatar">
        <img src="[v:l.avatar]" alt="" />
      </div>
    [/]

    <div class="commentdata">
      [c:!l.isguest]
        <span class="commentusername"><a href="[v:l.profilelink]">[v:l.authorname]</a></span>
      [/]

      [c:l.isguest]
        <span class="commentusername">[v:l.authorname]</span> [c:l.authorname!=Guest](Guest)[/]
      [/]

      <span class="postdate">[v:l.posttime]</span>
    </div>

    <div class="comment-content">
      [v:l.comment]
    </div>

    <div class="commentcontrol">
      <span class="[v:l.editclass]"><a href="[v:l.editlink]\&notitle" onclick="showCommentActionForm(event, [v:l.edit_jsdata]);" target="_blank">Edit</a></span>

      <span class="[v:l.deleteclass]"><a href="[v:l.deletelink]" onclick="showCommentActionForm(event, [v:l.delete_jsdata]);" target="_blank">Delete</a></span>
    </div>
  </div>
[/]
```

#### Comments Loop
It's the same as the Author Notes loop, but now for user comments. The variables are mostly the same. It now includes a `replyform` variable after the `[v:l.editclass]` and `[v:l.deleteclass]` variables, though.

```html
      <span><a href="[v:l.replylink_nopopup]\&notitle" onclick="showCommentActionForm(event, [v:l.reply_jsdata]);" target="_blank">Reply</a></span>
    </div>
  </div>

    <div class="replyform">
      [v:l.replyform]
    </div>

```

[Back to Top](#comicfury-template-engine-documentation)

## Archive

This is the code that appears on the archive pages `.../archive/` as well as the optional `.../archive/comics/` and `.../archive/chapters`.

### Archive Variables
- `[v:chaptername]` -  name of the chapter collection the comic is in
- `[v:chapterdescription]` - The HTML of the chapter description 
- `[v:thumbnail_box_styles]` - the styles of the mouseover box that previews the comic on the comics list.
- ~~`[v:banneradcode]`~~ Deprecated.

### Archive Conditionals
- `[c:ischapterarchive]` - renders if chapters are enabled
- `[c:show_comic_list]` - renders if comic is in comic view (as opposed to chapter view) (or if comic has no chapters)
- `[c:usechapters]` 
- `[c:show_chapter_overview]` - renders if comic is in chapter view
- `[c:lastpagenumber>1]` - renders if you have more than one page of comics.
- ~~`[c:bannerads]`~~ Deprecated.

### Archive Loops
#### Paginated Comics Loop
This is for the page at `/archive/comics` and renders the chapter-divided comics. The loop is utilized with `[l:comics_paginated]`.

- The `[c:l.newchapter]` condition executes if the comic is divided up into chapters, and contains two variables: `[v:l.chaptername]` and `[v:l.chapterdescription]`. You can wrap `[v:l.chapterdescription]` in `[c:l.chapterdescription]` so that the block only renders if the chapter *has* a description.
- After that, the other variables are `[v:l.number]`, which tells you what the page number of the comic overall is, then `[v:l.comictitle]`, `[v:l.comicurl]`, and `[v:l.posttime]`, which tells you when the comic was posted.
- If you need to have code only render after the last comic of the chapter, you can use `[c:l.chapterend]`.

```html
[l:comics_paginated]
    [c:l.newchapter]
        <div class="chapter-name-desc">
            <h3>[v:l.chaptername]</h3>
              [c:l.chapterdescription][v:l.chapterdescription][/]
        </div>
        <div class="nl-archivecomics">
    [/]
    
    <div class="nl-archivecomic">
        <div class="nl-archivecomicnumber">[v:l.number].</div>
        <a class="nl-archivecomictitle" href="[v:l.comicurl]" onpointerover="comicfury.thumbnailMouseOver(event, 'thumbnail-preview-box', [v:l.thumbnail_jsdata])" onpointerout="comicfury.thumbnailMouseOut(event)">[v:l.comictitle]</a>
        <div class="nl-archivecomicposttime">[v:l.posttime]</div>
    </div>
[/]
```

If you want to display *images* for your comic archive, rather than a list of the comics and their titles with the previews available when you hover, ComicFury has a way of doing this as well. It is documented on this thread [here, in a post by Kyo on the forums](https://comicfury.com/forum/viewthread.php?id=45825&page=1#p1136397), in the **"How to convert my archive to have all this new stuff, the hard way"** section within the spoiler toward the bottom. This will be documented in full later...

#### Chapter Overview Loop 
This is very similar to the Paginated Comics Loop, but for chapters instead. 

- The `[c:l.cover]` condition controls the chapter cover. If you have uploaded a cover image, it will display that; otherwise, it displays the very first comic in the chapter. It uses `[v:l.firstcomicinchapter]`, which is a link, wrapped around `[v:l.cover]`, which is the URL to an image. Then the image is set to a width of `[v:l.cover_width_small]` and `[v:cover_height_small]`.
- The second half of the loop controls the details. The `[v:l.chaptername]` is wrapped in a link to the first comic in the chapter again using `[v:l.firstcomicinchapter]`. Then the `[v:l.chapterdescription]` is used to fetch the description. Beneath it, there's a link to the `[v:l.chapterarchiveurl]`, which is a page with a paginated comics loop on it containing all the pages in that chapter.

#### Pagination Loop
If you have enough comics-- it appears to be over 160-- ComicFury splits your list of comics from the paginated comics loop into multiple pages with pagination. (Imagine that!) "Pagination" is just a fancy word for numbered pages. It's wrapped in a condition-- `[c:lastpagenumber>1]`-- which keeps the block from rendering unless you have multiple pages. 

The pagination loop contains two variables: `[v:l.pagelink]`, which is a link to the numbered page, and `[v:l.page]`, which is just the page number.

There are two conditions contained within the pagination condition: the `skipped_ahead` condition and the `is_current` condition. `[c:l.skipped_ahead]` is for when there are many, many pages, and can be used to contain a div with "..." to indicate that the pages have been truncated. The `[c:l.is_current]` simply checks to see if the page number displayed is the number of the page you're currently on.

[Back to Top](#comicfury-template-engine-documentation)

## Overview

This is an optional default page for your webcomic that you can set on the Webcomic Settings. It shows the most recent comment as well as blogs. `.../overview/`. 

### Overview Variables
- `[v:webcomicname]` 
- `[v:latestcomictitle]` - the title of the latest comic published.
- `[v:latestcomicposttime]` - the time posted of the latest comic published.
- `[v:latestcomicpermalink]` - a permalink to the latest comic published.
- `[v:latestcomicdescription]` - the description of the latest comic.
- `[v:latestcomicimage]` - `[v:comicimage]`, but it always displays the most recently published comic.
- `[v:latestcomicimageurl]` - `[v:comicimageurl]`, but it always returns the URL of the most recently published comic.
- `[v:comictitle]`
- `[v:posttime]`
- `[v:chapterlink]`
- `[v:chaptername]`
- `[v:comicimage]`
- `[v:prevcomic]`
- `[v:nextcomic]`
- `[v:comicid]`
- `[v:latestcomicid]` - `[v:comicid]`, but it always provides the ID of the most recently published comic.
- `[v:latestcomiccomments]` - the number of recent comments
- `[v:blogarchivelink]` - the actual URL to the blog archive.
- ~~`[v:banneradcode]`~~ Deprecated.

There are some additional variables exclusively relating to the first comic:
- `[v:firstcomicpermalink]` - A permalink to the first comic.
- `[v:firstcomicid]` - like `[latestcomicid]`, but for the first comic.
- `[v:firstcomictitle]` - the title of the first comic.
- `[v:firstcomicposttime]` - the post time of the first comic.
- `[v:firstcomiccomments]` - the comments on the first comic.
- `[v:firstcomicdescription]` - the description of the first comic.

As well as some related just to the thumbnail:
- `[v:firstcomicthumbnail_url]` - the URL of the first comic thumbnail.
- `[v:firstcomicthumbnail_width]` - the width of the thumbnail image
- `[v:firstcomicthumbnail_height]` - the height of the thumbnail image
- `[v:firstcomicthumbnail_width_small]` - half the width of the thumbnail image
- `[v:firstcomicthumbnail_height_small]` - half the height of the thumbnail image

These variables also exist for the latest comic image:
- `[v:comicthumbnail_url]` - also the URL of the latest comic thumbnail image.
- `[v:comicthumbnail_width]` - the width of the comic thumbnail image.
- `[v:comicthumbnail_height]` - the height of the comic thumbnail image.
- `[v:comicthumbnail_width_small]` - half the width of the comic thumbnail image.
- `[v:comicthumbnail_height_small]` - half the height of the comic thumbnail image.

### Overview Conditionals
- `[c:hascomics]
- `[c:usechapters]`
- `[c:haschapter]`
- `[c:isfirstcomic]`
- `[c:islastcomic]`
- `[c:allowcomments]`
- `[c:latestcomiccomments]`
- `[c:hasblogs]`
- `[c:hasmoreblogs]`
- ~~`[c:bannerads]`~~ Deprecated.

### Overview Loops
#### Quicknav Dropdown Loop
This is the same loop as is present on the Comics Page. See the [Quicknav Dropdown Loop](#quicknav-dropdown-loop) for more.

#### Latest Blog Posts Loop
This loop controls the display of latest blog posts and supports up to five blog posts (so the loop runs a maximum of five times.) The loop has 3 variables: `[v:l.bloglink]`, a link to the blog post, `[v:l.blogtitle]`, the title of the blog, and `[v:l.blog]`, the blog post itself. The `[c:l.allowcomments]` condition displays a simple, short link to the blog itself so that users can view the comments, but doesn't actually display them. The `[c:l.comments!=1]` condition hides or displays the letter "s" at the end of "comments" if there is a singular comment, allowing you to avoid it saying the grammatically incorrect "1 comments." 

```html
[l:latestblogs]
  <div class="blog">

      <h3><a href="[v:l.bloglink]">[v:l.blogtitle]</a></h3>

          <div class="blogcontent">[v:l.blog]</div>

    [c:l.allowcomments]
      <div class="blogmeta">
        <a href="[v:l.bloglink]#comments">[v:l.comments] Comment[c:l.comments!=1]s[/]</a>
      </div>
    [/]
  </div>
[/]
```

Within the loop, there is a conditional called `[c:l.allowcomments]`, which, if you have comments enabled, offers the ability to show the number of comments with `[v:l.comments]`.

`<a href="[v:l.bloglink]">view [v:l.comments] comment[c:l.comments!=1]s[/]</a>`

[Back to Top](#comicfury-template-engine-documentation)

## Search 

The search page, available at `.../search/`.

### Search Variables 
- `[v:searchterm]` - What the user searched for in the search bar.
- ~~`[c:banneradcode]`~~ Deprecated.
  
### Search Conditionals
- `[c:searched]` - renders if something has been searched using the search bar.
- `[c:foundresults]` - renders if something has been found after searching.
- ~~`[c:bannerads]`~~ Deprecated.

### Search Loops
#### Search Results Loop
The `[l.searchresults]` loop displays a list (much like the archive) of results returned when using the search function. It has 3 variables, `[v:l.comicurl]`, `[v:l.comictitle]`, and `[v:l.posttime]`, which you already know about.

```html
[l:searchresults]
  <div class="comic-number">[v:l.number]</div>
  <a href="[v:l.comicurl]">[v:l.comictitle]</a>
  <div class="time-posted">[v:l.posttime]</div>
[/]
```

[Back to Top](#comicfury-template-engine-documentation)

## Blog Archive
Available at `.../blog/` and `.../blogarchive/` (after the second page of blogs.)

### Blog Archive Variables
No variables outside of the loops.

### Blog Archive Conditionals
- `[c:hasblogs]` - renders if there are any blogs associated with the webcomic.

### Blog Archive Loops
#### Blogs Display Loop
The `[l:blogs_paginated]` loop shows each blog entry, the author and time it was posted, as well as the number of comments on the blog post.

```html
[l:blogs_paginated]
  <div class="blog">
      <span class="posttime">[v:l.posttime]</span>
      [c:l.avatar]
        <div class="blogavatar">
          <img src="[v:l.avatar]" alt="[v:l.authorname]">
        </div>
      [/]
      <div class="authordata"><a href="[v:l.profilelink]">[v:l.authorname]</a></div>
      <span class="blogtitle"><a href="[v:l.bloglink]">[v:l.blogtitle]</a></span>
    
      <div class="blogcontent">
        [v:l.blog]
      </div>

    [c:l.allowcomments]
      <div class="blogmeta">
        <a href="[v:l.bloglink]#comments">[v:l.comments] Comment[c:l.comments!=1]s[/]</a>
      </div>
    [/]
  </div>
[/]
```

#### Pagination Loop
The Pagination Loop was already used on the Comics Page and is exactly the same each time it appears. You can view the [documentation for the Pagination Loop here](#pagination-loop).

[Back to Top](#comicfury-template-engine-documentation)

## Blog Display

This is for the display of the actual blog page itself, eg. `.../blogarchive/38936`

### Blog Display Variables
- `[v:blogtitle]` - the  title of the blog.
- `[v:blog]` - the HTML of the blog itself, as generated by ComicFury.
- `[v:prevbloglink]` - the actual URL of the previous blog.
- `[v:blogarchivelink]` - the actual URL to the blog archive.
- `[v:nextbloglink]` - the actual URL of the next blog.
- `[v:profilelink]`
- `[v:avatar]` 
- `[v:authorname]`
- `[v:posttime]`
- `[v:commentform]`

### Blog Display Conditionals
- `[c:prevbloglink]` - renders if there is a previous blog to link to, i.e. if this isn't the first blog post
- `[c:nextbloglink]` - renders if there is a next blog to link to, i.e. if this isn't the last/most recent blog post
- `[c:avatar]` - renders if the user has uploaded an avatar.
- `[c:showcomments]`
- `[c:comments]`
- `[c:allowcomments]`
- `[c:allowguestcomments]` - renders if guest comments are allowed.

### Blog Display Loops
Because this is the page for each individual blog post, the only loop is the [Comments Loop](#comments-loop), which has already been defined on the Comics page.

[Back to Top](#comicfury-template-engine-documentation)

## Error Page

The page that shows whenever someone attempts to view a page that does not exist.

### Error Page Variables
- `[v:errortitle]` -  error text.
- `[v:errormessage]` - HTML for the error message.
  
### Error Page Conditionals
This page contains no conditionals.

### Error Page Loops
This page contains no loops.

[Back to Top](#comicfury-template-engine-documentation)

## Functions

Sometimes it is useful to slightly transform the value of a variable before you put it on the page. For that, ComicFury has some helpful functions.

Functions can be used on any of the above variables, including loop variables, at any time.

### Math functions
These functions all expect two numbers, which can be variables.

- `[f:add|a|b]` - adds up A and B (example: `[f:add|3|2]` will output `5`).
- `[f:subtract|a|b]` – subtracts B from A (example: `[f:subtract|3|2]` will output `1`).
- `[f:multiply|a|b]` – multiples A and B (example: `[f:multiply|3|2]` will output `6`).
- `[f:divide|a|b]` divides A by B (example: `[f:multiply|3|2]` will output `1.5`).
- `[f:randomnumber|a|b]` chooses a random number between A and B inclusive (example: `[f:randomnumber|3|2]` could output `2` or `3`). The output will be picked randomly every time the page loads, so you should use this sparingly as it reduces the performance of ComicFury and your webcomic.

### Text functions
Normally when ComicFury outputs a variable, it replace any apostrophes with the HTML entity `&#039;` and any quotation marks with the HTML entity `&quot;`. This means it is always safe to output a variable directly into HTML without breaking your site. (For example, `<div class="[v:custom.value]">` will always be valid HTML, even if `[v:custom.value]` contains quotation marks.) Note that this doesn't apply to literal text passed to a function.

These functions all modify that default behaviour and control how a variable is output.

- `[f:js|v:text]` will output the variable `[v:text]` and replace more characters that aren't letters or numbers (so apostrophes, quotation marks, brackets, emojis, for example) with JavaScript escape sequences, surrounded by quoutation marks. The result is always a string that will be valid in `<script>` tags.
- `[f:rawhtml|v:text]` will output the variable `[v:text]` without escaping the apostrophes and quotation marks.
- `[f:removehtmltags|v:text]` will output the variable `[v:text]` and remove all of the HTML tags. Tags that contain human-readable text (such as `<b>` for bold text) will be replaced with just their text. Tags that contain code (such as `<script>` or `<style>` tags) will be completely removed.
  + So `[f:removehtmltags|<b>bold text</b>]` becomes just `bold text` (that isn't bold!).
  + And `[f:removehtmltags|cool <script>alert("Hello!");</script> text]` becomes just `cool  text`.

## Other Useful Links

Most of these are lifted directly from the [Random Code Snippet Archive](https://comicfury.com/forum/viewthread.php?id=8597), but I think they're worth putting here regardless.

[Fancy Transcript Code](https://comicfury.com/forum/viewthread.php?id=48484) by [lookitslars](https://comicfury.com/profile.php?username=lookitslars) - a code for adding a collapsible (native!) transcript to your comic without Javascript, improving accessibility

[Dynamic Chapter Themes](https://comicfury.com/forum/viewthread.php?id=43344) by [PTGigi](https://comicfury.com/profile.php?username=PTGigi) - a guide on how to make it so that your webcomic theme changes based on what chapter the reader is on. 

[Hiding/Showing Comments After a Certain Number](https://comicfury.com/forum/viewthread.php?id=8597&page=1#p262089) by [Kyo](https://comicfury.com/profile.php?username=Kyo) - hides comments after a certain number (eg. 5) but allows you to see more if you click the "show more comments" button.

[Using a Random Background Each Time the Page Loads](https://comicfury.com/forum/viewthread.php?id=8597#p355616) by [Xenocartographer](https://comicfury.com/profile.php?username=Xenocartographer) - self-explanatory.

[Auto-Resizing Comic Images](https://comicfury.com/forum/viewthread.php?id=16209) - if a comic image is too big, resize it to fit the layout, but then add the ability to click a link to see the comic at full size.

[A Guide to Dark Mode](https://mournstera.tumblr.com/plugins/darkmode) by [Flipse on Tumblr](https://mournstera.tumblr.com/) - a way to add Dark Mode to a set of pages that the browser can "remember" so that you don't get flashbanged on a per-page basis.

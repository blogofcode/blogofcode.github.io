---
layout:     post
title:      Creating and maintaining your own BLOG
date:       2016-11-08 12:31:19
summary:    Github provides a free service Github Pages where you can create static webpages easily.
categories: jekyll pixyll
author:     A SAI RAHUL
permalink:  /creating-and-maintaining-your-own-blog/
tags:
  - github-tag
---

In this small blog post, we use Github Pages `Jekyll` theme [Pixyll](https://github.com/johnotander/pixyll).
There are many beautiful themes. Check out these links to select the theme that suits your need.
[Jekyll](https://github.com/jekyll/jekyll/wiki/themes), [Jekyll](http://jekyllthemes.org), [Jekyll](https://jekyllthemes.io), [Jekyll](http://themes.jekyllrc.org).
I chose `Pixyll` because it is simple to use, has beautiful user interface and is mobile first and I personaly think is the beast theme for coding blogs. [Blog of Code](http://www.blogofcodes.com) is also made using this theme.

### SETTING UP

   * Open [Pixyll](https://github.com/johnotander/pixyll) and Fork the repo, and then clone it so you've got the code locally.(on top-right).
   * After it has been forked, got to `Settings` on top navigation bar.
   * Change the `Repository name` to `your-github-username.github.io` and click rename.
   * Go to url `https://your-github-username.github.io`.

There you go, you created your static blog.

### MODIFY CONTENT

The `_config.yml` located in the root of the Pixyll directory contains all of the configuration details for the Jekyll site. The defaults are:

{% highlight markdown %}
    # Site settings
    title: Pixyll
    email: your_email@example.com
    author: John Otander
    description: "A simple, beautiful theme for Jekyll that emphasizes content rather than aesthetic fluff."
    baseurl: ""
    url: "http://pixyll.com"

    # Build settings
    markdown: kramdown
    permalink: pretty
    paginate: 3
{% endhighlight %}

   * pagination: number of blog posts you want to display on single page.
   * title: blog_name
   * email: your_email@example.com
   * author: your name
   * description: "describe your blog"
   * url: "http://your-github-username.github.io"

You can check furthur options in the same file.

   * date_format
   * show_related_posts
   * show_post_footers
   * show_social_icons etc,.

You can also link your social account to the blog by simply compyting the usernames to respective usernames under `
# Social icons` in the same file.

### ADDING COMMENTS SECTION

By default, there are no comments added to each blog post.

   * Got to [Facebook Developers](https://developers.facebook.com/apps/). Create an account, if you don't have one.
   * Add new app by clicking `Add a New App`.
   * Fill all the details, such as `Display Name`, `Contact Email, and choose `Category` and click `Create App ID`
   * Go to Dashboard and copy `App ID`.
   * Paste it in the `_config.yml` file beside facebook_appid as:

{% highlight markdown %}
    # Facebook Comments plugin
    # (leave blank to disable Facebook Comments, otherwise set it to true)
    facebook_comments: true
    facebook_appid: App ID
    facebook_comments_number: 10
{% endhighlight %}

    * Make sure `facebook_comments` is true and set the number of comments you want to display on each blog post.


Happy blogging!


---







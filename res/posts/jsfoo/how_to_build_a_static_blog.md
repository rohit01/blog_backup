title: How to Build a Static Blog
output: how_to_build_a_static_blog.html

---
# How to Build a Static Blog

---
### Blog decisions

* **Content & Design**
* **Static vs Dynamic**
* **Hosting** - maintenance, cost, features
* **Domain** - personal vs derived / free

---
### Why go with static approach?

* Free hosting + **total control**
* Zero maintenance
* Fast

---
### What about dynamic features?

* New blog posts
* Comments
* Search

---
### New blog posts

* Static website generators
    * Jekyll - Github pages support this
    * Octopress
    * Docpad
    * ... and many more
* New blog post - easy markdown

---
### Jekyll blog post example

```
  ---
  layout: post
  date: 2014-02-09 15:19:00 IST
  title: Simplicity
  ---

  Today, I changed the title of my blog to **Simplicity**. A simple thought, life, action and relation is somewhere lost in this complicated world! **Simplicity is an aquired taste**. A taste, which helped google dominate the web, Apple to be regarded as the biggest brand and Mahatma Gandhi to become the father of the Nation.

  The first thing to realize about simplicity is that, it does not mean *LIMITED*. **Simplicity is about subtracting the obvious and adding the meaningful**. The problem here is that the 'obvious' is not so OBVIOUS :(

  Simplicity also means, the achievement of maximum effect with minimum means. A absence of luxury or showiness, enjoying plainess.

  **And as always, Thanks for reading :)**

```

---
### Comments

* Disqus: free but proprietary

---
### Search

* Google custom search
    * Depends on google indexing
    * Branding and CSS
* Full text search
    * Does not scale
    * Basic

---
### Google CSE Example

![Simplicity - google CSE](/res/posts/jsfoo/google-cse.jpg)

---
### Full text search example

![Simplicity - Full text search](/res/posts/jsfoo/full_text_search.png)

---
### lunr.js

* Simple full-text search in your browser
    * [lunrjs.com](http://lunrjs.com)
* I am using: **Jekyll + lunr.js**
    * [github.com/slashdotdash/jekyll-lunr-js-search](https://github.com/slashdotdash/jekyll-lunr-js-search)
* Example: [www.rohit.io/search](http://www.rohit.io/search/)

---
### Thank You
<br />
<center>
**Rohit Gupta**  
[@rohit01](https://twitter.com/rohit01)  
[www.rohit.io](http://www.rohit.io)  
<br />
**Satyamev Jayate**  
starts oct 5, dekhna zarur :-)
</center>

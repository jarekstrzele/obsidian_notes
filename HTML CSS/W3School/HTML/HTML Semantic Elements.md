[[_HTML-W3school]]

---

# Semantic elements
>A semantic element clearly describes its meaning to both the browser and the developer.

semantic: `<form> <table> <article`
non-semantic: `<div> <span> ...`

![[sem_html_elems.excalidraw]]

---

## `<section> </section>`
defines a section in a document.
>A section is a thematic grouping of content, typically with a heading

(chapters, introductions, news items, contact information)

---
## `<article> </article>`
- specifies independent, self-contained content
- should make sense on its own
- should be possible to distribute it independently

(forum posts, blog, posts, user comments, products cards, newpaper article)

```html
<article>
<h2>Google Chrome</h2>
<p>Google Chrome is a web browser developed by Google, released in 2008. Chrome is the world's most popular web browser today!</p>
</article>

<article>
<h2>Mozilla Firefox</h2>
<p>Mozilla Firefox is an open-source web browser developed by Mozilla. Firefox has been the second most popular web browser since January, 2018.</p>
</article>
```

articles in sections - ok
sections in articles - ok

---
## `<header> </header>`
typically contains:
- one or more heading elements (`<h1> <h2> ...`)
- logo or icon
- authorship information

>represents a container for introductory content or set of navigational links


---
## `<footer> </footer>`

defines a footer for a document or section

typically contains:
- authorship information
- copyright info
- contact info
- sitemap
- back to top links
- related documents

---

### `<nav> </nav>`
defines a set of navigation links
```html
<nav>
  <a href="/html/">HTML</a> |
  <a href="/css/">CSS</a> |
  <a href="/js/">JavaScript</a> |
  <a href="/jquery/">jQuery</a>
</nav>
```

---
## `<aside> </aside>`
defines some content aside from the main content 

---
## `<figure> </figure>`
specifies self-contained content, like illustrations, diagrams, photos, code listings....

`<figcaption>` tag:
- defines a caption for a `<figure>` element,
- can be placed as the first or the last child of a `<figure>` element

```html
<figure>
  <img src="pic_trulli.jpg" alt="Trulli">
  <figcaption>Fig1. - Trulli, Puglia, Italy.</figcaption>
</figure>
```

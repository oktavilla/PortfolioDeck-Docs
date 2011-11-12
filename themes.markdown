---
layout: doc
title: Themes Documentation
---





# Themes Documentation

This documentation is for creating custom themes in PortfolioDeck. Don't hesitate to drop us a line if you got any questions or comments. Send an email to <hello@portfoliode[.com>.





## Contents

* [Introduction][intro]
* [Templates and assets][templates]
* [Global objects[global]
* [Template specific objects][template_objects]
* [Filters][filters]
* [Image sizes][sizes]






[intro]: ## Introduction

We use [Liquid](http://www.liquidmarkup.org/) as our templating language. If you ever have designed themes in [Shopify](http://www.shopify.com/?ref=winston) you've used it. If you're new to Liquid, please take a couple of minutes to read through [Liquid for designers](http://wiki.github.com/tobi/liquid/liquid-for-designers). Don't worry, we'l[wait. Done? Good, let's proceed.

[templates]: ## Templates and assets

A theme consists of six template files and accompanying assets (stylesheets, javascripts and graphics). There is a template for each page type. There is also a layout template for the framework of the site (header, navigation and footer). Each page template is rendered inside the [yout template.

* [layout.liquid][[ayout_template]
* [index.liquid][index_template]
* [collection.liquid][collection_template]
* [set.liquid][set_template]
* [item.liquid][item_template]
* [p[e.liquid][page_template]

[layout_template]: ### layout.liquid

The layout template is used to set the framework for the site. This is were you'll place all the elements that should be available on every page of your site. E.g. logo, navigation, footer. It is also in this template that you write your <code>&lt;html&gt;</code>, <code>&lt;head&gt;</code> and <code>&lt;body&gt;</code> tags.

#### Availableobjects

* [global objects][global]

[index_template]: ### index.liquid

The index template is your sites front-page.

#### Available objects

* [Global objects][global]

[collection_template]: ### collection.liquid

This template renders a collections page. The main purpose of this page would most likely be to show the sets in a collection.

#### Available objects

* [Global objects][global]
* [collection][collection_object]

[set_template]: ### set.liquid

This template renders a set page. On this page you can, for example, show the first item in the set or an overview of all items in the set.

#### Available object[
* [Global objec[][global]
* [[t][set_object]

[item_template]: ### item.liquid

This template renders an item page. An item is an image (soon we we'll also support movies) that you have uploaded and placed in a set. On this page you might want to render the image in your preferred size and display title and description.

#### Available objects

* [Global objects[global]
* [item][item_object]

[page_template]: ### page.liquid

The template renders one of your static pages.

#### Available objects

* [Global objects][global]
* [page][page_object]







[global]: ## Global objects

These objects are available in all template files.

* collections
* sets
* link_lists
* page_title

### Collections

The 'collections' object is available in all templates. It contains a list of all collections in the portfolio.

You can also retrieve a specific collection with its 'handle' e.g. 'collections.main', where <code>main</code> is the handle, will return the <code>collection</code> with the handle <code>main</code>.

[Check out the docs for the collection object][collection_object]

#### Example

For example, if you want to create a list of links to all your collections this is how you would do it.

<pre>{% if collections != empty %}
  &lt;ul&gt;
  {% for _collection in collections %}
    &lt;li&gt;&lt;a href="{{ _collection | path }}"&gt;{{ _collection.title }}&lt;/a&gt;&lt;/li&gt;
  {% endfor %}
  &lt;/ul&gt;
{% endif %}</pre>

### Sets

The <code>sets</code> object is available in all templates. It contains a list of all sets in the portfolio.

You can also retrieve a specific <code>set</code> with its <code>handle</code> e.g. <code>sets.main</code>, where <code>main</code> is the handle, will return the <code>set</code> with the handle <code>main</code>.

[Check out the docs for the set object][set_object]

#### Example

For example, if you wanted to create a list of links to all your sets this is how you would do it.

<pre>{% if sets != empty %}
  &lt;ul&gt;
  {% for _set in sets %}
    &lt;li&gt;&lt;a href="{{ _set | path }}"&gt;{{ _set.title }}&lt;/a&gt;&lt;/li&gt;
  {% endfor %}
  &lt;/ul&gt;
{% endif %}</pre>

### Pages

The <code>pages</code> object is available in all templates. It contains a list of all pages in the portfolio.

You can also retrieve a specific <code>page</code> with its <code>handle</code> e.g. <code>pages.main</code>, where <code>main</code> is the handle, will return the <code>page</code> with the handle <code>main</code>.

[Check out the docs for the page object][page_object]

#### Example

For example, if you wanted to create a list of links to all your pages this is how you would do it.

<pre>{% if pages != empty %}
  &lt;ul&gt;
  {% for _page in pages %}
    &lt;li&gt;&lt;a href="{{ _page | path }}"&gt;{{ _page.title }}&lt;/a&gt;&lt;/li&gt;
  {% endfor %}
  &lt;/ul&gt;
{% endif %[/pre>

[link_lists_object]: ### link_lists

The <code>link_lists</code> object is a global array of all your link lists. To retrieve a <code>link_list</code> object you need to supply its <code>handle</code>. E.g. <code>link_lists.main</code> where <code>main</code> is the handle, will return the <code>link_list</code> with the handle <code>main</code>.

* <code>link_lists.example_handle</code> <br>Returns the <code>link_list</code> with the handle <code>example_handle</code>.
* <code>link_lists.example_handle.links</code> <br>Returns an array of <code>links</code>.
* <code>link_lists.example_handle.title</code> <br>Returns the title of the <code>link_list</[de>.

[link_object]: ### link

Each <code>link</code> in an link_list object has:

* <code>link.current</code> <br>Returns <span class="caps">TRUE</span> if you are on the page where that link points.
* <code>link.title</code> <br>Returns a string with the links title.

#### Example

<pre>&lt;ul id="nav"&gt;
  {% for _link in link_lists.main.links %}
    &lt;li{% if _link.current %} class="current"{% endif %}&gt;&lt;a href="{{ _link | path }}"&gt;{{ link.title }}&lt;/a&gt;&lt;/li&gt;
  {% endfor %} 
&lt;/ul&gt;</pre>

### page_title

Returns a string with the title of the current page. If the current page is a <code>set</code> it returns the <code>set.title</code> and so on for <code>page</code>, <code>collection</code> and <code>item</code>[




[template_objects]: ## Template specific objects

* collection
* set
* item
* [ge

[collection_object]: ### collection

The current collection is retrieved with <code>collection</code>. It is available in the <code>collection.liquid</code> template. These variables are available on the collection object:

* <code>collection.title</code> <br>Returns a string with the collections title.
* <code>collection.description</code> <br>Returns a string with the collections description.
* <code>collection.uri</code> <br>Returns a string with the <span class="caps">URI</span> for the collection.
* <code>collection.sets</code> <br>Returns an array with the sets in the collecti[.

[collection_set]: ### set

The current set is retrieved with <code>set</code>. It is available in the <code>set.liquid</code> template.

These are the available variables on the set object:

* <code>set.title</code> <br>Returns a string with the sets title.
* <code>set.description</code> <br>Returns a string with the sets description.
* <code>set.cover</code> <br>Returns a object with the sets cover image.
* <code>set.items</code> <br>Returns an array with the items in the se[

[item_object]: ### item

The current item is retrieved with <code>item</code>. It is available in the <code>item.liquid</code> template.

These variables are available on the item object:

* <code>item.title</code> <br>Returns a string with the items title.
* <code>item.description</code> <br>Returns a string with the items description.
* <code>item.width</code> <br>Returns an integer with the width of the original.
* <code>item.height</code> <br>Returns an integer with the height of the original.
* <code>item.landscape</code> <br>Returns <span class="caps">TRUE</span> if width &gt; height.
* <code>item.portrait</code> <br>Returns <span class="caps">TRUE</span> if width &lt; height.
* <code>item.next_item</code> <br>Returns an object with the next item in the set.
* <code>item.previous_item</code> <br>Returns an object with the previous item in the set.
* <code>item.set</code> <br>Returns an object with the set the item belongs.
* <code>item.position</code><br>Returns an integer with the <code>items</code> position in relation to the other items in the set[

[page_object]: ### page

The current page is retrieved with <code>page</code>. It is available in the <code>page.liquid</code>.

These are the available objects:

* <code>page.title</code> <br>Returns a string with the page title.
* <code>page.body</code> <br>Returns a string with the pages body content.




[[filters]: ## Filters

This is the filters we have set up specifically for PortfolioDeck. Liquid also has its own <a href="http://wiki.github.com/tobi/liquid/liquid-for-designers">standard filters</a>.

* <code>path</code>
* <code>path_with_collection</code>
* <code>asset_tag</code>

### path

The <code>path</code> filter is used to get the address for a <code>collection</code>, <code>set</code>, <code>item</code> or <code>page</code>.

#### Examples

<pre>&lt;a href="{{ collection | path }}"&gt;{{ collection.title }}&lt;/a&gt;</pre>

This would result in:

<pre>&lt;a href="/collection/the-title"&gt;The Title&lt;/a&gt;</pre>

### path_with_collection

The <code> path_with_collection </code> filter is used to get the address for a <code>set</code> or <code>item</code> with the parent <code>collection</code> added to the address.

#### Examples

<pre>&lt;a href="{{ set | path_with_collection: collection }}"&gt;{{ set.title }}&lt;/a&gt;</pre>

This would result in:

<pre>&lt;a href="/collection/collection-title/set/set-title"&gt;The Title&lt;/a&gt;</pre>

### asset_tag

The <code>asset_tag</code> is used to get the <span class="caps">HTML</span> for an item.

#### Examples

<pre>{{ item | asset_tag: '685' }}</pre>

If the item is an image this would result in:

<pre>&lt;img src="/images/YOUR_ACCOUNT_NAME/685/item_filename.jpg?token=RESIZE_TOKEN" alt="Item Title" width="685" height="400"&gt;</pre>





[sizes]: ## Image sizes

As you see in the example above we supply '685' to the asset tag. This is the size the asset will be displayed in. There are a couple of different ways to get the desired size.

* <code>685</code> <br>Renders the image within a 685px square. If the image is in landscape format it will be 685px wide. An image in portrait format will be 685px high.
* <code>685x500</code> <br>Renders the image within a rectangle with a width of 685px and a height of 500px.
* <code>w685</code> <br>Renders the image with a width of 685px.
* <code>h685</code> <br>Renders the image with a height of 685px.
* <code>c200x250</code> <br>Renders the image cropped to 200px width and 250px height.

### Examples

<pre>{{ item | asset_tag: 'w685' }}</pre>
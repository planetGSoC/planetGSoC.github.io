<p align="center">
  <img width="320" height="320" src="https://2.bp.blogspot.com/-K5NjtdmmQgY/V_KwiwXH-LI/AAAAAAAAA6U/R1eXaWE4R6sEF3rnomIOwTK_UzohhSkDgCPcB/s320/image00.jpg">
</p>

# [planetGSoC.github.io](http://planetgsoc.github.io/)
Planet for GSoC - A Google Summer of Code Blog Aggregator. 

PlanetGSoC uses river5 as it's river-of-news RSS aggregator which is written in NodeJS and is deployed on OpenShift with the help of TravisCI. The code resides in the [river branch](https://github.com/planetGSoC/planetGSoC.github.io/tree/river).

[![DEPLOY ON OpenShift](http://launch-shifter.rhcloud.com/launch/DEPLOY%20ON.svg)](https://openshift.redhat.com/app/console/application_type/custom?&cartridges[]=nodejs-0.10&initial_git_url=https://github.com/planetGSoC/river5.git&name=river5-planetGSoC)

This branch contains the frontend. 

Feel free to contribute by sending in pull requests or opening issues.

## Adding your blog to http://planetgsoc.github.io/

You can add your Blog's feed to the [river branch's lists/gsoc.txt](https://github.com/planetGSoC/planetGSoC.github.io/blob/river/lists/gsoc.txt) by sending a pull request. Please try to add blogs that are related to Google Summer of Code or you can read below to add tags/labels to your blog and get it's feed.

You can also edit the file without cloning the directory to your machine. Just click the edit button.
![https://help.github.com/assets/images/help/repository/edit-file-edit-button.png](https://help.github.com/assets/images/help/repository/edit-file-edit-button.png)

### Jekyll Powered Blogs

Jekyll allows you to add tags to your blogs. After adding tags it is as easy as adding the following feed generator for that tag.

You can add tags by adding this to the YAML: 

```yaml
---
layout: post
title: Participating in Google Summer of Code 2016
tags:
- gsoc
---

Blog Content...

```

And then simply add the following file and save it as `feed-gsoc.xml`.

```xml
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
    <title>{{ site.title | xml_escape }}</title>
    <description>{{ site.description | xml_escape }}</description>
    <link>{{ site.url }}{{ site.baseurl }}/</link>
    <atom:link href="{{ "/feed-gsoc.xml" | prepend: site.baseurl | prepend: site.url }}" rel="self" type="application/rss+xml"/>
    <pubDate>{{ site.time | date_to_rfc822 }}</pubDate>
    <lastBuildDate>{{ site.time | date_to_rfc822 }}</lastBuildDate>
    <generator>Jekyll v{{ jekyll.version }}</generator>
    {% for post in site.tags.gsoc limit:10 %}
      <item>
        <title>{{ post.title | xml_escape }}</title>
        <description>{{ post.content | xml_escape }}</description>
        <pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
        <link>{{ post.url | prepend: site.baseurl | prepend: site.url }}</link>
        <guid isPermaLink="true">{{ post.url | prepend: site.baseurl | prepend: site.url }}</guid>
	{% for tag in post.tags %}<category term="{{ tag }}"/>{% endfor %}
        {% for tag in page.tags %}
        <category>{{ tag | xml_escape }}</category>
        {% endfor %}
        {% for cat in page.categories %}
        <category>{{ cat | xml_escape }}</category>
        {% endfor %}
      </item>
    {% endfor %}
  </channel>
</rss>
```

Finally, you can add the link (`http://rhnvrm.github.io/feed-gsoc.xml`) to [river branch's lists/gsoc.txt](https://github.com/planetGSoC/planetGSoC.github.io/blob/river/lists/gsoc.txt) in a new line.

### Blogger/Blogspot powered blogs

You can add a label named `GSoC` to your blog and the feed for that specific tag will reside in `blog.com/feeds/posts/default/-/GSoC/?alt=rss`. You can then add this to [river branch's lists/gsoc.txt](https://github.com/planetGSoC/planetGSoC.github.io/blob/river/lists/gsoc.txt) in a new line.


### Wordpress powered blogs

Feed for Wordpress blogs can be generated at `http://www.example.com/?tag=tagname&feed=rss2` or `http://example.in/feed/?cat=gsoc-2016`. You can read up the documentation here: `https://codex.wordpress.org/WordPress_Feeds#Categories_and_Tags`. Add this in a new line to [river branch's lists/gsoc.txt](https://github.com/planetGSoC/planetGSoC.github.io/blob/river/lists/gsoc.txt)

---

planetGSoC is powered by the GSoC Community.

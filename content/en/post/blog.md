---
date: 2022-01-22T16:00:00+01:00
description: "From laziness to motivation"
featured_image: "/images/letters_bg_1280.jpg"
tags: ["cms","golang","hugo"]
title: "This is the story of a blog"
---

You, who are passing through this modest place, are probably wondering what you will find here...
There are many subjects in this world that can be tackled with more or less success.

I confess, a little shamefully, that this is only a piece of a secret garden, or rather a shared vegetable garden.
Indeed, if your heart is in it,
I would like to plant seeds,
I would like to share with you some of my experiments, some of my thoughts.

Every journey begins with a first step, so let's start with the creation of this reading corner.
If you allow me a little digression, which I am afraid I am too fond of,
it's been a few years since I took the time to publish in this way.

First came the idea,
it was not well-formed and lacked sufficient will to manage any tool on my own.
So I looked at the well-known platforms, here a [medium](https://medium.com/), there a [wordpress](https://wordpress.com/).
I tried, in vain, to convince myself: the important thing was the writing exercise, the path, not the form or the tool.
However, an insistent voice whispered in my ear: "Have courage, take your dexter out of the foundation".

Then came the motivation.
I needed something technical enough to be fun,
simple so as not to waste too much time, and free so as not to waste too much money.
As a developer by profession, I had a brainstorm: can I manage the blog like I manage code?
I impose myself two constraints, keep the source manager and use known technologies.
In short, I would like to use [Git](https://git-scm.com/) and [github](https://github.com/),
and find a [CMS](https://fr.wikipedia.org/wiki/Syst%C3%A8me_de_gestion_de_contenu) in [Go](https://go.dev/).

Anyway, I chose [Hugo](https://gohugo.io/) without much surprise.
It's an [open source](https://github.com/gohugoio/hugo) tool written in Go that allows to generate static sites.
It seems to be only a detail, but one day I'll have to tell you about the world of Open Source,
at the same time fabulous and worrying, open and ruthless, it will be the subject of a next ballad.

Let's go back to our sheep, but to better understand the rest of our journey,
I must explain to you how Hugo works.
It is a tool that will take content written in [Markdown](https://fr.wikipedia.org/wiki/Markdown),
use a [template](https://gohugo.io/templates/) to transform it into a clean and beautiful site.
You will have understood, Hugo provides you both a structural base to customize
and generation tools to lead you to the ultimate goal: the publication of your site.

That's all very nice, you may say, but how and where do you publish this Blog?
Yes, I can store the content and structure of the site in a Github repository,
but where will I publish it?
It happens that Github offers to host static pages via [Github Pages](https://pages.github.com/).

I see you coming, and you're right, I can't (decently) put the content of the Hugo project in the Github Pages repository.
The missing brick to solve this puzzle can be provided by a [continuous integration](https://fr.wikipedia.org/wiki/Int%C3%A9gration_continue).
It turns out, that [Github Actions](https://docs.github.com/en/actions) meets these expectations.

Well, I have an editing/generation repository and a publishing repository.
Let's see how I can get around this schmilblick.
On the publishing repository, I activate the Github Actions and define their behaviors directly in the repository.
Using their superpowers, I have to [teleport the sources](https://github.com/actions/checkout),
get the [necessary tools](https://github.com/peaceiris/actions-hugo) for the generation,
transmute the material into a site and [deploy](https://github.com/peaceiris/actions-gh-pages) to Github Pages.
All these incantations can be read in the [grimoire](https://github.com/jbdoumenjou/myblog/blob/main/.github/workflows/gh-pages.yml) of the site.

If you were curious enough to read the incantations of this site, you may have detected some mysticism, the power word `secrets.GH_TOKEN`.
You will have to imbue it with your person, so that the spell acts only for you, to do this,
I encourage you to consult this [document] (https://docs.github.com/en/actions/security-guides/automatic-token-authentication).

Are you still here? What courage, what self-sacrifice!
We have come to the end of this adventure, finally to the first stage.
Let's summarize in a few words:

* First the definition of the content and the look thanks to [Hugo](https://gohugo.io/).
* Then [Github](https://github.com/) to store and take advantage of adapted tools
  such as [Github Actions](https://docs.github.com/en/actions) to transmute the sources into a site and deploy it auto-magically.
* Finally [Github Pages](https://pages.github.com/) to expose the site publicly.


Let's be honest, this is only a very small first stone.
There are still some untranslated elements, some leftovers of the default theme, the structure is basic,
the possibility to make comments is missing and many other things.
Still, it is a sufficient step to start sharing with you,
and to open the way for fabulous adventures (or small misadventures).

I leave you here, hoping to see you soon!
May the winds be favorable to you.

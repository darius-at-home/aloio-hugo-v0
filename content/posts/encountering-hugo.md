---
title: "Encountering Hugo"
date: 2022-11-20T14:32:04-08:00
tags: metablogging
---

Well I can't say I'm thrilled about the tight coupling between themes, configs,
and content, but it seemed pretty easy to onboard so let's see what happens when
we push.

NB: left off at [#Directory Structure](https://jpanther.github.io/congo/docs/getting-started/#directory-structure)
in the theme docs.

---

So far this is coming down to:

1. go templates vs jinja
1. the lots more convenient (hugo) vs the sightly more flexible (pelican) toolchain
1. a mild preference for working in python vs the better (though still not very
   well structured) documentation for hugo

---

Starting to make more sense now that I realize that the theme is the thing that
kinda drives the site.  Which probably would have been obvious sooner if I had
any experience with other <abbr title="static site generator">SSG</abbr>s.

---

NB: You **MUST** have the suffix on the page filepath in order for `hugo new` to
work.  Unfortunately the `failed to resolve "foo" to a archetype template` error
message isn't all that helpful if you just made a typo.

Still really liking this thing in general but it *definitely* has the "the better
your porcelain, the harder your users will find it to perform DIY fixes on the
plumbing when it does break" problem.  Docs matter.  And (cf diataxis) doc
*structure* matters.

Oh and the problem I had with the default config is that if you put it into the
`config` directory you need to name the default subdirectory `_default` instead
of `default`.

But hey at least I sorta understand how site menus work now.  They just don't
exist out of the box (at least in ananke) because you need to set them up.

```
themes/ananke/layouts/partials/site-navigation.html
12:      {{ if .Site.Menus.main }}
14:          {{ range .Site.Menus.main }}
```

Any case, the big lesson so far is that themes in Hugo are a much more central
than they first appeared.  They include a lot of semantic constraints on the
type and structure of the content you can create.

---

Ohhh...  So you _are_ supposed to keep the root level config file.

---

Welp, so much for the nice quickstart.  Gonna need config environments sooner or later, so
thought I'd postpone trying to get site nav for later.  Config merge doesn't quite work the
way I'd interpreted the docs, sadly, but at least if you do `--environment default` it works.

---

Disappointed that [Goldmark](https://gohugo.io/getting-started/configuration-markup/#goldmark)
doesn't have subscript and superscript tho.  And no site/category nav by default?

---

{{< figure src="/images/site/thumbs-up-25607_960_720.png" alt="Big Thumbs Up."
    caption="Big thumbs up to Hugo." >}}

So I'm trying Hugo out because I got a little frustrated with the docs for Pelican and:

1. Badass project
1. I can kinda see why people like Go

More to the point of #2, I can see how Go encourages a lot of good coding habits, which
is definitely nothing to sneeze at.  And of course, I can tell without even spending any
time in the Hugo codebase, that everything about it will confirm my preconceptions about
software development. 😉

Seriously, what's impressed me most so far is how trivially easy it was to discover why
the html tag for the thmbs-up image above wasn't rendering, and how to fix it.  And the
docs...  Swoon.

(TTA: [pixabay](https://pixabay.com/vectors/thumbs-up-thumb-yes-success-sign-25607/) for the image. )

---

What's really going on here is more like reconnaissance than an encounter.

Kinda surprised you don't get TOC for free in the quickstart.

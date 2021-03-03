# MDITA topics

The LwDITA specification describes 2 MDITA "profiles": core and extended. Only extended MDITA, in my opinion, is of any interest because it allows the inclusion of HDITA tags through which mechanisms like content referencing and filtering can be applied. Any further references to "MDITA" from now on are to "Extended MDITA" unless otherwise stated.

Both core and extended MDITA align with [GitHub-flavoured Markdown](https://github.github.com/gfm/) \(GFM\). If you are comfortable withe GFM, you will have no problem with MDITA. Every thing you can do with GFM, you can do in MDITA.

In addition in extended MDITA, you can add a YAML header section that permits you to add the following key/value pairs:

```
---
id: some_ID
shortdesc: Some test here as a short description
author: Joe Schmo
---

# Title
```

Adding YAML header frontmatter can be useful when working with some Static Site Generators \(SSGs\). Although, at time of writing, getting some SSGs to support MDITA output is still difficult. This hopefully will change when the standard is released and more users attempt to integrate Leightweight DITA with their favorite SSG.

You can also add Multimarkdown-style tables if you prefer not to add tables in HTML:

```
| First Header | Second Header | Third Header |
| ------------ | :-----------: | -----------: |
| Content      | *Long Cell*                 ||
| Content      | **Cell**      | Cell         |
```

Footnotes are possible using the PHP Markdown system:

```
That's some text with a footnote.[^1]

[^1]: And that's the footnote.
```

And, most importantly from the point of view of integrating features like content reuse and content filtering, you can add a subset of the HDITA tags.


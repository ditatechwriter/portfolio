# Using LwDITA output with GitBook

The DITA-OT comes with ready-made build instruction that creates a `summary.md` file from your ditamap. The `summary.md` file is used by Gitbook \(and it's open-source equivalent MdBook\) to create the navigation for your document.

```
$ dita --input=some.ditamap --output=docs --format=markdown_gitbook
---

```


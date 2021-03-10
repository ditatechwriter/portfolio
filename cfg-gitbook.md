---
id: cfg-gitbook
---

# Using LwDITA output with GitBook

The DITA-OT comes with ready-made build instruction that creates a `SUMMARY.md` file from your ditamap. The `SUMMARY.md` file is used by Gitbook (and its open-source equivalent MdBook) to create the navigation for your document.
```
$ dita --input=some.ditamap --output=docs --format=markdown_gitbook
```
You can link your GitBook account to the branch in your repository (or a folder within it) where you store your output files.

> [!NOTE]
>  This is a note.

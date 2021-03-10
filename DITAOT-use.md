---
id: DITAOT-use
---

# Installing and using the DITA Open Toolkit

In order to take advange of LwDITA's content reuse mechanism, you need to transform your raw MDITA content into an output format that incorporates the key, conref or filter magic. The tool for that is the DITA Open Toolkit (DITA-OT).

If you want to build your content locally, you'll need to download it from DITA-OT website [dita-ot_download] page. Installing it is as easy as downloading a ZIP files, extracting it to a folder on your machine and add the folder containing the main DITA-OT executable to your $PATH variable. See the [Installing DITA-OT] page for (slightly) more detail.

The DITA-OT is a command-line tool with a single command `dita` and a range of parameters to tweak how you want the output to look. The following is a sample build argument that uses *some.ditamap* as an input file (`--input`), specifies the *docs* subfolder in the same folder as the input file to put the output files (`--output`), and defines the output format as *markdown_github* (`--format`).
```
$ dita --input=some.ditamap --output=docs --format=markdown_github
```
This command will transform all the files referenced in *some.ditamap* into GitHub-flavored Markdown files and deposit them in the *docs* folder.

There are other parameters that give you more fine-grained control over the buildp rocess. See [dita_command] for details.

## DITA-OT plugins vs SSGs

The DITA-OT comes with a variety of built-in plugins for transforming your content into HTML5, PDF, EPUB, Markdown and more. There are also many community-contributed (as well as commerical) plugins available for more specialized output.

The output of the bundled DITA-OT plugins is generally pretty basic by design. The idea is that you can customize the output to suit your own needs. However, plugin customization can be a something of a dark art, and particularly HTML5 and PDF customizations take a lot of work and knowledge of XSLT and XSL-FO. For that reason, I think using using out-of-the-box Markdown as an output format offers technical writers a new opportunity - to style their docs using a static site generator rather than a DITA-OT plugin for web-based docs.

Static site generators (SSGs) are, on the whole, much better documented than the DITA-OT plugins (with the possible exception of Leigh White's book, [dita-for-print]). There are even some that are specifically for technical documentation, and even the more all-purpose SSGs have nice documentation themes. Software houses are also more likely to have a web designer on staff than an XSLT guru so specialist customization of a static site generator is more likely to be in the company toolbox than plugin customization. I think using static site generators for LwDITA output deserves serious consideration.


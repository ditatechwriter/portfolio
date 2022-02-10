---
id:LwDITA-toolchain
---

# A Lightweight DITA toolchain

I only describe here a toolchain that I use. The aim however in any docs-as-code set up, in my opinion, is to have a flexible an attitude to tools as possible and, ideally avoiding, as much as possible, dependence on proprietary tools.

## Writing content in a text editor

At time of writing (with about a year to go until the Lightweight DITA 1.0 standard is published), mature support for Lightweight DITA even among tools used most commonly for writing standard DITA (Oxygen XML Editor, Adobe Framemaker) is spotty. However, you can certainly write Lightweight DITA without spending $$$ on specialist editors, and. with the publication of the Lightweight DITA 1.0 standard, better support will be provided.

To write Lightweight DITA in the formats I discuss here, all you need is an text editor capable of handling Markdown and XML. Common open-source progamming editors like Atom, Visual Studio Code, or Eclipse all have plugins that permit you to work in Markdown and XML.

## Managing content in a version control system

Many software house use an online host for their code repositories based on Git. GitHub is perhaps the most popular, along with Gitlab and BitBucket.

## Building output with the DITA Open Toolkit

The DITA Open Toolkit (DITA-OT) supports the conversion of MDITA files into HTML5, PDF, various markdown flavors and other output formats.

## Automating builds

There are many options to choose from here from CircleCI, TravisCI, and the one I use for this site, GitHub Actions. All of these can be used to build and lint content.

## Displaying content using static site generators
Because MDITA files can be outputted as Markdown there many options for using MDITA outputs with static site generators (SSGs). MDITA content can be added to the following SSGs:

- Gitbook/MDBook
- Docsify
- MkDocs
- Docusaurus
- Jekyll
- Hugo


---
id:md-dac
---

# Markdown and docs-as-code

Most docs-as-code practitioners favor a plain-text format for writing their docs. Although it is possible to XML formats such as [DITA](https://en.wikipedia.org/wiki/Darwin_Information_Typing_Architecture) or [Docbook](https://en.wikipedia.org/wiki/DocBook) in a doc-as-code set-up, the need of specialist tools to validate the XML, and the general unreadability of heavily tagged documents make them a less popular choice. 

Other plain-text formats such as [AsciiDoc](https://en.wikipedia.org/wiki/AsciiDoc) or [reStructuredText](https://en.wikipedia.org/wiki/ReStructuredText), while eminently more readable than the XML formats mentioned above, are also only really used by technical writers and, consequently, not ideal for reviewing in their raw formats. And, like the XML vocabularies, they present a not insignificant learning curve for new writers who, given the relative rarity of these formats, are unilkely to have come across them before.

## Markdown to the rescue

Unlike the other formats discussed, the use of [Markdown](https://en.wikipedia.org/wiki/Markdown) is, I would argue, central to a succesful implementation of a doc-as-code publication pipeline. Here's why:

- Markdown is easy to learn. You can pick it up in half an hour.
- Markdown is ubiquitous. Developers all know it, and are happy to review and contribute to documentation that uses it.
- Markdown can be written in any old plain-text editor. Use a developer's editor like Atom, or Visual Studio Code, or Eclipse and you have content completion, spell-checking, and linting features that make writing Markdown very straightforward.
- Online code storage and versioning platforms like GitHub have integrated Markdown editors that make reviewing Markdown code very easy for your reviewers.
- There are a plethora of static site generators (SSGs) that can turn simple Markdown content into beautiful documentation sites relatively easily.

With content written in Markdown, training new writers is easy, reviewing documentation is easy, even publication is (relatively) easy. But Markdown is not without it's limitations.




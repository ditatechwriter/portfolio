# What Markdown cannot do

Unlike the more sophisticated formats like DITA or AsciiDoc, Markdown lacks keys features that make it suitable for large and complex documentation needs. Maintaining documentation for multiple products with multiple versions in plain Markdown is a significant challenge.

## Content reuse

Markdown has no mechanisms for content reuse. If, for example, your product has 3 version (e.g. Lite, Professional, Enterprise) you would need to keep three discrete markdown document sets, one for each version, even if each document set had significant portions of content in common. This would mean of course that if you would need to make any updates to the shared content in each document set individually.

Similarly, if you had a single topic that explained how to install your product on Windows, MacOS, and Linux, and the install instructions for each contained shared steps, you have to make any updates to that shared content in 3 places.

The lack of any content reuse facility, therefore, introduces significant maintenance overhead for documentation written in Markdown.

## Text variables

The ability to use variables for things like product or company names or any word or short phrase used through a text and that is likely to change, is a boon for technical writers. By defining a variable in one place that is updated throughout the text is much less risky than global find and replace. Markdown, alas, has no way to add text variables.

## Content filtering

Content filtering allows you to to produce different version of a document form a single source. So, instead of having three individual document sets to produce manuals for our Lite, Professional and Enterprise products, we would prefer one source set of documents that could filter out non-relevant version -specific content at build time to produce the manual for a given product version.

Again, Markdown offers no filtering mechanism for producting multiple documents from a single source.

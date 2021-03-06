---
id: MDITA-conrefs
---

# Using content references with MDITA

For content that appears in several locations in document, DITA writers use the content referencing ( or *conref*) mechanism.

The best way to manage content in a document is to use a "warehouse" file. This is an ordinary MDITA (or HDITA) file containing the content snippets you want to reuse in the document. Warehouse files are added to your root ditamap using a topicref and should have the *processing-role* set to *resource-only*. 

A MDITA Markdown topic can be used for a warehouse file but the content to be referenced must be in HDITA tags.

A sample MDITA conref warehouse topic, conref.md:
```
---
id: conref-content
---

# Conref content

<p id="install-step1">First, download the appropriate installer for your operating system from the <span keyref="product_name"></span> website <span keyref="gruntmaster-downloads"></span> page.</p>

...
 
```
To reference the shared content within an MDITA markdown file, an HDITA tag must be used along with the *id* attribute set. Note also the use of the \<span\> tags to reference keys. Because the conref content is HTML5, we cannot use Markdown mark-up for key referencing. If you want to reference a key within conref snippet use the format `\<span keyref="somekey"\>\</span\>`.

To use snippet in the conref warehouse file add a \<p\> tag with a *conref* attribute value that uses the following format CONREF SOURCE FILE NAME#TOPIC ID/TAG ID. For example:
```
## Installing the [product_name] companion app

Follow the instructions below to install the [product_name] companion app on Mac OSX:

1. <p conref="conref.md#conref-content/install-step1"></p>
1. Double-click on the DMG icon, and follow the installation wizard instructions.
1. When installation is complete, restart your device.
```
Once built the HDITA tag is replaced by the referenced text in Markdown:
```
## Installing the Grunt Master 6000 companion app

Follow the instructions below to install the Grunt Master 6000 companion app on Mac OSX:

1. First, download the appropriate installer for your operating system from the Grunt Master 6000 website [Downloads](https://gruntmaster6000.com/downloads) page.
1. Double-click on the DMG icon, and follow the installation wizard instructions.
1. When installation is complete, restart your device.
```



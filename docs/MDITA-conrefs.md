# Using content references with MDITA

For content that appears in several locations in document, DITA writers use the content referencing \( or *conref*\) mechanism.

The best way to manage content in a document is to use a "warehouse" file. This is an ordinary MDITA \(or HDITA\) file containing the content snippets you want to reuse in the document. Warehouse files are added to your root ditamap using a topicref and should have the *processing-role* set to *resource-only*.

A MDITA Markdown topic can be used for a warehouse file but the content to be referenced must be in HDITA tags.

A sample MDITA conref warehouse topic:

```
---
id: conref-content
---

# Conref content

<p id="install-step1">First, download the appropriate installer for your operating system from the [product_name] website [gruntmaster-downloads] page.</p>

<p id="disclaimer">Gruntmaster Industries accepts no liability for any injury, blindness, infertility, or death caused by even casual use of the [product_name].</p>

...
 
```

To reference the shared content within an MDITA markdown file, an HDITA tag must be used along with the *data-conref* attribute. The value for the *data-conref* attribute uses the following format <TOPIC FILE NAME\>\#<TOPIC ID\>/<TAG ID\>. For example:

```
## Installing the Grunt Master 6000 companion app

Follow the instructions below to install the Grunt Master 6000 companion app:


<---! Reviewers, go to conref.md and look at the paragraph with the install-step1 ID if you want to review this step. --->
1. <p conref="conref.md#conref-content/install-step1"></p>
1. Double-click on the installer, and follower the installation wizard instructions.
1. When installation is complete, restart your device.
```

Once built the HDITA tag is replaced by the referenced text.

As in the above example, it's a good idea to add a comment that points reviewers towards the conref source in case they might want to review that content too.


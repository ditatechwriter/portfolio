# Organizing MDITA topics with XDITA maps

If you are only used to writing in Markdown, you probably use a file in your static site generator to give a navigation order to your Markdown files. A map in LwDITA does exactly the same thing, and when built, the map is outputted as a file (index.md) that can be used by an SSG as a navigation TOC.

A map also has another important uses: it provides a place where variablized content can be stored, where files containing shared content can be referenced, and where content filter files can be located.

Maps basically have 5 tag types:

- \<map\> - a container for the map tags
- \<topicref\> - a reference to topic
- \<keydef\> - a key definition (we'll look at keys in more depth later)
- \<navtitle\> - an alternate title for a topic

In addition, each tag can have a range of attributes. For more information, see the latest [LwDITA-Spec].

Here is a sample map written in XDITA, the XML flavor of LwDITA:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD XDITA Map//EN" "map.dtd">
<map id="portfolio-map">
    <topicref href="intro.md" format="markdown" keys="intro"/>
    <topicref href="dac.md" format="markdown" keys="dac">
        <topicref href="md-dac.md" format="markdown" keys="md-dac"/>
        <topicref href="md-limits.md" format="markdown" keys="md-limits"/>
    </topicref>
    <topicref href="dac2-0.md" format="markdown" keys="dac2-0">
        <topicref href="lwdita-overview.md" format="markdown" keys="lwdita-overview"/>
        <topicref href="MDITA-topics.md" format="markdown" keys="MDITA-topics"/>
        <topicref href="HDITA-tags.md" format="markdown" keys="HDITA-tags"/>
        <topicref href="XDITA-maps.md" format="markdown" keys="XDITA-maps"/>
    </topicref>   
    <topicref format="markdown" href="Dita-dac.md" keys="ddac"/>
    <topicref format="markdown" href="DITA4dac.md" keys="d4dac">
        <topicref format="markdown" href="write-review-MDITA.md" keys="write-MDITA"/>
        <topicref format="markdown" href="Ditamaps4dac.md" keys="MDITA-maps"/>
        <topicref format="markdown" href="MDITA-keys.md" keys="MDITA-keys"/>
        <topicref format="markdown" href="MDITA-conrefs.md" keys="MDITA-conrefs"/>
        <topicref format="markdown" href="MDITA-filters.md" keys="MDITA-filters"/>
        <topicref format="markdown" href="publish-MDITA.md" keys="publish-MDITA"/>
        <topicref format="markdown" href="test.md" keys="test"/>
    </topicref>
    <topicref format="ditamap" href="keydefs.ditamap" keys="keydefsmap"
        processing-role="resource-only"/>
    <topicref format="markdown" href="conref.md" keys="conrefs" processing-role="resource-only"/>
    <topicref href="mac-exclude.ditaval" format="ditaval" processing-role="resource-only"/>
</map>
```
Note that each markdown file is identified using a *href* attribute in a topic reference tag. Note also that the format attribute defines the file type as *markdown*. Use `format="markdown"` to indicate the file is to be processed as "extended" MDITA - in other words allowing the features that go beyond what is permitted in simple GitHub-flavored Markdown. See [MDITA-topics] for a fuller discussion of "extended" MDITA.

One topic reference has `format="ditamap"`, meaning that I have embedded another map within this map. In this case it is for key definitions but yo ucould just as easily add a submap of topic references.

I have given each topic reference the above example a key using the *keys* attribute. This is optional and I'll explain the use of keys further on.

Some topic references are have `processing-role="resource-only"`. The resource-only processing role tells the DITA-OT to use this file during the build but not to add it to the index.md TOC.


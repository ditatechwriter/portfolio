# Organizing MDITA topics with XDITA maps

If you are only used to writing in Markdown, you probably use a file in your static site generator to give a navigation order to your Markdown files. A map in LwDITA does exactly the same thing, and when built, the map is outputted as a file (index.md) that can be used by an SSG as a navigation TOC.

A map also has another important uses: it provides a place where variablized content can be stored, where files containing shared content can be referenced, and where content filter files can be located.

Maps basically have 5 tag types:

- \<map\> - a container for the map tags
- \<topicref\> - a reference to topic
- \<keydef\> - a key definition (we'll look at keys in more depth later)
- \<navtitle\> - an alternate title for a topic

In addition, each tag can have a range of attributes. For more information, see the [LwDITA-Spec].

Here is a sample map written in XDITA, the XML flavor of LwDITA:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD XDITA Map//EN" "map.dtd">
<map id="portfolio-map">
    <topicref href="intro.md" format="mdita" keys="intro"/>
    <topicref href="dac.md" format="mdita" keys="dac">
        <topicref href="md-dac.md" format="mdita" keys="md-dac"/>
        <topicref href="md-limits.md" format="mdita" keys="md-limits"/>
    </topicref>
    <topicref href="dac2-0.md" format="mdita" keys="dac2-0">
        <topicref href="lwdita-overview.md" format="mdita" keys="lwdita-overview"/>
        <topicref href="MDITA-topics.md" format="markdown" keys="MDITA-topics"/>
        <topicref href="HDITA-tags.md" format="markdown" keys="HDITA-tags"/>
    </topicref>   
    <topicref format="mdita" href="Dita-dac.md" keys="ddac"/>
    <topicref format="mdita" href="DITA4dac.md" keys="d4dac">
        <topicref format="mdita" href="write-review-MDITA.md" keys="write-MDITA"/>
        <topicref format="mdita" href="Ditamaps4dac.md" keys="MDITA-maps"/>
        <topicref format="mdita" href="MDITA-keys.md" keys="MDITA-keys"/>
        <topicref format="mdita" href="MDITA-conrefs.md" keys="MDITA-conrefs"/>
        <topicref format="mdita" href="MDITA-filters.md" keys="MDITA-filters"/>
        <topicref format="mdita" href="publish-MDITA.md" keys="publish-MDITA"/>
        <topicref format="mdita" href="test.md" keys="test"/>
    </topicref>
    <topicref format="ditamap" href="keydefs.ditamap" keys="keydefsmap"
        processing-role="resource-only"/>
    <topicref format="mdita" href="conref.md" keys="conrefs" processing-role="resource-only"/>
    <topicref href="mac-exclude.ditaval" format="ditaval" processing-role="resource-only"/>
</map>
```


---
id: MDITA-keys
---

# Using keys with MDITA

Keys in DITA provide an means of indirect referencing. A key is way to provide an alternative name to a resource such as text string or a URL. By referrring to the resource by its key rather than directly, you have more flexibility in being able to change the content of resource in one place and see updated content reflected through the document. This is make maintaining text  or links that are liable to change much easier to maintain.

Keys are defined in a ditamap. They can be added to a root map or - if there are many - contained in a dedicated key definitions map of their own which is referenced in the root map.

A key definitions map added as a submap to your main root ditamap is useful way to manage keys. It uses *keydef* tags rather than *topicref* tags. By default *keydef* tags have their *processing-role* attributes set to *resource-only*, so the content of a *keydef* tag never appears in the navigation TOC. 

## Using keys for text variables

Single words or short text strings can be variabilized using keys. it's a good idea to use a text variable for any text, such as product name or company name, that is used frequently in a text and which could change based on factors over which the writer has no control. That way, the text value can be changed in one place and it will be updated throughout the document. Much better than using a risky global find-and-replace, which may have unintended consequences.

The recommended format for creating a key definition in an keydefs map is:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD XDITA Map//EN" "map.dtd">
<map id="keydefs-map">    
    
    <keydef keys="product_name">
        <topicmeta>
            <linktext><ph>Gruntmaster 6000</ph></linktext>
        </topicmeta>
    </keydef>

...

</map>
```
Within an MDITA topic the key is referenced by putting it within square brackets:
```
The [product_name] represents a leap forward in home exercise technology! 
```
Once built, `\[product_name\]` will be replaced by the string "Gruntmaster 6000".

## Using keys for external links

If you link to an external site in several places in your document, it's a good idea to use a key to refer to that site, so if the URL of the site ever changes you only need to update it in one place.

The recommended format for defining a key for an external link is:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD XDITA Map//EN" "map.dtd">
<map id="keydefs-map">  

  <keydef keys="gruntmaster-userguide" href="https://www.gruntmaster6000.com/userguide/index.html" scope="external" format="html">
    <topicmeta>
        <linktext>Gruntmaster 6000 user guide</linktext>
    </topicmeta>
  </keydef>

...

</map>
```
Note that the *scope* attributes must be set to *external* and the format attribute to the file type (usually *html*) of the external resource.

In your MDITA topic you can then refer to the site via its key wthin square brackets rather than a URL, for example:
```
For more information, see [gruntmaster-userguide].
```
Once built, the final Markdown output is:
```
For more information, see [Gruntmaster 6000 user guide](https://www.gruntmaster6000.com/userguide/index.html).
```

## Using keys for internal links

You can (and I recommend that you do) use keys for internal links in your docs. By linking to another file using a key rather than a href, you give yourself the flexibility to change the file name or location in the DITA map without having to make updates in every topic where the file is referenced.

You do not need to use a separate key definition map to set a ket for an internal resouce, you can do that in root ditamap itself, for example:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD XDITA Map//EN" "map.dtd">
<map id="root-map"> 

  <topicref href="MDITA-topics.md" format="markdown" keys="MDITA-topics">
     <topicmeta>
        <navtitle>MDITA topics</navtitle>
     </topicmeta>
  </topicref>

...

</map>
```
The keys attribure in the topicref tag is used to set the key. A *navtitle* tag containing the topic title needs to be added within *topicmeta* tags so that the topic title is used for the link and not the file name. In a topic the internal file is referenced as follows:
```
For more information, see [MDITA-topics].
```
Once built, the final Markdown output is:
```
For more information, see [MDITA topics](MDITA-topics.md).
```






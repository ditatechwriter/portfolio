# Lightweight DITA

With the advent of the upcoming [Lightweight DITA](https://www.oasis-open.org/committees/download.php/65658/lwdita.pdf) (LwDITA) 1.0 standard (sometime hopefully in early 2022), some of the advantages of a heavy-weight documentation solution like DITA can be applied to Markdown content.

LwDITA is a simplified form of the DITA standard with only 48 tags in total and comes in 3 flavors:

- XDITA - a subset of the main DITA standard XML elements.
- HDITA - A DITA variant written in HTML5 rather than XML.
- MDITA - A DITA variant written in Markdown rather than XML. This is based on GitHub-flavored Markdown but incorporates MultiMarkdown features for tables.

Gone from LwDITA is any notion of information typing. There are only two file types: map and topic.

MDITA is the real game changer for docs-as-code but we will need all 3 variants for a complete solution.

As with normal Markdown, you can include HTML tags and in this case HDITA tags can be used in MDITA topics. The use of HDITA tags allows important DITA features such as content referencing and content filtering. Using HDITA tags, however, does not add sufficient complexity to the MDITA source that it interferes with ease of editing for non-specialist reviewer. 

As with standard DITA, MDITA files are organized into maps. Maps provide the organizing principle - the navigation table of contents - for a documentation site. Maps too can be written in Markdown although to take full advantage of what LwDITA maps have to offer, I suggest using XDITA for maps. This is probably new to folks who have only used Markdown before but the learning curve is not so steep as XDITA maps are are cut-down versio nof those found in standard DITA. From a review point of view, there is no probel mas reviewers would not normally need to be review map files. 

Specialized HDITA files holding key definitions or content reference content used in build processing only can also be added to maps along with the MDITA files.

# Using filters with MDITA

Filtering content, be it individual words, sentences, paragraphs or even entire topics, in MDITA files requires two things. A way to mark particular content for filtering, and build instruction that tells the DITA Open Toolkit to remove the content at build time. The former is achieved by the incorporating HDITA tags that use a *props* attribute value. The latter requires a special file called a `.ditaval` file that contains the build instruction added to ditamap containing the content to be filtered. Several ditavals can be added to a map. A parameter added to the build instrution is used to defione which `.ditaval` file is to be used.

In the following example, items in an unordered list can be diltered by operating system. Note in the example below that the entire unordered list must be in HDITA markup not simply the list items that are to be filtered.

```
## Supported Operating Systems

The following operating systems are supported by the [product_name] lite edition companion app:

<ul>
  <li props="mac">Mac OSX</li>
  <li props="win">Windows 10 and higher</li>
  <li props="linux"> Ubuntu Linux 18.04 and higher</li>
  <li props="bsd">FreeBSD 11.4 or higher</li>
</ul>
```

To filter out the first list item, the ditaval filter file `nix_exclude.ditaval` used by the build instruction is:

```
<?xml version="1.0" encoding="UTF-8"?>
<val>
    <prop action="exclude" att="props" val="linux"/>
    <prop action="exclude" att="props" val="bsd"/>  
</val>
```

The DITA open toolkit instruction needs to include the `nix_exclude.ditaval`:

```
dita -i some_map.ditamap -f markdown_github -o some__output_folder --filter=nix_exclude.ditaval
```

The resultant Markdown output is:

```
## Supported Operating Systems

The following operating systems are supported by the Gruntmaster 6000 lite edition companion app:

- Mac OSX
- Windows 10 and higher
```

The `props` attribute can also used at the map level to filter out whole files from a build:

```
<topicref href="somefile.md" format="markdown" props="mac"/>
```


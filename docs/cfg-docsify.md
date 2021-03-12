# Using LwDITA output with Docsify

Docsify is JavaScript framework for documentation sites. It has several great advantages when working with Lightweight DITA:

-   It accepts the `index.md` outputted by the `markdown_github` DITA-OT transform from your ditamap for site navigation.

-   It uses a single easy-to-use configuration file.

-   It has a range of simple-to-deploy plugins for common documentation features, including: - search - code highlighting - copy code link - source editing on GitHub - collapsible navigation TOC - single page TOC - pagination


## Configuring Docsify for LwDITA output

Here is a sample Docisify configuration page \(`index.html`\) with all the features on this site:

```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>Michael McLoughlin DITA Tech Writer</title>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="viewport"
    content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/themes/vue.css" />
  <link rel="stylesheet" href="https://unpkg.com/docsify-toc@1.0.0/dist/toc.css" />
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/sidebar.min.css" />
  
  <script src="//cdn.jsdelivr.net/npm/docsify-edit-on-github"></script>
</head>

<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      name: "Your site name here",
      repo: "Your GitHub repo here", // Use the format AccountName/reponame
      homepage: 'myHomepage.md', // File name can be anything you like.
      coverpage: 'mycoverpage.md', // File name can be anything you like.
      themeColor: '#5e1cda',
      loadNavbar: 'navbar.md',
      loadSidebar: 'index.md', // This must be 'index.md' for markdown_github output.   
      subMaxLevel: 2,
      subMaxLevel: 1,
      executeScript: true,
      search: {
        paths: 'auto',
      },
     copyCode: {
       buttonText : 'Copy to clipboard',
       errorText  : 'Error',
       successText: 'Copied'
      },
      toc: {
        scope: '.markdown-section',
        headings: 'h1, h2, h3, h4, h5, h6',
        title: 'On this page',
      },
      plugins: [
      EditOnGithubPlugin.create('https://github.com/myGitHubAccName/myRepoName/blob/main/')
      ]
    }
  </script>
  <script src="https://unpkg.com/docsify/lib/docsify.min.js"></script>
  <script src="//unpkg.com/docsify/lib/plugins/search.min.js"></script>
  <script src="https://unpkg.com/docsify-toc@1.0.0/dist/toc.js"></script>
  <script src="https://unpkg.com/docsify-copy-code@2"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
</body>
</html>
```

See the [Docsify documentation](https://docsify.js.org/#/) for full configuration details.


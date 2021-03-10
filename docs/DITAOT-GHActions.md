# Building LwDITA with GitHub Actions

If you store your docs on GitHub and don't want to be bothered downloading and making local builds with the DITA-OT, you can use GitHub Actions to build them for you. The following is Gihub Actions workflow that installs the latest DITA-OT, builds the content of *myProduct.ditamap* in my `main` branch in GitHub-flavored Markdown, and then deploys the output files to the */docs* folder on my `site` branch.

```
# site build workflow

name: site-build

# Controls when the action will run. 
on:
  # Triggers the workflow on push or pull request events but only for the main branch
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

  
jobs:
 build-dita:
    name: Build-DITA
    runs-on: ubuntu-latest
    steps:
      - name: Git checkout
        uses: actions/checkout@v2
      - name: Build Gitbook
        id: DITA-build
        uses: jason-fox/dita-build-action@master
        with:
          build: dita -i myProduct.ditamap -f markdown_github -o out
      - name: Upload DITA
        id: upload
        uses: actions/upload-artifact@v2
        with:
          name: dita-artifact
          path: 'out'    
      - name: Deploy
        id: deploy
        uses: JamesIves/github-pages-deploy-action@4.0.0
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          BRANCH: site # The branch the action should deploy to.
          FOLDER: out # The folder the action should deploy.
          TARGET-FOLDER: docs
          CLEAN: false
```

The workflow is set to to kick-off when any content is pushed, or any pull requests are merged, to the `main` branch.

The build job itself has 4 distinct steps:

1.  First,the `main` branch is checked out.

2.  Next, Jason Fox's [dita-build-action](https://github.com/jason-fox/dita-build-action), downloads and installs the latest version of the DITA-OT and runs the `dita` build command specified.

3.  The Upload DItA step uses the upload-artifact action which takes the output files and uploads them to a temporary folder called *out*.

4.  Finally James Ives' [github-pages-deploy](https://github.com/marketplace/actions/deploy-to-github-pages) action copies the contents of the *out* folder to the *docs* folder on the `site` branch.


The `site` branch could contain static site generator files and be published to Github Pages or be used as the source for a webhook to publish the content on a hosting site like AWS or Netlify.


# Template Quarto Revealjs site

This template can be used to publish a [RevealJS](https://revealjs.com/) website that has been written in
[Quarto](https://www.quarto.org). It includes a [GitHub Action](https://docs.github.com/en/actions) which will convert
the Quarto source to HTML and publish them via [GitHub Pages](https://pages.github.com/).

Its a useful way of making slides portable as they are then available via the URL and naturally the slides are version
controlled.

## Usage

### Use the Template

Start by clicking on the "_Use this Template_" button and selecting "_Create a new repository_". You will have to choose
a name for the repository. When ready click on "_Create repository from template_" and this will copy all the resources
into a new repository under your GitHub account ready for you to start using. You will probably want to clone the
repository locally to do so.

### Edit `_quarto.yaml`

You will have to edit `_quarto.yaml` and change the `site-url` to reflect your GitHub user account and the name of the
repository you have chosen for this project. Its probably wise to modify the `title` and `description` too. The sample
code below shows in capitals the fields you should modify.

``` yaml
project:
  type: website

website:
  title: "<INSERT_TITLE>"
  site-url: https://<YOUR_GITHUB_USERNAME>.github.io/<NAME_OF_REPOSITORY>
  description: "<INSERT_DESCRIPTION>"
```

### Publish Locally

You will need to run `quarto publish gh-pages` once locally before deploying this template.

### Repository settings

You will also need to make sure your repository action settings are configured to allow read and write permissions.

![image](https://user-images.githubusercontent.com/20887250/216280796-86028c95-76b7-418a-a3eb-e614a8ab874a.png)

You can find this settings at `https://github.com/[USER]/[repo]/settings/actions`

### Write your slides

You are now ready to create your slides by editing the `index.qmd` in the root of the repository. For more information
on writing RevealJS slides in Quarto see the [RevealJS](https://quarto.org/docs/presentations/revealjs/) guide and the
[Revealjs Reference](https://quarto.org/docs/reference/formats/presentations/revealjs.html).

### pre-commit

A [pre-commit](https://pre-commit.com) configuration is included (see `.pre-commit-config.yaml`) and includes a hook for
[markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) (see `.markdownlint-cli2.yaml` for
configuration). To use `pre-commit` you will have to install `pre-commit` in your cloned repository. This requires
`pre-commit` to be installed on your system or within a Python Virtual Environment. To find out more about installing
and configuring `pre-commit` see the article [pre-commit : Protecting your future
self](https://rse.shef.ac.uk/blog/pre-commit/) or refer to the official documentation.

## Extensions

There is a growing number of useful [Quarto extensions](https://quarto.org/docs/extensions/). These are installed as
part of the `publish.yml` action that is included in the template to publish the slides via GitHub pages but to use and
render them locally when developing the slides you will have to install them.

``` bash
quarto install extension jmbuhr/quarto-qrcode
quarto install extension grantmcdermott/quarto-revealjs-clean
```

### QR Code generation

The [quarto-qrcode](https://github.com/jmbuhr/quarto-qrcode) extension is particularly useful as it simplifies
generating and embedding [QR Codes](https://en.wikipedia.org/wiki/QR_code) that link to websites in your slides.

### Clean Theme

The [quarto-revealjs-clean](https://github.com/grantmcdermott/quarto-revealjs-clean/) theme is a nice (clean!)
theme. For a full example of all the features of this theme see the authors
[quarto-revealjs-clean-demo](https://github.com/grantmcdermott/quarto-revealjs-clean-demo).

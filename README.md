# Template Quarto Revealjs site

This template can be used to publish a [RevealJS](https://revealjs.com/) website that has been written in
[Quarto](https://www.quarto.org). It includes a [GitHub Action](https://docs.github.com/en/actions) which will convert
the Quarto source to HTML and publish them via [GitHub Pages](https://pages.github.com/).

Its a useful way of making slides portable as they are then available via the URL and naturally the slides are version
controlled.

## Usage

### Use the Template

Start by clicking on the "_Use this Template_" button and selecting "_Create a new repository_". You will have to choose
a name for the repository and this should reflect the nature of your talk. When ready click on "_Create repository from
template_" and this will copy all the resources into a new repository under your GitHub account ready for you to start
using.

### Repository settings

You **MUST** make sure your repository action settings are configured to allow read and write permissions.

![image](https://user-images.githubusercontent.com/20887250/216280796-86028c95-76b7-418a-a3eb-e614a8ab874a.png)

You can find this settings at `https://github.com/[USER]/[repo]/settings/actions`.

### Clone the repository

Typically you will work on files on your local computer, staging and committing changes and periodically pushing to
GitHub for backup and publishing. How you clone depends on what client you use but at the command line you can use...

``` bash
git clone https://github.com/<USERNAME>/<REPOSITORY>
```

Substitute `<USERNAME>` and `<REPOSITORY>` appropriately.

### Edit `_quarto.yaml`

How you should edit `_quarto.yaml` and change the `site-url` to reflect your GitHub user account and the name of the
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

### Install Extensions

This template uses some [extensions](https://quarto.org/docs/extensions/)
([quarto-clean](https://github.com/grantmcdermott/quarto-revealjs-clean), [QR
extension](https://github.com/jmbuhr/quarto-qrcode), [confetti](https://github.com/ArthurData/quarto-confetti)),
[openlinksinnewpage](https://github.com/davidwilby/openlinksinnewpage) and [reveal-header](https://github.com/shafayetShafee/reveal-header)
these need to be installed locally _before_ you can proceed.

``` bash
quarto add --no-prompt jmbuhr/quarto-qrcode
quarto add --no-prompt grantmcdermott/quarto-revealjs-clean
quarto add --no-prompt ArthurData/quarto-confetti
quarto add --no-prompt davidwilby/openlinksinnewpage
quarto add --no-prompt shafayetShafee/reveal-header
```

### Publish Locally

You will need to run `quarto publish gh-pages` once locally before deploying this template. This creates a new branch
`gh-pages` which is where the resulting pages are published to and pushes them to GitHub.

``` bash
quarto publish gh-pages
```

### Write your slides

You are now ready to create your slides by editing the `index.qmd` in the root of the repository. For more information
on writing RevealJS slides in Quarto see the [RevealJS](https://quarto.org/docs/presentations/revealjs/) guide and the
[Revealjs Reference](https://quarto.org/docs/reference/formats/presentations/revealjs.html).

When you stage, commit and push your commits to GitHub the `quarto-publish.yaml` will run.

## pre-commit

A [pre-commit](https://pre-commit.com) configuration is included (see `.pre-commit-config.yaml`) and includes a hook for
[markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) (see `.markdownlint-cli2.yaml` for
configuration). To use `pre-commit` you will have to install `pre-commit install` in your cloned repository. This requires
`pre-commit` to be installed on your system or within a Python Virtual Environment. To find out more about installing
and configuring `pre-commit` see the article [pre-commit : Protecting your future
self](https://rse.shef.ac.uk/blog/pre-commit/) or refer to the official documentation.

## Extensions

There are a growing number of useful [Quarto extensions](https://quarto.org/docs/extensions/). Five are included in this
template and they are also installed during the publishing and deployment of the resulting slides as they are listed in
the `quarto-publish.yml` under the `Install Quarto Extensions` step. You should have installed these locally as
instructed above.

If you use additional extensions then as well as installing them locally on your computer you **MUST** remember to add
them to the `Install Quarto Extensions` section of `.github/workflows/quarto-publish.yaml` otherwise your pages will not
build and deploy.

### QR Code generation

The [quarto-qrcode](https://github.com/jmbuhr/quarto-qrcode) extension is particularly useful as it simplifies
generating and embedding [QR Codes](https://en.wikipedia.org/wiki/QR_code) that link to websites in your slides.

### Clean Theme

The [quarto-revealjs-clean](https://github.com/grantmcdermott/quarto-revealjs-clean/) theme is a nice (clean!)
theme. For a full example of all the features of this theme see the authors
[quarto-revealjs-clean-demo](https://github.com/grantmcdermott/quarto-revealjs-clean-demo).

### Confetti

The [confetti](https://github.com/ArthurData/quarto-confetti) extension adds some eye-candy and throws confetti over
your slides whenever you press the `c` button. They originate from the mouse location and therefore follow it around.

### Open Links In New Page

The [openlinksinnewpage](https://github.com/davidwilby/openlinksinnewpage) extension does what it says on the tin and
ensures that when you click on a link in the resulting slides it will open a new tab/page (this saves you and others who
may not know of the shortcut from having to hold down `Ctrl` to achieve the same effect).

### Reveal Header

The [reveal-header](https://github.com/shafayetShafee/reveal-header) extension allows you to add headers as well as
footers to all slides. This template includes a simple text `header:`  nested under the `format: <theme>:` YAML header
in `index.qmd`. Please refer to the [documetation](https://github.com/shafayetShafee/reveal-header) for further
customisation such as adding a `header-logo` and other options available with this extension.

## Embedding Code

The beauty of Quarto is that it is a literate programming system which means you can embed code that is executed and the
results, whether that is tables, figures, or numbers, can be included in the resulting document. Quarto supports several
languages including perhaps the two of the most popular languages [R](https://www.r-project.org) and
[Python](https://www.python.org).

### R

You will likely have [R](https://www.r-project.org) installed locally along with all the packages that are required (and
perhaps even use reproducible environments using [renv](https://rstudio.github.io/renv/) or
[pak](https://pak.r-lib.org)).

For slides to build and execute your R code correctly you need to enable installation of R and the required packages in
the `.github/workflows/quarto-publish.yaml`. A sample section is already present that should just need un-commenting,
but may need tweaking if you use any packages to manage a reproducible environment.

### Python

Similarly with Python you likely have Virtual Environments configured locally to run your Python code, and these should
have be detailed in a `requirements.txt` file so they can be installed when the GitHub Workflow is executed to build
your pages on GitHub.

You will need to enable installation of Python and these packages in the `.github/workflows/quarto-publish.yaml` and
a sample section is already present that can be un-commented if required.

{% include head.html %}

# Creating a website for a repository using gh-pages

Each repository can have a website associated with it using GitHub's [gh-pages](https://pages.github.com/). This allows for websites to easily be built using Markdown. The gh-pages website lives in a separate root branch of the repository. This can be setup via:

```
$ git checkout --orphan gh-pages
# preview files to be deleted
$ git rm -rf --dry-run .
# actually delete the files
$ git rm -rf .
```

You will then need to copy `_config.yml`, `_includes/head.html`, `_layouts/default.html` and `assets/css/style.scss` from the main [BHPToolkit website repository](https://github.com/BlackHolePerturbationToolkit/blackholeperturbationtoolkit.github.io). Next create `index.md`, commit and push. Each `.md` file should contain the following at the start:

```
---
layout: default
title: Black Hole Perturbation Toolkit
---
```

## Adding the 'Get the code!' button

In order to add the get the code button to a repository's webpage add the following at the top of the page:

```
<p>
 <h1 style="display:inline">Package Name</h1> <span style="float:right;"><a href="{{ site.github.repository_url }}" class = "code_btn">Get the code!</a></span>
</p>
```


## Enabling MathJax

The BHPToolkit gh-pages is setup to use [MathJax](https://www.mathjax.org/). To enable this on a particular page put

```
{% raw  %}{% include head.html %}{% endraw  %}
```
at the top of the page (but after the layout information). With this you can include equations in the page by placing LaTeX between dollar signs. e.g., $a^2 + b^2 = c^2$.


## Previewing gh-pages locally

If you want to test changes to the gh-pages website before pushing them install Jekyll, navigate to the directory containing the site and execute `bundle exec jekyll serve`. You can now view the site at [http://localhost:4000](http://localhost:4000).

With Jekyll running locally every time you make a change to the source the site is regenerated. Once you are happy with the changes you can push them to the repository (note, the local Jekyll server will create an _sites directory that should not be added to the repository).

## Pushing your new gh-pages branch

In order to push your new website execute the command
```
git push origin gh-pages
```
## General Guide

MkDocs, which is used to build this wiki, is a lightweight static site generator. You can write contents in markdown and publish easily to Github. The [official user guide](http://www.mkdocs.org/) should be sufficient for learning its usage. 

The following is a summary of the most frequently used commands.

### 1. Install MkDocs

Install Python and its package management tool "pip" if you haven't.

```
$ sudo apt-get install python-pip python-dev
```

Then install MkDcos.

```
$ sudo -H pip install mkdocs
```

In case you get the error saying mkdocs cannot be found, add the following line to your "~/.bashrc"

```
export PYTHONPATH="${PYTHONPATH}/usr/local/lib/python2.7/site-packages:/usr/lib/python2.7/site-packages"
```

Don't forget to source "~/.bashrc" after you make the modification.

```
$ source ~/.bashrc
```

### 2. Edit page

You can create pages in the "docs" folder using markdown.

Some useful reference for using markdown:

* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
* [Basic Writing and Formatting Syntax](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
* [Markdown Tutorial](https://github.com/LewisVo/Markdown-Tutorial)  

After creating a page, you need to add it to "index.md" and "mkdocs.yml" so that it will be indexed and displayed properly. Just open these two files and refer to the format of other entries.

### 3. Build and Preview

Use the command to build pages

```
$ cd <location-of-acel-wiki-folder>
$ mkdocs build
```

You can preview the pages locally before pushing to Github.

```
$ mkdocs serve
```

Open your browser and type "http://127.0.0.1:8000/" to view the locally hosted site.

### 3. Deploy static site

When you are ready, push the generated site to Github.

```
$ mkdocs gh-deploy
```

After this command, the folder "site", which contains the generated HTML pages, will be pushed to the "gh-pages" branch of the wiki repository. "gh-pages" is the default branch that Github will treat as a project site and host automatically.

Don't forget to also push the "source files" used to generate the site, usually "*.md" files and images.

```
$ <create-a-git-comit>
$ git push origin acel-wiki
```

**Note**: Ask for access if you could not push to the repository.
---
title: Editing the Wiki
layout: page
categories: help
description: This page explains how to write and edit pages.
---

# Getting started

Creating or editing a page on GitHub pages is super easy! Pages can be created or modified online via GitHub's online file editor (clicking "Edit page" on the top right of this page will bring you to this specific page's source) or, for advanced users, via a local installation of jekyll and the imagej.github.io site. (See our advanced user guide for jekyll set-up instructions)

If you do not need to create a new page and would like to make changes to an existing page, skip to [adding and editing page content](Editing_the_Wiki#adding-and-editing-page-content).

## Creating a new page
<br>

{% include image-right name="create-page" image_path="/images/readme/create-page-etw.png" %}

<br>

1. Navigate to the [_pages section](https://github.com/imagej/imagej.github.io/tree/master/_pages) of the `imagej.github.io` repository.
Click `Add file` then  `Create new file` from the drop-down.

2. Add a name for your file. **Note: this is not the page title;** the page title will be applied in the next section, front matter. File names should be lowercase, avoid symbols, and contain no spaces (use underscores or dashes instead, `_` `-`).

{% include image-right name="name-your-file" image_path="/images/readme/name-your-file.png" classes="grey-border" %}

## Add the page's *front matter*
The *front matter* precedes the content of your page, and sets several parameters that help setup your page within the repository. Without the front matter, your page will not render correctly.

**title:** The title of your page.\
**layout:** This sets the page's layout. Always use setting `page`.\
**categories:** Categories that your page falls into, [see a list of imagej.github.io categories.](/search?query=categories) (These are the only categories recognized be the site)\
**description:** A short description of your page. Also used for the site's search engine.

Find below the front matter for this page. You can copy and paste this code into the editor of a new page from lines 1-6. Replace the settings in the `title`, `categories`, and `description` fields with details from the new page. **Do not change the `layout: page` setting.**

```
---
title: Editing the Wiki
layout: page
categories: demo, help
description: This page explains how to write and edit pages.
---
```

## Adding and editing page *content*
Pages on `imagej.github.io` are optimized to be written in git markdown, but will also read `html` formatting. This section will cover how to populate the *content* of your page, including: links to GitHub markdown resources, as well as guides on how to use this site's includes.



#### Markdown
Markdown is plain-text syntax formatting, allowing a user to easily and cleanly modify text with italics, bold, ordered or bulleted lists, etc. As a GitHub pages hosted website, imagej.github.io uses the `git` flavor of markdown. [A basic Git markdown guide can be found here.](https://guides.github.com/features/mastering-markdown/)

#### Using includes
Includes provide more robust formatting options and are unique to this site. With includes, you can insert menus, images, tables, sideboxes, figures, math, warnings, etc with pre-formatted settings into a page. For a full list of includes with utilization instructions, [see below](Editing_the_Wiki#available-includes).

#### Available "includes"

| Action | Link to demo page|
| : --- : | :---: |
| Insert the about menu | [about-menu]({{"/demo-about-menu" | relative_url}})
| Insert a citation | [citation]({{"/demo-citation" | relative_url}})
| Insert conference info | [conference]({{"/demo-conference" | relative_url}})
| Generate info/details box | [details-box]({{"/demo-details-box" | relative_url}}) |
| Alternative info/details boxes | [alt-boxes]({{"/demo-additional-info-boxes" | relative_url}}) |
| Insert figure | [figure]({{"/demo-figure" | relative_url}}) |
| Insert a gallery | [gallery]({{"/demo-gallery" | relative_url}}) |
| Link to github files | [github]({{"/demo-github" | relative_url}}) |
| Insert Git menu | [git-menu]({{"/demo-git-menu" | relative_url}}) |
| Insert images | [image]({{"/demo-image" | relative_url}}) |
| Insert a notice | [info-box]({{"/demo-info-box" | relative_url}})
| Insert logos | [logo]({{"/demo-logo" | relative_url}}) |
| Insert menu breadcrumb | [menu-bc]({{"/demo-menu-breadcrumb" | relative_url}}) |
| Insert math | [math]({{"/demo-math" | relative_url}}) |
| Insert person details | [person]({{"/demo-person" | relative_url}})
| Insert a sidebox | [sidebox]({{"/demo-sidebox" | relative_url}})
| Insert the SNT nav bar | [SNT-nav]({{"/demo-SNT-nav" | relative_url}})|
| Insert a symbol | [symbol]({{"/demo-symbols" | relative_url}})
| Insert a table | [markdown-table]({{"/demo-markdown-table" | relative_url}})
| Insert a todo list | [todo-list]({{"/demo-todo-list" | relative_url}})
| Insert a tech box | [tech-box]({{"/demo-tech-box" | relative_url}})
| Insert a warning | [warning-box]({{"/demo-warning-box" | relative_url}}) |
| Insert a YouTube video | [youtube-video]({{"/demo-youtube-video" | relative_url}}) |


# Syntax highlighting

Java example:

```java
Image3DUniverse univ = new Image3DUniverse();
univ.show();
univ.addMesh(yourImagePlus, null, "somename", 50, new boolean[] {true, true, true}, 2);
...
```

Python example:

```python
def update_progress(progress):
    barLength = 10 # Modify this to change the length of the progress bar
    status = ""
    if isinstance(progress, int):
        progress = float(progress)
    if not isinstance(progress, float):
        progress = 0
        status = "error: progress var must be float\r\n"
    if progress < 0:
        progress = 0
        status = "Halt...\r\n"
    if progress >= 1:
        progress = 1
        status = "Done...\r\n"
    block = int(round(barLength*progress))
    text = "\rPercent complete: [{0}] {1}% {2}".format( "#"*block + "-"*(barLength-block), progress*100, status)
    sys.stdout.write(text)
    sys.stdout.flush()
```
# Advanced editing with jekyll

## Install jekyll
The jekyll static site generator can be installed on Linux, MacOS and Windows. To install a local version of jekyll follow the instructions for your respective operating system [here](https://jekyllrb.com/docs/installation/).

## Clone the `imagej.github.io` repository
Once jekyll has been installed, [clone](https://docs.github.com/en/enterprise/2.13/user/articles/cloning-a-repository) the the imagej.github.io repository. Navigate to the cloned repository and run `bundle install` to install the specific gems used in imagej.github.io. Once this is complete, it is a good idea to run `bundle update`.

## Serve a local version of imagej.github.io
Now that the both jekyll and the repository are installed on your local machine, you can run the static site generator by navigating to the directory imagej.github.io withing a terminal was saved and running `bundle exec jekyll serve`. Wait for a minute or two while it generates, and then in your browser navigate to `http://127.0.0.1:4000`. Changes you make to any file in the directory will be detected by jekyll, regenerating the site to reflect the new changes.

Alternatively, you can run `bundle exec jekyll serve --incremental` to initiate the local server. This command will reduce the amount of time it takes for the site to regenerate if you anticipate making many changes in quick succession.

## Create a new page in `_pages`

In `/path/to/imagej.github.io/_pages`, create a new text file i.e. `cat > your_page_name.md`.

<br>

NOTE: filenames should be lowercase, omit spaces, and use extension `.md`.

From here, the [front matter](Editing_the_Wiki#add-the-pages-front-matter) and content of the new page can be populated with a text editor of your choosing.

* Images and other media should be stored in `/path/to/imagej.github.io/media`.

* Regularly save your progress with `git add` i.e. if within the `imagej.github.io` working directory, use command `git add _pages/your-page-name.md`

## Pushing, pulling, and maintaining with Git

Once you are ready to publish your your new page you will need to add, commit, and push your changes to the repository. These steps should looks something like:

1. `git add path/to/your-page-name.md`
2. `git commit path/to/your-page-name.md` Note: you will not be prompted to enter a commit message. Our lab uses imperative tense, i.e. "Add new page xzy"
3. `git push` Your new page or edits will not be pushed to the master branch of the repository.

[This guide](https://rogerdudler.github.io/git-guide/) provides further explanations on the above steps, as well as how to keep your local repository up-to-date with the master with `git pull`.

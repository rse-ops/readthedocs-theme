---
substitutions:
  rarr: |-
    ```{eval-rst}
    .. unicode:: U+2192 .. RIGHTWARDS ARROW
    ```
---

# Contributing a documentation change

This tutorial will take you through the process of:

- Downloading the current documentation
- Installing required libraries
- Building and previewing the documentation
- Creating a new git branch
- Making a change to the documentation
- Committing the changes and making a pull request

## Download the documentation

1. Sign up to [GitHub](https://github.com) and [fork the project](https://github.com/rse-ops/readthedocs-theme/fork)

2. Install [Git](https://git-scm.com/downloads). If you're new to Git, the Django project has a good introduction on [working with Git and GitHub](https://docs.djangoproject.com/en/3.0/internals/contributing/writing-code/working-with-git/). You can also take a look at the [GitHub branch-based workflow](https://guides.github.com/introduction/flow/)

3. Using the command line, `cd` to the directory where you want your local copy of the software to live. The documentation can then be downloaded
   using:

   ```bash
   $ git clone https://github.com/YourUsername/readthedocs-theme.git
   ```

4. (Optional) We recommend that you install your development copy of the software
   in a virtual environment.

   ```bash
   $ python -m venv env
   ```

5. Install the cloned copy of the software (`-e` for editable or development mode):

   ```bash
   $ pip install -e project/
   ```

## Install required libraries

```bash
$ pip install -r requirements.txt
```

## Build and preview the documentation

To build the documentation locally, navigate to the `docs` directory and
run `make html`:

```bash
$ cd docs/
$ make html
```

Occasionally you may need to clean up the generated files before a change
gets applied:

```bash
$ make clean && make html
```

The HTML generated by the build can be viewed by opening
`_build/html/index.html` in a web browser or by doing:

```
$ cd _build/html
$ python -m http.server 9999
```

And then going to <http://localhost:9999>

## Create a new branch

Create a new branch `my-changes` for your changes (you can choose any name
that you want instead). Any changes made in this branch will be specific to
it and won't affect the main copy (the `main` branch) of
the documentation:

```bash
$ git checkout -b my-changes
```

## Make a change to the documentation

At this point you can make a change to a markdown or rst file in the docs!
Let's say we add `reading.md` to the tutorials folder.
When you add this new page, make sure that it appears on a toc tree somewhere.
If not, you'll see:

```text
checking consistency... [/path/to]/readthedocs-theme/docs/tutorials/reading.md: WARNING: document isn't included in any toctree
```

Make sure to preview the docs, as shown above, to see that the page is visible.
Here is how to include a new page in the docs. Let's say that we are adding
the reading.rst file to the tutorials folder. You'dd add it to 
`tutorials/index.md`, as follows:

```
.. toctree::
   :maxdepth: 1

   installation
   contributing_code
   contributing_docs
   reading
```

If you rebuild the HTML you should find that the warning is gone and that
your new page is reachable from the main documentation page. You have the choice
to write markdown or rst. If you need help with the reST markup then you can
check out Sphinx's [reStructuredText primer](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html?highlight=re)

There are also a number of directives that tell Sphinx to do certain things
(like inserting code blocks or a table of contents). Sphinx has a list of
these [here](https://www.sphinx-doc.org/en/master/usage/restructuredtext/directives.html).

For more information on writing documentation see
{doc}`writing documentation</guides/writing_documentation>`.

Just like before, you should build and preview the updated page. When you're
happy with the results move on to the next section.

## Commit your changes and make a pull request

First we add our new file to git:

```bash
$ git add tutorials/reading.md
```

And then stage the remaining changes (`-a`) and commit at the same time:

```
$ git commit -am "Add new reading.md on <x>"
```

After committing the changes, send them to your fork:

```bash
$ git push origin my-changes
```

You can create a pull request by visiting the [project GitHub page](https://github.com/rse-ops/readthedocs-theme) where you
should see your branch under *"Your recently push branches"*. Click *"Compare &
pull request"* and fill out the title (with a `[WIP]` prefix, i.e.
`[WIP] Add new reading example for <x>`) and follow the
instructions in the main entry window. At this point your code will be tested via
continuous integration. If you set up Artifacts preview (e.g., CircleCI)
then you should be able to click on the Artifacts tab in the CircleCI interface
and click any html file to preview.

## What happens next?

One or more reviewers would look at your pull request and may make suggestions,
ask for clarification or request changes. Once the reviewers were happy,
the pull request would be approved and your changes merged into the
`main` branch.
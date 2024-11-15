# Contribute

We love contributions! This analysis guide is open source, built on open source, and we'd love to have you help make it even better!

First off, if directly writing content in this repository is too unfamiliar and you just want to write what you know down, we will be happy to accept contributions in any form.
Our preferences would be for something which is as close to [markdown](https://www.markdownguide.org/) as you are comfortable writing, so if not markdown then plain text, LaTeX, or lightly formatted word documents are all ok (in that order of preference).

If you are happy to contribute directly to the source on GitHub then thank you!
We have tried to make it as approachable as possible, but if you encounter any issues then please let us know.

## Getting Started

The first step is to sign up / sign into GitHub.

The next step is to fork the repository to your own GitHub account, to do this go to https://github.com/DKISTDC/proposing-docs/fork.

Then, you clone the repository to your local machine. First make sure you have [generated an SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [added it to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

To clone the repository run:

```console
$ git clone git@github.com:<your github username here>/proposing-docs.git
```

setting your github username as required.

Next we want to add the upstream DKISTDC repository to your local clone:

```console
$ git remote add upstream git@github.com:DKISTDC/proposing-docs.git
```

Then we can update the remotes with:

```console
$ git remote update
```

This should set you up with a local copy of the files to edit.

### Creating a Python Environment

#### Using conda (recommended)

If you don't already have conda installed you can follow the instructions here for [installing miniforge](https://docs.dkist.nso.edu/projects/python-tools/en/stable/installation.html#installing-miniforge).

If you already have conda installed you need to create a new environment for the analysis guide and then install the requirements:

```console
$ conda create -n proposing-docs -c conda-forge python unidep
$ conda activate proposing-docs
$ unidep install .
```

When coming back to work on the analysis guide make sure you run `conda activate proposing-docs` to activate the environment.


#### Using pip

If you are using pip, please create an isolated virtual environment and then run:

```console
$ pip install 'unidep[all]'
$ unidep install --skip-conda .
```

## Authoring Content

### Building the guide

The easiest way to preview the guide as you are working on it is to run:

```console
$ jupyter-book build analysis-guide
```

The end of this command should print a file path for you to open in your web browser.

### Editing Files

The guide is written in a markup language called [MyST](https://mystmd.org) which is an extension to [markdown](https://www.markdownguide.org/).
Each chapter has it's own file which are built into a variety of possible output formats by jupyter book.
The chapters of the book are defined in the `_toc.yml` file, more information about the structure of the guide can be found in the [jupyter book](https://jupyterbook.org/en/stable/basics/organize.html) documentation.

#### Adding Chapters

To start a new chaper, create a new markdown file (`.md`) and then add the filename to the `_tox.yml` file.

#### Style

When writing content in the markdown files, please write one sentence per line as this helps when using git.


## Submitting your changes

Once you have edited the guide and want to submit your changes, you will need to make a [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork).
To do you this you need to:

* Locally commit your files to git.
* Push these commits to your fork on GitHub.
* Open a Pull Request.

The first step is to create a new local branch with git:

```console
$ git switch -c <branch name>
```

replace `<branch name>` with a name for your branch such as "intro-improvements".

Then we will add and commit all the changes:

```console
$ git add .
$ git commit -m "<some commit message>"
```

replace `<some commit message>` with a short descriptive message such as "fixed typos in intro page".

Next we need to push these changes to your fork on GitHub which we setup at the start of the guide:

```console
$ git push origin <branch name> --set-upstream
```

again, replacing branch name with the name of the branch you used earlier.
The output of this command should give you a shortcut link to open a pull request from this branch, but if not you can navigate to `https://github.com/<your github user name here>/proposing-docs/pull/new/<branch name>` replacing your GitHub username and branch name as needed.
Type a descriptive title and a short description and then click "Create Pull Request".
This will then run some automatic tests and notify people to review your contribution.

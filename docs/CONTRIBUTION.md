# Contribution

## Table of Contents

- [Local Development Environment](#local-development-environment)
  - [Python](#python)
  - [Visual Studio Code](#visual-studio-code)
- [Contribution Process](#contribution-process)
  - [Creating a Fork](#creating-a-fork)
  - [Clone the Repository](#clone-the-repository)
  - [Creating a Topic Branch](#creating-a-topic-branch)
  - [Local Development](#local-development)
  - [Submitting a Pull Request](#submitting-a-pull-request)
- [Commit Guidelines](#commit-guidelines)
  - [Conventional Commits](#conventional-commits)
- [Coding Guidelines](#coding-guidelines)
  - [Python](#python-1)
  - [Markdown](#markdown)
  - [YAML](#yaml)

<br />

## Local Development Environment

This section outlines the necessary steps to configure your machine with the necessary tools and dependencies for contributing to this project. Please follow the steps carefully and ensure that all required tools work as intended.

### Python

This project uses [Python 3](https://www.python.org/). Follow the [installation instructions in the Python wiki](https://wiki.python.org/moin/BeginnersGuide/Download) to install it on your machine.

In addition to Python3 itself, you'll also have to install some additional Python packages to run the code. Install them by running the following command from within the project's `/src` directory.

```sh
pip3 install -r requirements.txt
```

### Visual Studio Code

VS Code is the recommended editor for this project. If you prefer using other editors, please make sure the settings regarding formatting and linting match those provided for VS Code.

#### Workspace Settings

VS Code automatically applies the workspace settings from [`/.vscode/settings.json`](/.vscode/settings.json) when you open the project. The settings take precedence over your local user settings and serve to maintain the [Coding Guidelines](#coding-guidelines). VS Code will automatically apply formatting rules whenever you save a file.

#### Extensions

The following extensions are recommended to aid in working on this project. VS Code should prompt you to install them the first time you open the repository.  If you want to manage their installation manually, select the extensions tab on the left hand side in VS Code and search for `@recommended`.

- [**autopep8**](https://marketplace.visualstudio.com/items?itemName=ms-python.autopep8)  
Formatting support for Python files using the [autopep8 formatter](https://pypi.org/project/autopep8/).
- [**markdownlint**](https://marketplace.visualstudio.com/items?itemName=davidanson.vscode-markdownlint)  
Markdown linting and style checking for Visual Studio Code
- [**Python Debugger**](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)  
Python Debugger extension using debugpy.
- [**Pylance**](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)  
A performant, feature-rich language server for Python in VS Code
- [**Python**](https://marketplace.visualstudio.com/items?itemName=ms-python.python)  
Python language support with extension access points for IntelliSense (Pylance), Debugging (Python Debugger), linting, formatting, refactoring, unit tests, and more.
- [**Better Jinja**](https://marketplace.visualstudio.com/items?itemName=samuelcolvin.jinjahtml)  
Syntax highlighting for jinja(2) including HTML, Markdown, YAML, Ruby and LaTeX templates

<br />

## Contribution Process

This section outlines the key steps for contributing code, from forking the repository to submitting a pull request and having it undergo a review. Understanding and following these guidelines ensures that contributions are consistent, high-quality, and seamlessly integrated into the project.

We use **trunk based development with topic branches** (also known as Github flow).

### Clone the Repository

> [!NOTE]  
> Work in progress

### Creating a Fork

If you do not have the necessary permissions to create branches in the main repository, you will have to create a fork. A fork is a clone of the repository under your own username. You will push your work to your fork instead of the main repository. The overall contribution process will remain mostly unchanged.

1. Go to our [repository in Github](https://github.com/Cyclonit/docs-templates).
1. Click on the button `Fork` to the right of the repository's title.
1. Under `Owner` select yourself.
1. Update `Description` to your liking.
1. Check `Copy the main branch only` unless you want a copy of all active branches.
1. Finish by clicking on `Create fork`.
1. Add your fork as a remote for your local clone of the repository. Go to your clone's root directory and run the following command.

    ```sh
    git remote remote add fork https://github.com/<your username>/docs-templates.git
    ```

1. Verify that your repository's remotes are set up correctly. The output of the command `git remove -v` should show the main repository as `origin` and your fork as `fork`.

    ```sh
    git remote -v
    > origin https://github.com/Cyclonit/docs-templates (fetch)
    > origin https://github.com/Cyclonit/docs-templates (push)
    > fork https://github.com/<your username>/docs-templates (fetch)
    > fork https://github.com/<your username>/docs-templates (push)
    ```

### Creating a Topic Branch

Topic branches are short lived branches used to allow work on multiple features in parallel. Instead committing directly to `main`, all work is done on topic branches. You may add as many commits as necessary on your branch. Once you are finished, your topic branch will be merged into `main` via a `pull request`.

#### Naming Scheme

```txt
<type>/<issue id>_<name>
```

We use [Conventional Commit types](#types) as topics. Every topic branch **must** be related to an issue and contain it's id in its name. Then follows the branch's actual name. It **should** reflect that of the issue, but may differ if the issue's title is too long, contains special characters or is otherwise unsuitable. Branch names cannot contain spaces, thus all spaces **must** be replaced with underscores (`_`).

#### Examples

- > feature/#42_answer_the_question
- > fix/#43_ask_the_right_question

#### How-To

1. Make sure you are on the branch `main` and that it is up to date with respect to our repository.

    ```sh
    git switch main
    git pull origin main
    ```

1. Create a new topic branch using the naming scheme defined above.  

    ```sh
    git branch '<type>[(<scope>)]/<issue>_<name>'
    ```

### Local Development

> [!NOTE]  
> Work in progress

#### Committing

When committing changes, make sure to follow our [commit guidelines](#commit-guidelines).

#### Running Tests Locally

> [!NOTE]  
> Work in progress

### Submitting a Pull Request

#### Naming Scheme

```txt
<type> [(<scope>)] <issue id> <name>
```

Our naming scheme for pull requests is a more human readable analogue to the [branch naming scheme](#naming-scheme). The similarity serves to easily identify related branches and PRs. A branch may contain different types of commits (e.g. `feature` and `docs`). In this case, choose the primary type for the PR name.

#### Examples

- > Feature #42 answer the question
- > Fix #43 ask the right question

#### How-To

1. Make sure you committed all intended changes on your topic branch.
1. Rebase your changes onto the current state of `origin/main`. Rebasing simplifies the commit history by eliminating concurrent modifications in multiple branches.

    ```sh
    git switch main
    git pull origin main
    git rebase main <your topic branch>
    ```

1. Push your changes to Github. If you are working on a fork use the remote `fork`, otherwise use `origin`.

    ```sh
    git push <remote>
    ```

1. Create the pull request.  
   1. Go to our repository's [pull requests page](https://github.com/Cyclonit/docs-templates/pulls).
   1. Click on `New pull request` at the top right.
   1. Under `base` select or trunk `main`.
   1. If you are working on a fork, click on `compare across forks` and under `head repository` select your fork.
   1. Under `compare` select your topic branch.
   1. Click on `Create pull request`.
   1. Name the pull request according to our [naming scheme for pull requests](#naming-scheme-1) and fill out the description.
   1. Finish by clicking on `Create pull request`.

<br />

## Commit Guidelines

Our commit guidelines serve to maintain a clear and expressive version control history. They are intended to help developers create meaningful commit message and organize changes in a way that makes it easy for other team members to follow the evolution of the project. Addtionally, the commit history enables us to automate our changelog generation using [git-cliff](https://git-cliff.org/). See [LINK HERE](LINK HERE) for details.

### Conventional Commits

All commit messages **must** adhear to the [Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/). This serves to keep commit messages consistent and maintain a clean commit history. It also enables us to generate the project's changelog automatically (see [RELEASES.md#Changelog](./RELEASES.md#Changelog)).

```text
<type>[optional <scope>]: <issue> <description>

[optional body]

[optional footer(s)]
```

#### Types

We use the following **types** for commits. The list is loosely based on the [Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines). If neither of these types accurately cover all of the changes in your commit, consider splitting it into smaller commits. Changes of the types `docs` and `test` may be included in commits of other types for sake of brevity.

- **feature**  
a new feature
- **fix**  
a bug fix
- **chore**  
non-functional routine changes (example: updating dependencies)
- **docs**  
documentation only changes
- **refactor**  
a code change that neither fixes a bug nor adds a feature
- **ci**  
changes to CI configuration files and scripts
- **test**  
adding missing tests or correcting existing tests
- **revert**  
reverting some previous change

#### Scopes

We use the following **scopes** for commits. If neither scope suits the changes in a commit, consider defining a new scope and adding it to this list. You may ommit assigning a scope if the changes affect the entirety of the project.

- **README**  
changes affecting README.md
- **CONTRIBUTION**  
changes affecting CONTRIBUTION.md
- **RELEASING**  
changes affecting RELEASING.md
- **TESTING**  
changes affecting TESTING.md

#### Issues

Each commit should reference the issue it is related to in its header. Use Github's short link syntax `#<issue id>` instead of a full URL (e.g. `#42`).

#### Description

The `description` **must** be written in **imperative present tense** for consistency. You may use any suitable tense for the `body`.  
The `description` **must** start with a lower-case character or number.

#### Body

The `body` **should** contain a short summary of the changes, if the `description` and issues referenced therein are insufficient.

#### Examples

- > feature(CONTRIBUTION): #42 answer the question
- > fix(CONTRIBUTION): #43 ask the right question

<br />

## Coding Guidelines

By adhering to a well-defined set of standards, teams can ensure that their codebase is understandable and accessible to all members, regardless of when they join the project. These guidelines facilitate smoother collaboration, reduce the likelihood of errors, and streamline the onboarding process for new developers.

### Python

> [!NOTE]  
> Work in progress

- We use [autopep8](https://pypi.org/project/autopep8/) to format our code to conform to the [PEP 8 style guide](https://peps.python.org/pep-0008/).

### Markdown

- We use [markdownlint](https://marketplace.visualstudio.com/items?itemName=davidanson.vscode-markdownlint) to format all of our markdown. Refer to [.markdownlint.jsonc](/.markdownlint.jsonc) for our configuration.
- We use `<br />` to insert one additional line of whitespace before level 2 headings (except the first) to improve readability.
- When creating numbered lists, we use the index `1.` for all elements. This simplifies dynamically ommitting/adding elements in templates. Markdown renderers will automatically number the elements in a list correctly.

### YAML

- We use the file extension `.yml` for all YAML files.

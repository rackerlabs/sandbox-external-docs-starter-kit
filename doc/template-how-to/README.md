# How to create a how-to style site

This folder contains templates that you can use to create how-to style articles for your product. There are three types of articles that we recommend for a how-to site: task-based, conceptual, and troubleshooting. Each template describes how to structure your article and includes content examples.

## Before you begin

Before starting the work described in this document, read and perform the tasks in the following:

1. [Welcome to the docs starter kit repository (main README.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/README.md)

2. [How to use this repository (how-to-use-repository.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/how-to-use-repository.md)

3. [GitHub workflow (GITHUBING.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/GITHUBING.md)

4. [Contributor guidelines (CONTRIBUTING.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/CONTRIBUTING.md)

5. To set up internal publishing,
[Internal tools (README.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/tools-internal-repo/README.md)

6. To set up external publishing,
[External tools (README.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/tools-external-repo/README.md)

Having followed the instructions in the preceding files, you have performed the following tasks:

1. Decided what templates that you need to use.

2. Created a new repository in GitHub to house your new content. Generally, the repository is either in GitHub Enterprise for an internal (Rackers only) site, or in the rackerlabs organization in GitHub for an external (customer-facing) site.

3. Forked and cloned the [docs-starter-kit repo](https://github.rackspace.com/IX/docs-starter-kit). You now have a copy of the `docs-starter-kit` repo on your computer.

4. Forked and cloned your new doc repo. You now have a copy of your new doc repo on your computer.

5. On your computer, copied the `template-how-to` to your new doc repo as the `templates` folder.

6. Set up remotes so that you are ready to start creating changes for which you eventually create pull requests (PRs).

7. Set up your repository so that automatic builds and publishing occur.

## How-to template files

Copy the `template-how-to` folder and all the files it contains to the local copy of your new doc repo. This folder includes the following files:

- A `concept-based-article-template.md` file template for creating conceptual articles.
- A `task-based-article-template.md` file template for creating task-based articles.
- A `troubleshooting-article-template.md` file template for creating troubleshooting articles.

### Content structure

The content for a how-to site is developed in Markdown. Generally, how-to content is organized in a main `content` folder, with subfolders for each category of article that you want. If you want to include images in your articles, you must have an `_assets/img` folder, with subfolders to match the organization of your content folder.

For an example of how to organize your how-to content, see the [Rackspace How-To repository](https://github.com/rackerlabs/rackspace-how-to) or the [Rackspace Whitepapers repository](https://github.com/rackerlabs/rackspace-whitepapers).

### Support and feedback

We welcome feedback, comments, and bug reports. Follow the [contributor guidelines](https://github.rackspace.com/IX/docs-starter-kit/blob/master/CONTRIBUTING.md) to propose a source file change, or [submit a GitHub issue](https://github.rackspace.com/IX/docs-starter-kit/issues) to request an update or to provide feedback.

You can also contact the [Rackspace documentation team](mailto:infodev@rackspace.com) directly for general issues or questions about the content.

# Welcome to the docs-starter-kit repo!

**The docs-starter-kit is currently in beta.**

This repository (repo) contains templates and instructions to help you set
up your own documentation repo. This README provides instructions on how to
copy the repo, use it to create your own content, and publish that content.

## Getting started

Before you can create a documentation repo, you have to determine who your
audience is and what kind of content you need to produce for them.

1. Is your documentation for Rackers only, or is it customer facing?

   - If the content is for Rackers only, you should create an
     *internal* repo. Repos for internal content are in GitHub
     Enterprise at https://github.rackspace.com/IX/. Internal content
     is published on the [internal docs landing
     page](https://pages.github.rackspace.com/IX/internal-docs-landing-page/).

   - If the content is customer facing, you should create an
     *external* repo. Repos for external content are in GitHub at
     https://github.com/rackerlabs/. These repos generally have names
     that begin with docs (for example,
     https://github.com/rackerlabs/docs-cloud-load-balancers).
     External documentation is published on the [external docs landing
     page](https://developer.rackspace.com/docs/) or on the [Support
     site](https://support.rackspace.com/how-to/).

2. What type of documentation are you creating?

   - **API content**: The repo has
     [templates](https://github.rackspace.com/IX/docs-starter-kit/tree/master/template-api-guide)
     for API getting started and reference content. You create your
     repo with the Sphinx configuration files and write your
     documentation in RST.

   - **End-user content**: The repo has
     [templates](https://github.rackspace.com/IX/docs-starter-kit/tree/master/template-user-guide)
     for user guide content, including installation, getting started,
     configuration, use cases, and using a product or service. You
     create your repo with the Sphinx configuration files and write
     your documentation in RST.

   - **Support articles**: The repo has
     [templates](https://github.rackspace.com/IX/docs-starter-kit/tree/master/template-how-to)
     for creating stand-alone articles that are published on
     **support.rackspace.com**. You create your repo with the Jekyll
     configuration files and write your documentation in Markdown.

If you are unsure about what kind of content you need to create,
contact the [Information Development
team](mailto:infodev@rackspace.com) for a consultation.

## Helpful resources

The following files in this repo have information to help you get
started with GitHub and authoring:

- For instructions on using GitHub and Git, see the [GITHUBING.md
  file](https://github.rackspace.com/IX/docs-starter-kit/blob/master/GITHUBING.md).
- For information about updating and adding content, see the
  [CONTRIBUTING.md
  file](https://github.rackspace.com/IX/docs-starter-kit/blob/master/CONTRIBUTING.md).

## Create the repo

Set up your repo with all the necessary files and prepare it to
publish content.

1. Log in to the appropriate GitHub site for the kind of content that you need
   to create:
   - Internal content: https://github.rackspace.com/IX/
   - External content: https://github.com/rackerlabs/
2. Create your own GitHub documentation repo.
3. While in your new GitHub repo, use **Settings > Collaborators & teams** to
   add **Admin** access to the repo for the **ix-tools** team so that they
   can provide assistance as needed.
4. Fork your GitHub repo to create your own copy of it (also called a *fork*).
5. Clone your fork to your local computer.
6. Fork the [docs-starter-kit
   repo](https://github.rackspace.com/IX/docs-starter-kit) to create
   your own copy of it.
7. Clone your fork of the docs-starter-kit repo to your local computer.
8. Copy files from your local copy of docs-starter-kit into the local
   copy of your repo.
9. Set up builds for publishing your documentation:
   - Instructions for internal documents are in the
     [tools-internal-repo
     folder](https://github.rackspace.com/IX/docs-starter-kit/tree/master/tools-internal-repo).
   - Instructions for external documents are in the
     [tools-external-repo
     folder](https://github.rackspace.com/IX/docs-starter-kit/tree/master/tools-external-repo).
10. Ensure that your content builds locally without errors or
    warnings. Ensure that the generated content looks like you expect
    by opening the HTML files in your browser.
11. Determine the date by which your content must be published.
    Contact the InfoDev Tools Team *well in advance* of this
    publication date. We recommend that you start working with them a
    month in advance of the date of first publication. At minimum,
    allow at least two weeks lead time. You must have a clean local
    build before engaging the Tools team to publish your content.

## Repo structure

To see how your content will be structured after you have performed the
preceding steps, see the "Content files and structure" section in the
following files:

-  For a user guide, see this [README
   file](https://github.rackspace.com/IX/docs-starter-kit/blob/master/template-user-guide/README.md).
-  For an API guide, see this [README
   file](https://github.rackspace.com/IX/docs-starter-kit/blob/master/template-api-guide/README.md).

In addition to the content files, the following files are included in
your ``docs`` folder:

-  ``Makefile``
-  ``conf.py``
-  ``make.bat``
-  ``spelling_wordlist.txt``

At the root level of your repo, you will also see these files:

-  ``Jenkinsfile``
-  ``LICENSE``
-  ``Makefile``
-  ``build.sh``
-  ``publish.sh``
-  ``requirements.txt``
-  ``test.sh``
-  ``tox.ini``
-  ``variables.sh``

## Write your content

After you create and set up your repo, you can create your content and
build it.

1.	In the local copy of your repo, write your content by using the files in
    the templates that you choose.
2.	In the local copy of your repo, delete any template files that you don't
    need.
3.	To commit your changes to the local copy of your repo, use ``git commit``.
4.	To push your changes from the local copy to your fork of the repo on
    GitHub, use ``git push``.
5.	In GitHub, create a pull request (PR) to move the changes from
    your fork into the master branch of the upstream repo on GitHub.
    When you create a PR, a build is automatically started to provide
    a preview of your changes.
6.	Review the preview and correct any build errors that occurred.
7.	Request reviews of your PR from subject matter experts (SMEs) on your team.
    You can use the review process in GitHub to request the review.
8.	Request reviews of your PR from the Information Development team in the
    ``#docs`` channel in Slack.
9.	After all review comments have been addressed, you can merge your
    PR, which automatically starts the documentation build and
    publishes the documentation either on the [internal docs landing
    page](https://pages.github.rackspace.com/IX/internal-docs-landing-page/)
    or the [external docs landing
    page](https://developer.rackspace.com/docs/), depending on where
    you've placed the repository.

## Support and feedback

We welcome feedback, comments, and bug reports.

Request an update to information in this repository or provide
feedback by [submitting a GitHub
issue](https://github.rackspace.com/IX/docs-starter-kit/issues/new).

You can also contact the [Information Development
team](mailto:infodev@rackspace.com) directly for general issues or
questions about the content.

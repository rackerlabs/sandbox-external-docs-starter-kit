# Internal Tools

The tools in the `docs-starter-kit/tools-internal-repo` directory are
for use with documentation in GitHub Enterprise
(`github.rackspace.com`).

The internal documentation system uses Jenkins to deploy to GitHub
Pages. GitHub Pages is a native publication platform for GitHub repos
that is built on Jekyll, a static site generator. Jenkins is a
continuous integration/continuous delivery (CI/CD) system that tests,
builds, and publishes documentation automatically.

## Work flow

The internal publication process is as follows:

1. Make changes to documentation in a new branch (not `master` or `gh-pages`)
    or make changes in your fork or clone of the repo.

2. Open a PR on `master`.

3. Wait for Jenkins to post a status update to your PR. You will see a green check mark and a comment with a staging link if the PR passes. You will see a red X if the PR fails.

    - If the PR passes, a green check mark and a comment with a staging link are displayed. Click the staging link to view the content and ensure that it looks correct.
    - If the PR fails, a red X is displayed. Use the Details link to see where the build failed.

4. After the PR passes and the content on staging looks correct, request a review from an IX team member.

5. The IX team member either provides comments or merges the PR.

    - If there are any comments, resolve them.
    - If the PR is merged, Jenkins builds and deploys the page to the
        website.

## How it works

Jenkins uses a pipeline-as-code solution held in a Jenkinsfile in conjunction
with a set of shell scripts. The Jenkinsfile uses logic to decide which shell
scripts to run and when to run each one. The shell scripts are specific to the
markup language used for the documentation in the repo.

## Using the tools

Perform the following tasks to set up your own documentation repo for publishing.

### Add a gh-pages branch to your repo

**Note: Your repository must be public. Jenkins will not work with
private repos.** If you have converted a private repo to public, you
may need to restart the scan from the organization page at
<https://infodev.jenkins.cit.rackspace.net/job/IXOrg/>.

1. Add an empty branch called `gh-pages` to your repo. We recommend adding the branch before you add content to the repo. Otherwise, create a new "orphan" branch from master.

    - If you are using the command line, use `git checkout --orphan gh-pages` to create the orphan branch. Then, delete the content and commit.

        **Note:** If you haven't used the command line for GitHub Enterprise before, you must authenticate with your username (your SSO, *not* your public GitHub username) and password. Consider using a [personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) to avoid authenticating every time you push to or pull from a repository.

    - If you are not using the command line, [create the new gh-pages branch from master](https://help.github.com/articles/creating-and-deleting-branches-within-your-repository/). On the new gh-pages branch, remove all the files.

    **Note:** Before continuing, ensure that the `gh-pages` branch is empty.

2.  In your repo, go to the **Settings** tab.
3.  In the **Options > GitHub Pages** section under GitHub Pages, select `gh-pages branch` under **Source** and then click **Save**.

### Add the Jenkins service account

1. Add the `InfoDev-docbuild-svc` service account as an admin collaborator on your repo.

    **Note:** Adding the service account lets Jenkins have access to
    your repo to publish your pages, comment on PRs with staging
    links, and send status updates on PRs. If you don't add it,
    Jenkins won't be able to publish your site.

2. Notify the [InfoDev Tools Team](mailto:mailto:infodev-tools@rackspace.com) that you
   added the service account to a new repository.

If your repo is in the IX organization, you do not need to do anything further. If the repo
is not in the IX organization, you need to set up an organization-level webhook.

#### (Non-IX only) Set up an organization-level webhook

Jenkins uses an organization-level webhook to deliver content. Your organization administrator must complete the following steps:

1. On the **Settings** tab for the repo, select **Hooks and services**.
2. In the **Webhooks** section, click **Add webhook**.
3. For **Payload URL**, enter **https://infodev.jenkins.cit.rackspace.net/github-webhook/**.
4. For **Content type**, select **application/x-www-form-unencoded**.
5. For **Which events would you like to trigger the webhook?**, select **Let me select individual events** and then select the following check boxes:

   - Create
   - Issue comment
   - Pull request
   - Pull request review
   - Pull request review comment
   - Push
   - Release
   - Repository
   - Status

6. Select the **Active** check box.

7. Click **Add webhook**.

### Add the configuration files

1. From the directory that matches the content of your repo (e.g., the
   Sphinx-RST directory for RST files), download the entire contents
   (shell script files, config files, and the Jenkinsfile) and put
   them in the root of your repo.
2. Replace the following elements in the files to match your repo by
   using a search-and-replace system, such as the repository search
   bar here in GitHub or the search-and-replace function in
   [Atom](https://atom.io).

#### Jekyll-Markdown-based (if your content is written in Markdown)

Use the `Jekyll-Markdown-based` directory.

- Replace all instances of `<orgNameOrUsername>` to match your GitHub Enterprise organization (for example, `IX`) or username (for example, `rakr0123`). We recommend using the organization name.
- Replace all instances of `<repoName>` to match the name of the repo where you are working (for example, `handbook`).
- In `_config.yml`:
   - Replace `<siteTitle>` with the title of your documentation (for example, `Rackspace Engineering Handbook`).
   - Replace `<teamEmail>` with your team's email address.
   - Replace `<multiLineDescription>` with a short description of your product (for example, `A handbook for any engineer at Rackspace.`). The description can take up multiple lines.


#### RAML-based (for API documentation written in RAML)

Use the `RAML-based` directory.

**Note:** Only RAML 1.0 is supported. If you use RAML 0.8, contact the
[InfoDev Tools Team](mailto:mailto:infodev-tools@rackspace.com).

- Replace all instances of `<orgNameOrUsername>` to match your GitHub Enterprise organization (for example, `IX`) or username (for example, `rakr0123`). We recommend using the organization name.
- Replace all instances of `<repoName>` to match the name of the repository where you are working (for example, `handbook` or `handbookModule-RPC`).
- In the **index.raml** file, copy and replace the `<ramlNames>` and `<raml-file-name>` placeholders with the names of your RAML files (the filename without `.raml` at the end). For example:

        #%RAML 1.0
        ---
        title: Index
        documentation:
          - title: API index
            content: |
            [My RAML 1](my-raml-1.html)
            [My RAML 2](my-raml-2.html)
            [My RAML 3](my-raml-3.html)


#### Sphinx-RST-based (if your content is written in RST)

Use the `Sphinx-RST-based` directory.

- Replace all instances of `<orgNameOrUsername>` to match your GitHub
  Enterprise organization (preferred; for example, `IX`) or username
  (for example, `rakr0123`). We recommend using the organization name.
- Replace all instances of `<repoName>` to match the name of the
  repository where you are working (for example, `handbook`).
- In `conf.py`:
  - Replace all instances of `<officialProjectName>` with your
    project's official name (for example, `Rackspace Engineering
    Handbook`).
  - Replace `<year>` with the current year.


##### RST Directory structure

The RST repos are set up slightly differently than other repos. The
`Jenkinsfile`, `Makefile`, `test.sh`, `build.sh`, `publish.sh`,
`variables.sh`, `tox.ini`, and `requirements.txt` files go in the root
of the repo. The `conf.py`, `make.bat`, `Makefile0`, and
`spelling_wordlist.txt` files go into the directory (typically `doc/`)
containing your content. After you move the `Makefile0` file to
`doc/`, rename it to `Makefile`.

Here is a typical RST project directory structure:

      CONTRIBUTING.rst
      GITHUBING.rst
      Jenkinsfile
      LICENSE
      Makefile
      README.rst
      build.sh
      publish.sh
      requirements.txt
      test.sh
      tox.ini
      variables.sh
      docs/
        Makefile (was Makefile0)
        chapter.rst
        common/
        conf.py
        index.rst
        make.bat
        spelling_wordlist.txt


##### Builds and spelling checks

The build checks spelling in your documents against the
`doc/spelling_wordlist.txt` file by running `tox -e checkspelling`. If
misspellings are found, the build fails and no staging link is
generated. You can see the specific spelling errors in the Jenkins
build file (click `Details` in your GitHub PR output.) If your project
uses unique terms, abbreviations, or non-typical names, add them to
`spelling_wordlist.txt` and re-check the build.

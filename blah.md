##Contributing to Gluster Documentation

The Gluster user base is growing in fast pace and there is an increase in development pace. The documentation of the new features added or anything that comes in fresh has to be documented. Contributing to the Gluster's Documentation is the most simple and easiest way to contribute to the Gluster project. From fixing spelling errors to formatting to adding new pages, any kind of contribution will help The Project immensely.

All the Documentation source resides in the ```glusterfs/docs``` directory of the gluster repository on ```Github```. All documentation pages are written in ```markdown``` format. We use [readthedocs](http://readthedocs.org) service to host the pages and mkdocs helps in converting the markdown files to html pages. The html rendered pages are available at [gluster.readthedocs.org](gluster.readthedocs.org) and this currently displays the master branch as latest documentation. You may view version specific documentation by selecting the version specified in floating button for versions (bottom right corner of the page).

The Documentation is classified into the following folders based on their content:

*  Quick Start Guide : A headstart guide for the beginners.
*  Installation Guide : Step by step instructions to install GlusterFS.
*  Administration Guide : Container for for all administrative actions.
*  Developer Guide : Container for all development related aspects.
*  Upgrade Guide : Contains guides to upgrade from older versions of GlusterFS.
*  Features : Container for all the features of GlusterFS introduced in various versions.
*  GlusterFS Tools : Contains tools used in GlusterFS.
*  Troubleshooting Guide : Container for basic troubleshooting and debugging guides.
*  Images : Container for images (in .jpg or .png format) that are present inline the documention pages.

###How to contribute

The documentation contribution workflow is similar to code development workflow but includes build process for documentation source instead of compiling programs.

The workflow sequence includes following steps:

1.  Get the Source
2.  Select/Create a new branch
3.  Make changes
4.  Commit the changes
5.  Push the changes
6.  Create a Pull Request
7.  Notify the maintainer

####Get the Source

Gluster documentation resides in the gluster repository under glusterfs/docs.

The most common way to make contributions is to use the [Fork and
Pull](https://help.github.com/articles/using-pull-requests) approach.
You must:

1.  Install git locally. For Debian/Ubuntu, execute:

        sudo apt-get install git

    For Fedora, execute:

        sudo yum install git

    For CentOS/RHEL, execute:

        sudo yum install git

2.  Ensure your `.gitconfig` file has your name and email address. :

        [user]
           email = {your-email-address}
           name = {your-name}

    For example:

        git config --global user.name "Shravan Chandra"
        git config --global user.email shravantc@ymail.com

3.  Create a [github](http://github.com) account (if you don't have
    one).

4.  Fork the Gluster project. See <https://github.com/gluster/glusterfs>.

5.  Clone your fork of the Gluster project to your local host.

####Select a Branch

When you make small changes to the documentation, such as fixing
typographical errors or clarifying explanations, use the `master` branch
(default). You should also use the `master` branch when making
contributions to features that are in the current release. `master` is
the most commonly used branch. :

    	git checkout master

When you make changes to documentation that affects an upcoming release,
use the appropriate branch:

    	git checkout `branch_name`

When you are making substantial contributions such as new features that
are not yet in the current release or if you want to see your documentation
seperate branch before it gets merged into the `master`
branch, you should create a branch. 

> **note**  
> Please do not mingle documentation contributions and source code
> contributions in a single pull request. Editors review the
> documentation and engineers review source code changes. When you keep
> documentation pull requests separate from source code pull requests,
> it simplifies the process and we won't have to ask you to resubmit the
> requests separately.
> best practice is to start the commit message with ```doc:``` for all documentation
> related commits.

Before you create your branch, ensure that it doesn't already exist
in the local or remote repository:

    	git branch -a | grep {your-branch-name}

If it doesn't exist, create your branch:

    	git checkout -b {your-branch-name}

####Make a Change

Modifying a document involves opening a markdown file, changing
its contents, and saving the changes. See [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
for syntax related requirements.

Adding a document involves creating a new markdown file under
the `doc` or `docs` directory or its subdirectories and saving the file with a
`*.md` file extension.  

**You must also include a reference to the
document: a entry into the `mkdocs.yml` file which defines the index structure
for the documentation . Relevant entries (wherever applicable) should be made
into the subdirectory specific index.md (or README.md) file.**

Your new document doesn't get tracked by `git` automatically. When you
want to add the document to the repository, you must use
`git add  {path-to-filename}`. For example, from the top level directory
of the repository, adding an `example.md` file to the `Features`
subdirectory would look like this:

    	git add doc/Features/example.md

Deleting a document involves removing it from the repository with
`git rm {path-to-filename}`. For example:

    	git rm doc/Features/example.md

You must also remove any reference to a deleted document from other
documents.

####Commit the Change

Gluster documentation commits are simple, but follow a strict convention:

-   A commit SHOULD have 1 file per commit (it simplifies rollback). You
    MAY commit multiple files with related changes. Unrelated changes
    SHOULD NOT be put into the same commit.
-   A commit MUST have a comment.
-   A commit comment MUST be prepended with `doc:`. (strict)
-   The comment summary MUST be one line only. (strict)
-   Additional comments MAY follow a blank line after the summary, but
    should be terse.
-   A commit MAY include `Fixes: #{bug number}`.
-   Commits MUST include `Signed-off-by: Firstname Lastname <email>`.
    (strict)

> **tip**  
> Follow the foregoing convention particularly where it says `(strict)`
> or you will be asked to modify your commit to comply with this
> convention.

The following is a common commit comment (preferred):

    doc: Fixing a spelling error and a broken hyperlink.

    Signed-off-by: Shravan Chandra <shravantc@ymail.com>

The following comment includes a reference to a bug:

    doc: Fixing a spelling error and a broken hyperlink.

    Fixes: #1234

    Signed-off-by: Shravan Chandra <shravantc@ymail.com>

To commit changes, execute the following:

    	git commit -a

An easy way to manage your documentation commits is to use visual tools
for `git`. For example, `gitk` provides a graphical interface for
viewing the repository history, and `git-gui` provides a graphical
interface for viewing your uncommitted changes, staging them for commit,
committing the changes and pushing them to your forked Gluster repository.

For Debian/Ubuntu, execute:

        sudo apt-get install gitk git-gui

For Fedora, execute:

        sudo yum install gitk git-gui

In CentOS/RHEL7, `gitk` and `git-gui` are not available in default or
`epel` repository. So, use <http://rpmfind.net/> to find them. Then,
download them from a mirror and install them. For example:

	    wget ftp://rpmfind.net/linux/centos/7.0.1406/os/x86_64/Packages/gitk-1.8.3.1-4.el7.noarch.rpm
	    sudo yum install gitk-1.8.3.1-4.el7.noarch.rpm
	    wget ftp://rpmfind.net/linux/centos/7.0.1406/os/x86_64/Packages/git-gui-1.8.3.1-4.el7.noarch.rpm
	    sudo yum install git-gui-1.8.3.1-4.el7.noarch.rpm

Then, execute:

    	cd {git-gluster-repo-path}
    	gitk

Finally, select **File-\>Start git gui** to activate the graphical user
interface.

####Push the Change

Once you have one or more commits, you must push them from the local
copy of the repository to `github`. A graphical tool like `git-gui`
provides a user interface for pushing to the repository. If you created
a branch previously:

    	git push origin {your-branch-name}

Otherwise:

    	git push

####Make a Pull Request

As mentioned earlier, you can make documentation contributions using the
[Fork and Pull](https://help.github.com/articles/using-pull-requests)
approach.

####Notify the Relevant Person

After you make a pull request, notify the relevant person through a comment
in github or by sending a mail (can be found in the maintainers list)

### Helpful links for Markdown

*  [About Markdown](en.wikipedia.org/wiki/Markdown About Markdown)
*  [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
*  [Online Markdown Editor](http://dillinger.io)

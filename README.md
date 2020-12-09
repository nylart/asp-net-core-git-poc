# asp-net-core-git-poc
Proof of concept app for using git for asp net core MVC applications. Contains main solution "CoreApp" with submodule "CoreLibrary". "CoreLibrary" has its own git repository. "CoreApp" has an assembly dependency of the "CoreLibrary.dll". In the code, it references the CoreLibrary but does not actually do anything useful since this is a test application to show how submodules work.

## Important Concepts
### [Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
- Allows you to use another project within a project. Useful for libraries, third party libraries, or simply just different projects.
- Allows you to treat the projects separately, but still allows you to use one within another.
- Each submodule would have its own repository. 
- When you want to add a submodule of an already existing repo, run the following command. It will update the .gitmodules file with the newly added submodule. 
```
git submodule add [GIT URL HERE]
```
- Whenever you want to initialize the submodules, run 
```
git submodule update --init
```
- From the [Git Submodule Documentation](https://git-scm.com/docs/git-submodule): 
"update [--init] [--remote] [-N|--no-fetch] [--[no-]recommend-shallow] [-f|--force] [--checkout|--rebase|--merge] [--reference <repository>] [--depth <depth>] [--recursive] [--jobs <n>] [--[no-]single-branch] [--] [<path>…​]
Update the registered submodules to match what the superproject expects by cloning missing submodules, fetching missing commits in submodules and updating the working tree of the submodules."
### [Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- Let's say we are satisfied with a current build of the project. We would create a tag for it which will create a tag and branch for the project. 
- You can see [here](https://github.com/nylart/asp-net-core-git-poc/tags) how the tags are shown in Github.
- To create a tag you would run the command:
``` 
git tag [TAG NAME]
git push origin --tags
```
### [Branching](https://git-scm.com/docs/git-branch)
- It is obvious what branching is, but I specifically created a main and develop branch for the project.
### [Pull Requests](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/about-pull-requests#:~:text=Pull%20requests%20let%20you%20tell,merged%20into%20the%20base%20branch)
- Allows developers to submit a changeset that you wish to push to a branch. When the pull request is opened, the repository maintainer can review the changes before merging it into the branch. This is how code reviews would be done with Git.
## Getting Started
1. Download and setup Git.
2. Open up Git Bash, navigate to a directory that you wish to clone this project into. Run:
```
git clone https://github.com/nylart/asp-net-core-git-poc.git
```
3. Navigate into the cloned repository directory.
4. Initialize submodules by running:
```
git submodule update --init
```
    
5. Done :)

## Alternatives to Github.com for server hosting
- [Gitlab](https://gitlab.com/gitlab-com)
- [Bitbucket](https://bitbucket.org/product)
- [Gitolite](https://gitolite.com/gitolite/index.html)
- Azure Dev Ops
- Or just create your own server

## Random people on the internets reasoning on why Git > TFS
- https://www.continuousimprover.com/2015/06/why-you-should-abandon-tfs-source.html#:~:text=It%20keeps%20the%20history%20clean,pretty%20dumb%20text%2Dbased%20merge.
- https://dzone.com/articles/why-you-should-use-git-over-tfs
- https://michaelscodingspot.com/life-changed-moving-tfvctfs-git/
- https://simpleprogrammer.com/git-vs-tfvc/
- https://medium.com/@lahavlior/advantages-and-disadvantages-in-migratfrom-tfs-to-git-d3ac9b031982

## Concerns RE: Using Console vs GUI
There are several GUIs for Git available to use. I've used SmartGit, Github's own Github Desktop, GitKraken, etc. 
Github Desktop is limited really to the basic commands with Git. I like SmartGit since it has functionality for most commands including commands related to submodules, tagging, pull requests, etc. Visual Studio also has the ability to use Git as version control, however it is still limited in functionality.

If there are cases where you would need to run common commands, we can create a bash script to streamline the process so the developers don't have to remember so many different commands. 

## Code Reviews
Code reviews are done via pull requests. The repository maintainer reviews the changesets and decides if it is ready to merge or not. If yes, then the maintainer can merge the changeset into the master branch. 

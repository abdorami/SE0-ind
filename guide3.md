# 5.1 Distributed Git - Distributed Workflows
Now that you have a remote Git repository set up as a focal point for all the developers to share their code, and you’re familiar with basic Git commands in a local workflow, you’ll look at how to utilize some of the distributed workflows that Git affords you.

In this chapter, you’ll see how to work with Git in a distributed environment as a contributor and an integrator. That is, you’ll learn how to contribute code successfully to a project and make it as easy on you and the project maintainer as possible, and also how to maintain a project successfully with a number of developers contributing.

### Distributed Workflows
Unlike Centralized Version Control Systems (CVCSs), the distributed nature of Git allows you to be far more flexible in how developers collaborate on projects. In centralized systems, every developer is a node working more or less equally on a central hub. In Git, however, every developer is potentially both a node and a hub — that is, every developer can both contribute code to other repositories and maintain a public repository on which others can base their work and which they can contribute to. This opens a vast range of workflow possibilities for your project and/or your team, so we’ll cover a few common paradigms that take advantage of this flexibility. We’ll go over the strengths and possible weaknesses of each design; you can choose a single one to use, or you can mix and match features from each.

### Centralized Workflow
In centralized systems, there is generally a single collaboration model — the centralized workflow. One central hub, or repository, can accept code, and everyone synchronizes their work to it. A number of developers are nodes — consumers of that hub — and synchronize to that one place.
![](https://git-scm.com/book/en/v2/images/centralized_workflow.png)
*Figure 54. Centralized workflow.*
This means that if two developers clone from the hub and both make changes, the first developer to push their changes back up can do so with no problems. The second developer must merge in the first one’s work before pushing changes up, so as not to overwrite the first developer’s changes. This concept is as true in Git as it is in Subversion (or any CVCS), and this model works perfectly well in Git.

If you are already comfortable with a centralized workflow in your company or team, you can easily continue using that workflow with Git. Simply set up a single repository, and give everyone on your team push access; Git won’t let users overwrite each other. Say John and Jessica both start working at the same time. John finishes his change and pushes it to the server. Then Jessica tries to push her changes, but the server rejects them. She is told that she’s trying to push non-fast-forward changes and that she won’t be able to do so until she fetches and merges. This workflow is attractive to a lot of people because it’s a paradigm that many are familiar and comfortable with.

This is also not limited to small teams. With Git’s branching model, it’s possible for hundreds of developers to successfully work on a single project through dozens of branches simultaneously.

### Integration-Manager Workflow
Because Git allows you to have multiple remote repositories, it’s possible to have a workflow where each developer has write access to their own public repository and read access to everyone else’s. This scenario often includes a canonical repository that represents the “official” project. To contribute to that project, you create your own public clone of the project and push your changes to it. Then, you can send a request to the maintainer of the main project to pull in your changes. The maintainer can then add your repository as a remote, test your changes locally, merge them into their branch, and push back to their repository. The process works as follows (see [Integration-manager workflow.](https://git-scm.com/book/en/v2/ch00/wfdiag_b)):

1. The project maintainer pushes to their public repository.
1. A contributor clones that repository and makes changes.
1. The contributor pushes to their own public copy.
1. The contributor sends the maintainer an email asking them to pull changes.
1. The maintainer adds the contributor’s repository as a remote and merges locally.
1. The maintainer pushes merged changes to the main repository.
![](https://git-scm.com/book/en/v2/images/integration-manager.png)
*Figure 55. Integration-manager workflow.*
This is a very common workflow with hub-based tools like GitHub or GitLab, where it’s easy to fork a project and push your changes into your fork for everyone to see. One of the main advantages of this approach is that you can continue to work, and the maintainer of the main repository can pull in your changes at any time. Contributors don’t have to wait for the project to incorporate their changes — each party can work at their own pace.
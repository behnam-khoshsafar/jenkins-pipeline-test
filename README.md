#run jenkins in docker using the steps that defined [here](`https://www.jenkins.io/doc/book/installing/docker/).
#continue [this tutorial](https://devopscube.com/jenkins-multibranch-pipeline-tutorial/) to create Multi-branch Pipeline

#Pipeline behaviour config

1- `Exclude branches that are also filed as PRs`
* If you are discovering origin pull requests, you may not want to also build the source branches for those pull requests, but it's going to build the branch for each push before creating a pull request.
* It's going to build the branch again if you don't delete the branch after merging the pull request.

2- `Only branches that are also filed as PRs`
* Similar to discovering origin pull requests, but discovers the branch rather than the pull request. This means env.GIT_BRANCH will be set to the branch name rather than PR-#. Also, status notifications for these builds will only be applied to the commit and not to the pull request. 
* It's going to run pipeline for the PR and the source branch in the PR, and it is not going to run the pipeline for the target branch after merge.

3-`All branches`
* Ignores whether the branch is also filed as a pull request and instead discovers all branches on the origin repository.

we can use another filter like `Filter by name`, but this filter will be applied to all branches, including pull requests
# Git
This drill is about how we use git in our development.

## When to Commit
We commit our code frequently so that it is easier to debug or reference or understand how the app is being built.

Each commit should be small. It is like a unit of code that can be applied or removed from the project as a logical whole.

## Git Commit Message
Write the message of what this commit do in the imperative mode, that is as if you were commanding someone. Use "fix", "add", "change" instead of "fixed", "added", "changed".

Keep your commit message to 50 chars or less.

Capitalize the commit message.

If you find it hard to write a commit message, you are probably lumping too many changes into a commit. Try separating them into different commits.

Examples of good commit messages:
- Fix screen not loading bug on homepage
- Add Product model with test cases
- Refactor ProductsController#index
- Update Products show view
- Style Products show view

## Branching
We use git branching to separate our development work, commonly known as git flow.

`master` branch is used for production. It should always be deployable to production. We should not develop directly on the master.

`staging` branch is used for staging. It should always be deployable to staging. We should not develop directly on the staging too.

We create a branch (known as feature branch) for each story that we are developing for. The branch is based off master or staging branch. 

Once the feature is completed, we will push it to remote and then create a merge request on Gitlab for [code review](../../code-review/README.md). When the code review is completed, we will merge it into staging or master for deployment.

If a project does not have a production site, we will not use staging branch and instead, treat master branch as the staging branch. This is for productivity as it is pointless to merge into staging and then into master again when there is no staging site.

## Pull Request/Merge Request
We practice using pull request in Github or merge request in Gitlab to send in code for new features. [Code review](../../code-review/README.md) is done on the request before merging into the master.

## Common Git Practices
- Large number of files that are added to the project such as `rails new .` or adding bootstrap CSS files always goes into a commit. This separates the external code from our own developed code.
- When we created a rails project (eg. after we run `rails new .`), we always commit the Rails generated files as `Initial commit`

## How to practise this drill?
- Find a project to do that is simple such as [this](https://github.com/futureworkz/rails-test-1)
- Setup your own Gitlab repository for this project
- Start developing on your feature branch
- Write good commit message when you are committing
- Push it to Gitlab and open a merge request
- Merge the branch yourself
- Repeat for another feature

You can also show all your git commits to your peers to ask for review.

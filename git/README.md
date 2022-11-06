# Git Guidelines

This document covers the guidelines for best practices when using Git.

## Table of Contents-

- [1. Branches](#1-branches)
  - [1.1.1.1. Branch Structure](#11-branch-structure)
  - [1.1.1.2. Lifespan](#12-lifespan)
  - [1.1.1.3. Branch Naming](#13-branch-naming)
- [2. Commits](#2-commits)
- [3. Pull Requests](#3-pull-requests)
- [3.1. Before you start working](#31-before-you-start-working)
- [3.2. When to create a Pull Request?](#32-when-to-create-a-pull-request)
  - [3.2.1. When your work is complete](#321-when-your-work-is-complete)
  - [3.2.2. When you want early feedback on your work](#322-when-you-want-early-feedback-on-your-work)
- [3.3. How to create a PR?](#33-how-to-create-a-pr)
  - [3.3.1. Have a correct title](#331-have-a-correct-title)
  - [3.3.2. Make sure the description is clear](#332-make-sure-the-description-is-clear)
  - [3.3.3. Add design links or screenshots](#333-add-design-links-or-screenshots)
  - [3.3.4. Assign the right people as reviewers](#334-assign-the-right-people-as-reviewers)
  - [3.3.5. Set the correct target branch](#335-set-the-correct-target-branch)
  - [3.3.6. Other target branches](#336-other-target-branches)
    - [3.3.6.1. When Your work depends on an open PR](#3361-when-your-work-depends-on-an-open-pr)
    - [3.3.6.2. When you want part of your work to be reviewed separately](#3362-when-you-want-part-of-your-work-to-be-reviewed-separately)
- [3.4. What are your responsibilities in the PR review process?](#34-what-are-your-responsibilities-in-the-pr-review-process)
  - [3.4.1. Handling feedback](#341-handling-feedback)
- [3.5. General rules for merging a PR](#35-general-rules-for-merging-a-pr)
- [3.6. Exceptional cases](#36-exceptional-cases)

## 1. Branches

Branches are an important part of the Git workflow. They are used to isolate work from other work that is being done. Branches are also used to group work together that is related to a specific feature or bug fix.

### 1.1. Branch Structure

The branch structure should be as follows:

- `master` - The main branch. This branch should always be in a deployable state.
- `develop`/`dev` - The main development branch. This branch should always be in a deployable state. It should be based of the `main` branch.
- `feature/`/`feat` - A branch that is used to develop a new feature. It should merge in to `develop`/`dev`. It should be based of the `dev` branch
- `hotfix/` - A branch that is used to fix a bug urgently. It acts as a `patch` until a full proof solution is created for the issue. It can be merged in to `develop`/`dev`, `feature`/`feat` or directly the `main` branch.

Any other branches other than `hotfix` should primarily merge into a `feat` branch. The `feat` branch should then merge into the `dev` branch. `hotfix` branches can be merged directly into `main`/`dev` depending on the urgency of the fix.

### 1.2. Lifespan

- Branches should be short lived. Branches should not have have a lifespan exceeding 2-3 days.
- Branches should be created when work on a feature or bug fix is started and should be deleted when the work is completed.

### 1.3. Branch Naming

- Branches should be named using the following format: `feat/feature-name` or `fix/bugfix-name`. For example, `feat/awesome-feature` or `fix/awesome-bugfix`.

## 2. Commits

- Commits should follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) format.
- Only commit one feature at the time.
- Try to separate unrelated changes into different commits. This can include formatting changes, refactoring, etc.
- Always lint, format code before committing.
- Always make sure to pull the latest changes from the remote branch before committing.

## 3. Pull Requests

This section goes over the steps for creating a Pull Request (PR), including some dos and don’ts.

> Note: the terms _Pull Request_ and _Merge Request_ can be used interchangeably. The same is true
> for the terms _issue_, _ticket_, and _stories_.

### 3.1. Before you start working

Make sure that there is an issue created and assigned to you. Work on a feature branch that is named
accordingly (feature/, fix/, hotfix/). It might also be a good idea to validate the approach you
intend to take in case it is a big or complex issue.

### 3.2. When to create a Pull Request?

The two main reasons to create a pull request are when your work is complete, or when you want early
feedback on your work.

#### 3.2.1. When your work is complete

You finished the work on an issue in a dedicated feature branch, and you’re ready to have your code
merged into `develop`.

This process is also useful for others to learn about the changes you have made. The pull request
can be merged after the work is reviewed and all of the feedback has been addressed.

The branch should be deleted after merge, since the work is done and available in develop. Keeping
the branch open is the same thing as making a new branch from develop (maybe even with the same name
as before). The only reason to keep it open is convenience - not having to re-create the branch if
you plan to do make part of the ticket already available on develop but continue working on it, but
that's an edge case.

#### 3.2.2. When you want early feedback on your work

If you have been assigned a task, but are not 100% sure about the approach you are taking and want
some feedback before you continue down that road, please make sure that:

- You have added `WIP` to the title to make it clear that it is still a work in progress
- It is clear which specific code or features you’d like to have feedback on
- You indicated which people you want to review your code

After the feedback, you can either decline the PR and start over or continue with the work in the
same PR. You can keep committing in the same branch with updates, so the reviewers can keep track of
your work. Just make sure you let them know when it’s ready to review again by changing the PR
description and mentioning them. Remove `WIP` from the title when it’s ready and make sure the
reviewers are notified.

### 3.3. How to create a PR?

There are a couple of things to pay attention to when creating a PR, such as having a correct title,
and all the necessary information in the description.

#### 3.3.1 Have a correct title

Here are some guidelines for a correct title:

- Should contain ticket identification, such as the ticket link from clickup.
- Should be descriptive enough. A good rule of thumb is to make it the same as the issue summary.
- No emoticons. They add noise and don’t render properly in the PR list on some platforms.

#### 3.3.2. Make sure the description is clear

Add a proper description to your PR. It should contain:

- A link to the issue you are working on.
- A short description of the changes you made.
- A list of things you want the reviewers to pay attention to.

#### 3.3.3. Add design links or screenshots

If it’s a UI PR, link to the designs or add a screenshot so reviewers can clearly understand the
scope of the PR, and compare it with that.

#### 3.3.4. Assign the right people as reviewers

Not every developer should have to review every PR, so make sure you add the right people as
reviewers based on the PR content.

Try not to add developers if your PR is not relevant to the topics they work on. This way, if they
are added to a PR, they know it’s relevant for them and are more likely to respond in a timely
manner.

Everyone should be added as a reviewer for PRs that introduce a change in policy or rules. This
makes sure everyone is aware of that change. For example, a new linting rule or util that everyone
should follow/use.

#### 3.3.5. Set the correct target branch

The most common kind of PR is when a branch is created from `develop` as a base branch, and the PR is
merged back into `develop` when ready. This means that most of the time it’s fine to leave the default
branch as the target branch.

#### 3.3.6. Other target branches

In some cases, you might want to set a different target branch, for example when your work depends
on an open PR or when you want part of your work reviewed separately.

##### 3.3.6.1. When Your work depends on an open PR

Ideally, PRs are merged to develop in a timely manner so you can continue to build on that work. In
practice though, it may happen that an open PR is blocked but you need to start your own branch. You
can do that in the following way:

1. Create a new branch with the branch you depend on as a base branch instead of from develop.
2. When your work is completed, create a PR with that same base branch as the target.
3. In your description, clearly state that you want the originally blocked PR to be merged before
   merging this new PR.
4. If the PR that was blocking you has been merged, change the target branch back to develop.

##### 3.3.6.2. When you want part of your work to be reviewed separately

Sometimes you are working on a part of a feature that you want to have reviewed separately. For
example, you may want to check with others that you are on the right path. The workflow will look
something like this:

1. Create a separate branch with the feature branch you are currently working on as a base branch.
2. When the part of the work you want to be reviewed is completed, create a PR back to the feature
   branch. Make sure that the PR description mentions that this is intended as an intermediate
   review and that you want it to be merged before merging the full feature.

_After creating the PR, it can happen that it’s more practical to merge the original feature branch_

_to develop first. In this case, it’s still possible to revert back to the steps in When Your work
depends on an open PR. This means that after merging the original feature branch, you’ll need to
make sure you change the target of your PR back to develop_

### 3.4. What are your responsibilities in the PR review process?

As the author of the PR, you should maintain the following:

#### 3.4.1. Handling feedback

- Read incoming feedback/comments
- Address feedback/comments by either:
  - answering the question
  - making changes to the code
  - creating new issues for things that should be picked up outside of this PR. When it applies to a
    specific piece of code, add a TODO comment with a link to that issue in the code.
- When a comment is resolved, especially when doing so through code changes, add a
  [✅](https://emojis.wiki/check-mark-button/#:~:text=White%20Heavy%20Check%20Mark%20emoji,emoji%20that%20provides%20positive%20reinforcement.)
  reply to let everyone know it has been addressed.
- When committing suggested changes make sure that the commit message contains a descriptive message
  about these changes. Avoid writing messages like "Addressed PR feedback", "Fixed PR feedback"

#### 3.4.2 Merging into develop

Before merging into `develop`, merge `develop` into your branch and resolve any conflicts. If your PR
has been open for a long time you might need to repeat this step and make sure your PR still works
with the changes from develop.

### 3.5. General rules for merging a PR

Generally the person that created the PR should also merge it. This is because sometimes extra
actions are required after the merge, like updating ticket statuses or notifying people. Please read
when your PR is ready to be merged below.

- You have at least 2 approvals, out of which atleast 1 is from a senior developer. Having more
  approvals is always better as it can avoid tunnel vision.
- The CI pipeline build is successful.
- All feedback from comments is resolved. This can be by resolving all issues raised in the comment,
  or if necessary by deferring work to a new issue.
- There are no merge conflicts.

### 3.6. Exceptional cases

Some common sense should be applied when following the above rules. Below is a list of additions and
exceptions you should consider.

- When a PR has a big impact or breaking changes, it’s good to have approval from a lot of devs (or
  everyone), so we know everyone is aware of the changes
- When a PR is open for a long time, or has received a lot of updates, it’s good practice to merge
  in your develop branch once in a while (and ideally before merging it). You can only be sure your
  PR doesn’t break develop after merging, if the latest develop also exists in your branch (in other
  words, if your merge will result in a fast-forward on develop).
- When a PR is fairly small, or should be merged ASAP, the merge responsibility can be handed over
  to someone else, for example the last person to approve it, or someone in another timezone. Please
  add this as a general comment in the PR, and/or let them know via instant messaging.
- Some PRs are created to make work from a feature branch available in develop, before the feature
  itself is complete. However, the work in the branch is isolated enough, or a finished sub-set, and
  can be safely merged. In these cases, the branch should continue to live, because a future PR will
  be created after more work is done

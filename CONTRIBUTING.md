# Contributing

## Table of Contents

## Version Control and Git Flow

Whenever you encounter a :beetle: **bug** or have :tada: **feature request**,
report this via [Github issues](TODO: Link to issues).

We are happy to receive contributions to (TODO: PROJECT_NAME) in the form of **pull requests** via Github.
Feel free to fork the repository, implement your changes and create a merge request to the `develop` branch.
There is a [forking guide](#forking) available to get you started!

### Branching Guidelines
The development follows a simplified version of **git-flow**: The `main` branch always contains stable code.
New features and bug fixes are implemented in `feature/*` or `fix/*` branches and are merged to `develop` once they are finished.
When a new milestone is reached, the content of `develop` will be merged to `main` and a tag is created.

[Github Actions](TODO: Link to actions) are used for continuous integration.
All pull requests and pushes to `main` and `develop` are built automatically.

### Git Commit Messages
Commits should start with a Capital letter and should be written in present tense (e.g. __:tada: Add cool new feature__ instead of __:tada: Added cool new feature__).
It's a great idea to start the commit message with an applicable emoji. This does not only look great but also makes you rethink what to add to a commit.
* :tada: `:tada:` when adding a cool new feature
* :wrench: `:wrench:` when refactoring / improving a small piece of code
* :hammer: `:hammer:` when refactoring / improving large parts of the code
* :sparkles: `:sparkles:` when formatting code
* :art: `:art:` improving / adding assets like textures or images
* :rocket: `:rocket:` when improving performance
* :memo: `:memo:` when writing docs
* :beetle: `:beetle:` when fixing a bug
* :green_heart: `:green_heart:` when fixing the CI build
* :heavy_check_mark: `:heavy_check_mark:` when working on tests
* :arrow_up_small: `:arrow_up_small:` when adding / upgrading dependencies
* :arrow_down_small: `:arrow_down_small:` when removing / downgrading dependencies
* :twisted_rightwards_arrows: `:twisted_rightwards_arrows:` when merging branches
* :fire: `:fire:` when removing files
* :truck: `:truck:` when moving / renaming files or namespaces

A good way to enforce this on your side is to use a `commit-hook`. To do this, paste the following script into `.git/hooks/commit-msg`.

``` bash
#!/bin/bash

# regex to validate in commit msg
commit_regex='(:(tada|wrench|hammer|sparkles|art|rocket|memo|beetle|green_heart|arrow_up_small|arrow_down_small|twisted_rightwards_arrows|fire|truck|heavy_check_mark):(.+))'
error_msg="Aborting commit. Your commit message is missing an emoji as described in the contributing guideline."

if ! grep -xqE "$commit_regex" "$1"; then
    echo "$error_msg" >&2
    exit 1
fi
```

And make sure that it is executable:

``` bash
chmod +x .git/hooks/commit-msg
```

### Forking
This is pretty straight-forward. Just click the **Fork** button on the top right of this page. 
Then clone the forked repository, perform your changes, push to a feature branch and create a pull request to the develop branch.

``` bash
git clone git@github.com:<your user name>/<project name>.git
cd <project name>
git remote add upstream git@github.com:<user/organization>/<project name>.git
git checkout develop

git checkout -b feature/your-new-feature
# or
git checkout -b fix/your-bugfix

# ... do and commit your changes!

git push origin feature/your-new-feature
```

When there were changes in the develop branch, you will need to merge those to your fork before creating a pull request:

``` bash
git fetch upstream
git merge upstream/develop
```

Then you can create a pull request on GitHub to the develop branch.

## Development

### Requirements

> [!TIP]
> See the [README.md](./README.md#requirements). Maybe add some further requirements only for contributers here.

### Development Builds

> [!TIP]
> Give some hints for developers how they can build the software more efficiently during development. Maybe give examples of flags that disable optimizations or scripts that enable hot module reloading.

### Code Style

> [!TIP]
> Give information which code style to use and how to automatically enforce it. There are different tools for different languages.

### Linter

> [!TIP]
> If the project uses a linter, specify how to use it and what config to use.

### Test Cases

> [!TIP]
> Give information about your testing strategy. How to name tests and how to organize them. Maybe also give hints about the complexity of tests and which scope they should test.

### Documentation

> [!TIP]
> Add meaningful documentation to all classes, functions and fields. Try to be complete, but concise. Don't comment with redudant information like: `int counter; // the counter`.

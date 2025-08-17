<!-- Thanks Github for a nice template: <https://github.com/github/docs/blob/main/CONTRIBUTING.md> -->
# Contributing to Insulting Pros Projects

First off, thanks for taking the time to contribute! 👍

In this guide you will get an overview of the contribution workflow from opening an issue, creating a PR, reviewing, and merging the PR.

## Issues

### Create a new issue

If you spot a problem with the code-gameplay-broken features-etc, search if an issue already exists. If a related issue doesn't exist, you can open a new issue using a relevant issue form.

### Solve an issue

Scan through our existing issues to find one that interests you. You can narrow down the search using labels as filters. See Labels for more information. As a general rule, we don’t assign issues to anyone. If you find an issue to work on, you are welcome to open a PR with a fix.

<!-- Some Python sauce applied: <https://peps.python.org/pep-0008/> -->
## Coding style

**UnrealScript**:

- Check this [document](https://github.com/InsultingPros/.github/blob/main/.github/coding-style.md).

**Python**:

- Stick to [PEP 8](https://peps.python.org/pep-0008/).
- [Type hints](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html) are a must.

**Rust**:

- Clippy's [`pedantic`](https://rust-lang.github.io/rust-clippy/master/index.html#?versions=eq:29,lte:30,gte:29&groups=pedantic) ruleset.
- Code should not have any active or supressed warnings.

## Directory style

- You can use any case for your directory names, e.g. you can put your config files inside configs, Configs, CONFIGS or ConFIgS.
- Always provide default configuration files in `configs` directory.
- Put all documentation files into `docs`.

## Pull Request

When you're finished with the changes, create a pull request, also known as a PR.

- Fill the "Ready for review" template so that we can review your PR. This template helps reviewers understand your changes as well as the purpose of your pull request.
- Don't forget to link PR to issue if you are solving one.
- Once you submit your PR, we will review your proposal. We may ask questions or request for additional information.
- We may ask for changes to be made before a PR can be merged, either using suggested changes or pull request comments. You can apply suggested changes directly through the UI. You can make any other changes in your fork, then commit them to your branch.
- As you update your PR and apply changes, mark each conversation as resolved.

## Your PR is merged

Congratulations 🎉 We thank you ✨.

Once your PR is merged, your contributions will be publicly visible on the corresponding repo page.

Now you are a part of our community!

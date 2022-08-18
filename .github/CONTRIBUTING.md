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

- File Encoding: UTF8, but in rare conditions we want it in `UTF-16 BE` and mention that on file header comment.
- Indentation: use 4 spaces per indentation level. Even if you find an old piece of code that uses x2 spaces, override it.
- Use camel case - variable names start with lower case letter and class (object / actor) names with upper case: `local Object objectVariable`.
- `none`, `default`, `super`, `false / true` and all other special words: in lower case.
- `int`, `float`, `byte`, `bool`, `string` variables: lower case.
- 2 blank lines between functions.
- 1 blank line after variable declaration.
- Add a space between function call / conditions / statements and parentheses:`while (bBool)`.
- Don't put spaces:
  - Immediately after parentheses, brackets or braces: `FunctionCall(arg1, arg2)`.
  - Immediately before a comma, semicolon, or colon.
  - More than one space around an assignment (or other) operator to align it with another: `n = 3`.
- Avoid trailing whitespace anywhere.

Rest of the rules... I don't fucking know, just check out our code or something 🤣

## Directory style

- You can use any case for your directory names, e.g. you can put your config files inside configs, Configs, CONFIGS or ConFIgS.
- Always provide default configuration files in `Configs` directory.
- Put all documentation files into `Docs`.

## Pull Request

When you're finished with the changes, create a pull request, also known as a PR.

- Fill the "Ready for review" template so that we can review your PR. This template helps reviewers understand your changes as well as the purpose of your pull request.
- Don't forget to link PR to issue if you are solving one.
- Once you submit your PR, we will review your proposal. We may ask questions or request for additional information.
- We may ask for changes to be made before a PR can be merged, either using suggested changes or pull request comments. You can apply suggested changes directly through the UI. You can make any other changes in your fork, then commit them to your branch.
- As you update your PR and apply changes, mark each conversation as resolved.

## Your PR is merged!

Congratulations 🎉 We thank you ✨.

Once your PR is merged, your contributions will be publicly visible on the corresponding repo page.

Now you are a part of our community!

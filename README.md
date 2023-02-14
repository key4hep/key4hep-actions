# key4hep-actions
Github actions for CI in the key4hep stack

# Downstream build
This action does two things:
- Builds packages downstream to check that the changes that were made do not
  break the packages that depend on the one that was changed
- Builds packages that have been changed at the same time. For this to work
  there has to be a PR for each package. Then, in one of the pull request there
  has to be anywhere in the text a mention to all the PRs that we want to build
  together. This mention will look like this:

  ```
  PR text, explanation, release notes, etc
  Depends on URL_OF_PR_1, URL_OF_PR_2
  ```

  There is some flexibility to try to catch possible edge cases: the urls don't
  need to be in the same line, they can be comma separated or space separated or
  and-separated.


# key4hep-actions
Github actions for CI in the key4hep stack

# Key4hep build
This action builds the Key4hep stack on the supported OSes for both the stable
releases and the nightlies. After that, it runs the available tests using
`ctest`. It also runs during the night every day to populate a cache (using
`ccache`) that is later used by the action (for example, in pull requests) so
that building will be faster if they files that are built haven't changed. For
example, for a simple change in a README file the builds will be very fast since
all the files are cached, but the workflow may take longer because of the tests.

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


.. role:: bash(code)

.. _anno:

anno
----
Usage:

.. code-block:: shell

    git machete anno [-b|--branch=<branch>] [<annotation text>]
    git machete anno -H|--sync-github-prs

If invoked without any argument, prints out the custom annotation for the given branch (or current branch, if none specified with :bash:`-b/--branch`).

If invoked with a single empty string argument, like:

.. code-block:: shell

    $ git machete anno ''

then clears the annotation for the current branch (or a branch specified with :bash:`-b/--branch`).

If invoked with :bash:`-H` or :bash:`--sync-github-prs`, annotates the branches based on their corresponding GitHub PR numbers and authors.
Any existing annotations are overwritten for the branches that have an opened PR; annotations for the other branches remain untouched.

To allow GitHub API access for private repositories (and also to correctly identify the current user, even in case of public repositories),
a GitHub API token with :bash:`repo` scope is required, see :bash:`https://github.com/settings/tokens`. This will be resolved from the first of:
    1. :bash:`GITHUB_TOKEN` env var,
    2. current auth token from the :bash:`gh` GitHub CLI,
    3. current auth token from the :bash:`hub` GitHub CLI.

In any other case, sets the annotation for the given/current branch to the given argument.
If multiple arguments are passed to the command, they are concatenated with a single space.

Note: all the effects of :bash:`anno` can be always achieved by manually editing the definition file.

Options:
  -b, --branch=<branch>     Branch to set the annotation for.

  -H, --sync-github-prs     Annotate with GitHub PR numbers and authors where applicable.


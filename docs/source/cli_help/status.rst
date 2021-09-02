.. role:: bash(code)

.. _status:

status
------
Usage:

.. code-block:: shell

    git machete s[tatus] [--color=WHEN] [-l|--list-commits] [-L|--list-commits-with-hashes] [--no-detect-squash-merges]

Displays a tree-shaped status of the branches listed in the definition file.

Apart from simply ASCII-formatting the definition file, this also:

    * colors the edges between upstream (parent) and downstream (children) branches:

      - red edge means that the downstream branch tip is not a direct descendant of the upstream branch tip,

      - yellow edge means that the downstream branch tip is a direct descendant of the upstream branch tip,
        but the fork point (see help on :bash:`fork-point`) of the downstream branch is not equal to the upstream branch tip,

      - green edge means that the downstream branch tip is a direct descendant of the upstream branch tip
        and the fork point of the downstream branch is equal to the upstream branch tip,

      - grey/dimmed edge means that the downstream branch has been merged to the upstream branch,
        detected by commit equivalency (default), or by strict detection of merge commits (if :bash:`--no-detect-squash-merges` passed).


    * prints :bash:`(untracked/ahead of <remote>/behind <remote>/diverged from [& older than] <remote>)` message if the branch is not in sync with its remote counterpart;

    * displays the custom annotations (see help on :bash:`format` and :bash:`anno`) next to each branch, if present;

    * displays the output of :bash:`machete-status-branch` hook (see help on :bash:`hooks`), if present;

    * optionally lists commits introduced on each branch if :bash:`-l/--list-commits` or :bash:`-L/--list-commits-with-hashes` is supplied.

The currently checked-out branch is underlined.

In case of yellow edge, use :bash:`-l` flag to show the exact location of the inferred fork point
(which indicates e.g. what range of commits is going to be rebased when the branch is updated).
The inferred fork point can be always overridden manually, see help on :bash:`fork-point`.

Grey/dimmed edge suggests that the downstream branch can be slid out (see help on :bash:`slide-out` and :bash:`traverse`).

Using colors can be disabled with a :bash:`--color` flag set to :bash:`never`.
With :bash:`--color=always`, git machete always emits colors and with :bash:`--color=auto`, it emits colors only when standard output is connected to a terminal.
:bash:`--color=auto` is the default. When colors are disabled, relation between branches is represented in the following way:

|  <branch0>
|  \|
|  o-<branch1>  # green (in sync with parent)
|  \| \|
|  \| x-<branch2> # red (not in sync with parent)
|  \|   \|
|  \|   ?-<branch3> # yellow (in sync with parent, but parent is not the fork point)
|  \|
|  m-<branch4> # grey (merged to parent)

Options:
  --color=WHEN                      Colorize the output; WHEN can be :bash:`always`, :bash:`auto` (default; i.e. only if stdout is a terminal), or :bash:`never`.

  -l, --list-commits                Additionally list the commits introduced on each branch.

  -L, --list-commits-with-hashes    Additionally list the short hashes and messages of commits introduced on each branch.

  --no-detect-squash-merges         Only consider "strict" (fast-forward or 2-parent) merges, rather than rebase/squash merges,
                                    when detecting if a branch is merged into its upstream (parent).

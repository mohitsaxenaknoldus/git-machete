.. role:: bash(code)

.. _discover:

discover
--------
Usage:

.. code-block:: shell

    git machete discover [-C|--checked-out-since=<date>] [-l|--list-commits] [-r|--roots=<branch1>,<branch2>,...] [-y|--yes]

Discovers and displays tree of branch dependencies using a heuristic based on reflogs and asks whether to overwrite the existing definition file with the new discovered tree.
If confirmed with a :bash:`y[es]` or :bash:`e[dit]` reply, backs up the current definition file (if it exists) as :bash:`$GIT_DIR/machete~` and saves the new tree under the usual :bash:`$GIT_DIR/machete` path.
If the reply was :bash:`e[dit]`, additionally an editor is opened (as in :bash:`git machete edit`) after saving the new definition file.

Options:
  -C, --checked-out-since=<date>   Only consider branches checked out at least once since the given date. <date> can be e.g. :bash:`2 weeks ago` or :bash:`2020-06-01`, as in :bash:`git log --since=<date>`. If not present, the date is selected automatically so that around 10 branches are included.

  -l, --list-commits               When printing the discovered tree, additionally lists the messages of commits introduced on each branch (as for :bash:`git machete status`).

  -r, --roots=<branch1,...>       Comma-separated list of branches that should be considered roots of trees of branch dependencies.If not present, :bash:`master` is assumed to be a root. Note that in the process of discovery, certain other branches can also be additionally deemed to be roots as well.

  -y, --yes                        Don't ask for confirmation before saving the newly-discovered tree.
                                   Mostly useful in scripts; not recommended for manual use.

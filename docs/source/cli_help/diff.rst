.. role:: bash(code)

.. _diff:

diff
----
Usage:

.. code-block:: shell

    git machete d[iff] [-s|--stat] [<branch>]

Runs :bash:`git diff` of the given branch tip against its fork point or, if none specified, of the current working tree against the fork point of the currently checked out branch.
See :bash:`git machete help fork-point` for more details on meaning of the "fork point".

Note: the branch in question does not need to occur in the definition file.

Options:
  -s, --stat    Makes :bash:`git machete diff` pass :bash:`--stat` option to :bash:`git diff`, so that only summary (diffstat) is printed.

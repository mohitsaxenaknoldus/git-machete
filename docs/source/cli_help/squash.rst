.. role:: bash(code)

.. _squash:

squash
------
Usage:

.. code-block:: shell

    git machete squash [-f|--fork-point=<fork-point-commit>]

Squashes the commits belonging uniquely to the current branch into a single commit.
The chunk of the history to be squashed starts at the automatically computed fork point of the current branch by default, but can also be set explicitly by :bash:`--fork-point`.
See :bash:`git machete help fork-point` for more details on meaning of the "fork point".
The message for the squashed is taken from the earliest squashed commit, i.e. the commit directly following the fork point.

Note: the current reapplied branch does not need to occur in the definition file.

Tip: for more complex scenarios that require rewriting the history of current branch, see :bash:`reapply` and :bash:`update`.

Options:
  -f, --fork-point=<fork-point-commit>   Specifies the alternative fork point commit after which the squashed part of history is meant to start.

.. role:: bash(code)

.. _file:

file
----
Usage:

.. code-block:: shell

    git machete file

Outputs the absolute path of the machete definition file. Currently fixed to :bash:`<git-directory>/machete`.
Note: this won't always be just :bash:`<repo-root>/.git/machete` since e.g. submodules and worktrees have their git directories in different location.

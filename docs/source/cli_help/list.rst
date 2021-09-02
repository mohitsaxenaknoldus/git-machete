.. role:: bash(code)

.. _list:

list
----
Usage:

.. code-block:: shell

    git machete list <category>
where <category> is one of: :bash:`addable`, :bash:`managed`, :bash:`slidable`, :bash:`slidable-after <branch>`, :bash:`unmanaged`, :bash:`with-overridden-fork-point`.

Lists all branches that fall into one of the specified categories:
    * :bash:`addable`: all branches (local or remote) than can be added to the definition file,
    * :bash:`managed`: all branches that appear in the definition file,
    * :bash:`slidable`: all managed branches that have an upstream and can be slid out with :bash:`slide-out` command
    * :bash:`slidable-after <branch>`: the downstream branch of the <branch>, if it exists and is the only downstream of <branch> (i.e. the one that can be slid out immediately following <branch>),
    * :bash:`unmanaged`: all local branches that don't appear in the definition file,
    * :bash:`with-overridden-fork-point`: all local branches that have a fork point override set up (even if this override does not affect the location of their fork point anymore).

This command is generally not meant for a day-to-day use, it's mostly needed for the sake of branch name completion in shell.

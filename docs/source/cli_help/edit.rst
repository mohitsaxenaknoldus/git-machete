.. role:: bash(code)

.. _edit:

edit
----
Usage:

.. code-block:: shell

    git machete e[dit]

Opens an editor and lets you edit the definition file manually.

The editor is determined by checking up the following locations:
    * :bash:`$GIT_MACHETE_EDITOR`
    * :bash:`$GIT_EDITOR`
    * :bash:`$(git config core.editor)`
    * :bash:`$VISUAL`
    * :bash:`$EDITOR`
    * :bash:`editor`
    * :bash:`nano`
    * :bash:`vi`
and selecting the first one that is defined and points to an executable file accessible on :bash:`PATH`.

Note that the above editor selection only applies for editing the definition file,
but not for any other actions that may be indirectly triggered by git-machete, including editing of rebase TODO list, commit messages etc.

The definition file can be always accessed and edited directly under path returned by :bash:`git machete file` (currently fixed to <git-directory>/machete).

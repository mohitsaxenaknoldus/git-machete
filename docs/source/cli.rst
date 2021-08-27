
.. _cli:

Command Line Interface
=======================================

.. highlight:: console

When git-machete is installed it is added to your path, so it can be called from command line: `git-machete some_command some_command_options`. git-machete comes with a wide variety of commands and their options and in this site you can find their documentation.

git-machete commands:

* :ref:`add` -- Add a branch to the tree of branch dependencies.
* :ref:`advance` -- Fast-forward merge one of children to the current branch and then slide out this child
* :ref:`anno` -- Manage custom annotations
* :ref:`delete-unmanaged` -- Delete local branches that are not present in the definition file`
* :ref:`diff` -- Diff current working directory or a given branch against its computed fork point
* :ref:`discover` -- Automatically discover tree of branch dependencies
* :ref:`edit` -- Edit the definition file
* :ref:`file` -- Display the location of the definition file
* :ref:`fork-point` -- Display or override fork point for a branch
* :ref:`format` -- Display docs for the format of the definition file
* :ref:`github` -- Create, retarget and manage GitHub PRs while keeping them reflected in git machete
* :ref:`go` -- Check out the branch relative to the position of the current branch, accepts down/first/last/next/root/prev/up argument
* :ref:`help` -- Display this overview, or detailed help for a specified command
* :ref:`hooks` -- Display docs for the extra hooks added by git machete
* :ref:`is-managed` -- Check if the current branch is managed by git machete (mostly for scripts)
* :ref:`list` -- List all branches that fall into one of pre-defined categories (mostly for internal use)
* :ref:`log` -- Log the part of history specific to the given branch
* :ref:`reapply` -- Rebase the current branch onto its computed fork point
* :ref:`show` -- Show name(s) of the branch(es) relative to the position of a branch, accepts down/first/last/next/root/prev/up argument
* :ref:`slide-out` -- Slide out the current branch and sync its downstream (child) branches with its upstream (parent) branch via rebase or merge
* :ref:`squash` -- Squash the unique history of the current branch into a single commit
* :ref:`status` -- Display formatted tree of branch dependencies, including info on their sync with upstream branch and with remote
* :ref:`traverse` -- Walk through the tree of branch dependencies and rebase, merge, slide out, push and/or pull each branch one by one
* :ref:`update` -- Sync the current branch with its upstream (parent) branch via rebase or merge
* :ref:`version` -- Display the version and exit

To get help via CLI run:

    $ git-machete help
    $ git-machete help go
    $ git-machete go --help

.. _add:
.. include:: cli_help/add.rst

.. _advance:
.. include:: cli_help/advance.rst

.. _anno:
.. include:: cli_help/anno.rst

.. _delete-unmanaged:
.. include:: cli_help/delete-unmanaged.rst

.. _diff:
.. include:: cli_help/diff.rst

.. _discover:
.. include:: cli_help/discover.rst

.. _edit:
.. include:: cli_help/edit.rst

.. _file:
.. include:: cli_help/file.rst

.. _fork-point:
.. include:: cli_help/fork-point.rst

.. _format:
.. include:: cli_help/format.rst

.. _github:
.. include:: cli_help/github.rst

.. _go:
.. include:: cli_help/go.rst

.. _help:
.. include:: cli_help/help.rst

.. _hooks:
.. include:: cli_help/hooks.rst

.. _is-managed:
.. include:: cli_help/is-managed.rst

.. _list:
.. include:: cli_help/list.rst

.. _log:
.. include:: cli_help/log.rst

.. _reapply:
.. include:: cli_help/reapply.rst

.. _show:
.. include:: cli_help/show.rst

.. _slide-out:
.. include:: cli_help/slide-out.rst

.. _squash:
.. include:: cli_help/squash.rst

.. _status:
.. include:: cli_help/status.rst

.. _traverse:
.. include:: cli_help/traverse.rst

.. _update:
.. include:: cli_help/update.rst

.. _version:
.. include:: cli_help/version.rst

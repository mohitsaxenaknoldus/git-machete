.. role:: bash(code)

.. _format:

format
------
Note: there is no 'git machete format' command as such; 'format' is just a topic of 'git machete help'.

The format of the definition file should be as follows:

|  develop
|      adjust-reads-prec PR #234
|          block-cancel-order PR #235
|              change-table
|                  drop-location-type
|      edit-margin-not-allowed
|          full-load-gatling
|      grep-errors-script
|  master
|      hotfix/receipt-trigger PR #236

In the above example :bash:`develop` and :bash:`master` are roots of the tree of branch dependencies.
Branches :bash:`adjust-reads-prec`, :bash:`edit-margin-not-allowed` and :bash:`grep-errors-script` are direct downstream branches for :bash:`develop`.
:bash:`block-cancel-order` is a downstream branch of :bash:`adjust-reads-prec`, :bash:`change-table` is a downstream branch of :bash:`block-cancel-order` and so on.

Every branch name can be followed (after a single space as a delimiter) by a custom annotation - a PR number in the above example.
The annotations don't influence the way :bash:`git machete` operates other than that they are displayed in the output of the :bash:`status` command.
Also see help for the :bash:`anno` command.

Tabs or any number of spaces can be used as indentation.
It's only important to be consistent wrt. the sequence of characters used for indentation between all lines.

.. role:: bash(code)

.. _advance:

advance
-------
Usage:

.. code-block:: shell

    git machete advance [-y|--yes]

Fast forwards (as in :bash:`git merge --ff-only`) the current branch :bash:`C` to match its downstream :bash:`D`,
and subsequently slides out :bash:`D`. Both steps require manual confirmation unless :bash:`-y/--yes` is provided.

The downstream :bash:`C` is selected according to the following criteria:
    * if :bash:`C` has exactly one downstream branch :bash:`d` whose tip is a descendant of :bash:`C`, and whose fork point is equal to :bash:`C` or is overridden
      (basically: there's a green edge between :bash:`C` and :bash:`d`), then :bash:`d` is selected as :bash:`D`,
    * if :bash:`C` has no downstream branches connected with a green edge to :bash:`C`, then :bash:`advance` fails,
    * if :bash:`C` has more than one downstream branch connected with a green edge to :bash:`C`,
      then user is asked to pick the branch to fast-forward merge into (similarly to what happens in :bash:`git machete go down`).
If :bash:`--yes` is specified, then :bash:`advance` fails.

As an example, if :bash:`git machete status --color=never --list-commits` is as follows:

|  master
|  \|
|  m-develop *
|    \|
|    \| Enable adding remote branch in the manner similar to git checkout
|    o-feature/add-from-remote
|    \| \|
|    \| \| Add support and sample for machete-post-slide-out hook
|    \| o-feature/post-slide-out-hook
|    \|
|    \| Remove support for Python 2
|    \| Remove support for Python 2 - 1st round of fixes
|    ?-chore/v3
|    \|
|    \| Apply Python2-compatible static typing
|    x-feature/types

then running :bash:`git machete advance` will fast-forward the current branch :bash:`develop` to match :bash:`feature/add-from-remote`, and subsequently slide out the latter.
After :bash:`advance` completes, :bash:`status` will show:

|  master
|  \|
|  \| Enable adding remote branch in the manner similar to git checkout
|  o-develop *
|    \|
|    \| Add support and sample for machete-post-slide-out hook
|    o-feature/post-slide-out-hook
|    \|
|    \| Remove support for Python 2
|    \| Remove support for Python 2 - 1st round of fixes
|    ?-chore/v3
|    \|
|    \| Apply Python2-compatible static typing
|    x-feature/types

Note that the current branch after the operation is still :bash:`develop`, just pointing to :bash:`feature/add-from-remote`'s tip now.

Options:
  -y, --yes         Don't ask for confirmation whether to fast-forward the current branch or whether to slide-out the downstream. Fails if the current branch has more than one green-edge downstream branch.


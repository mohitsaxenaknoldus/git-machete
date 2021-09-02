.. role:: bash(code)

.. _traverse:

traverse
--------
Usage:
::
    git machete traverse [-F|--fetch] [-l|--list-commits] [-M|--merge]
                         [-n|--no-edit-merge|--no-interactive-rebase] [--no-detect-squash-merges]
                         [--[no-]push] [--[no-]push-untracked]
                         [--return-to=WHERE] [--start-from=WHERE] [-w|--whole] [-W] [-y|--yes]

Traverses the branch dependency tree in pre-order (i.e. simply in the order as they occur in the definition file) and for each branch:

    * detects if the branch is merged to its parent/upstream:

      - by commit equivalency (default), or by strict detection of merge commits (if :bash:`--no-detect-squash-merges` passed),
      - if so, asks the user whether to slide out the branch from the dependency tree (typically branches are longer needed after they're merged);

    * otherwise, if the branch is not in "green" sync with its parent/upstream (see help for :bash:`status`):
      - asks the user whether to rebase (default) or merge (if :bash:`--merge` passed) the branch onto into its upstream branch - equivalent to :bash:`git machete update` with no :bash:`--fork-point` option passed;

    * if the branch is not tracked on a remote, is ahead of its remote counterpart, or diverged from the counterpart & has newer head commit than the counterpart:

      - asks the user whether to push the branch (possibly with :bash:`--force-with-lease` if the branches diverged);

    * otherwise, if the branch diverged from the remote counterpart & has older head commit than the counterpart:

      - asks the user whether to :bash:`git reset --keep` the branch to its remote counterpart

    * otherwise, if the branch is behind its remote counterpart:

      - asks the user whether to pull the branch;

    * and finally, if any of the above operations has been successfully completed:
      - prints the updated :bash:`status`.

Note that even if the traverse flow is stopped (typically due to merge/rebase conflicts), running :bash:`git machete traverse` after the merge/rebase is finished will pick up the walk where it stopped.
In other words, there is no need to explicitly ask to "continue" as it is the case with e.g. :bash:`git rebase`.

Options:
  -F, --fetch                  Fetch the remotes of all managed branches at the beginning of traversal (no :bash:`git pull` involved, only :bash:`git fetch`).

  -l, --list-commits           When printing the status, additionally list the messages of commits introduced on each branch.

  -M, --merge                  Update by merge rather than by rebase.

  -n                           If updating by rebase, equivalent to :bash:`--no-interactive-rebase`. If updating by merge, equivalent to :bash:`--no-edit-merge`.

  --no-detect-squash-merges    Only consider "strict" (fast-forward or 2-parent) merges, rather than rebase/squash merges,
                               when detecting if a branch is merged into its upstream (parent).

  --no-edit-merge              If updating by merge, skip opening the editor for merge commit message while doing :bash:`git merge` (i.e. pass :bash:`--no-edit` flag to underlying :bash:`git merge`).
                               Not allowed if updating by rebase.

  --no-interactive-rebase      If updating by rebase, run :bash:`git rebase` in non-interactive mode (without :bash:`-i/--interactive` flag).
                               Not allowed if updating by merge.

  --no-push                    Do not push any (neither tracked nor untracked) branches to remote, re-enable via :bash:`--push`.

  --no-push-untracked          Do not push untracked branches to remote, re-enable via :bash:`--push-untracked`.

  --push                       Push all (both tracked and untracked) branches to remote - default behavior.

  --push-untracked             Push untracked branches to remote - default behavior.

  --return-to=WHERE            Specifies the branch to return after traversal is successfully completed; WHERE can be :bash:`here` (the current branch at the moment when traversal starts),
                               :bash:`nearest-remaining` (nearest remaining branch in case the :bash:`here` branch has been slid out by the traversal)
                               or :bash:`stay` (the default - just stay wherever the traversal stops).
                               Note: when user quits by :bash:`q/yq` or when traversal is stopped because one of git actions fails, the behavior is always :bash:`stay`.

  --start-from=WHERE           Specifies the branch to start the traversal from; WHERE can be :bash:`here` (the default - current branch, must be managed by git-machete),
                               :bash:`root` (root branch of the current branch, as in :bash:`git machete show root`) or :bash:`first-root` (first listed managed branch).

  -w, --whole                  Equivalent to :bash:`-n --start-from=first-root --return-to=nearest-remaining`;
                               useful for quickly traversing & syncing all branches (rather than doing more fine-grained operations on the local section of the branch tree).

  -W                           Equivalent to :bash:`--fetch --whole`; useful for even more automated traversal of all branches.

  -y, --yes                    Don't ask for any interactive input, including confirmation of rebase/push/pull. Implies :bash:`-n`.

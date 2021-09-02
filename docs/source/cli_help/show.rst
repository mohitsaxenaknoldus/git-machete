.. role:: bash(code)

.. _show:

show
----
Usage:

.. code-block:: shell

    git machete show <direction> [<branch>]<
where <direction> is one of: :bash:`c[urrent]`, :bash:`d[own]`, :bash:`f[irst]`, :bash:`l[ast]`, :bash:`n[ext]`, :bash:`p[rev]`, :bash:`r[oot]`, :bash:`u[p]`
displayed relative to given <branch>, or the current checked out branch if <branch> is unspecified.

Outputs name of the branch (or possibly multiple branches, in case of :bash:`down`) that is:

    * :bash:`current`: the current branch; exits with a non-zero status if none (detached HEAD)
    * :bash:`down`:    the direct children/downstream branch of the given branch.
    * :bash:`first`:   the first downstream of the root branch of the given branch (like :bash:`root` followed by :bash:`next`), or the root branch itself if the root has no downstream branches.
    * :bash:`last`:    the last branch in the definition file that has the same root as the given branch; can be the root branch itself if the root has no downstream branches.
    * :bash:`next`:    the direct successor of the given branch in the definition file.
    * :bash:`prev`:    the direct predecessor of the given branch in the definition file.
    * :bash:`root`:    the root of the tree where the given branch is located. Note: this will typically be something like :bash:`develop` or :bash:`master`, since all branches are usually meant to be ultimately merged to one of those.
    * :bash:`up`:      the direct parent/upstream branch of the given branch.

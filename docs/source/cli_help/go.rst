.. role:: bash(code)

.. _go:

go
--
Usage:

.. code-block:: shell

    git machete g[o] <direction>
where <direction> is one of: :bash:`d[own]`, :bash:`f[irst]`, :bash:`l[ast]`, :bash:`n[ext]`, :bash:`p[rev]`, :bash:`r[oot]`, :bash:`u[p]`

Checks out the branch specified by the given direction relative to the current branch:
    * :bash:`down`:    the direct children/downstream branch of the current branch.
    * :bash:`first`:   the first downstream of the root branch of the current branch (like :bash:`root` followed by :bash:`next`), or the root branch itself if the root has no downstream branches.
    * :bash:`last`:    the last branch in the definition file that has the same root as the current branch; can be the root branch itself if the root has no downstream branches.
    * :bash:`next`:    the direct successor of the current branch in the definition file.
    * :bash:`prev`:    the direct predecessor of the current branch in the definition file.
    * :bash:`root`:    the root of the tree where the current branch is located. Note: this will typically be something like :bash:`develop` or :bash:`master`, since all branches are usually meant to be ultimately merged to one of those.
    * :bash:`up`:      the direct parent/upstream branch of the current branch.

Roughly equivalent to :bash:`git checkout $(git machete show <direction>)`.

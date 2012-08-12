Git
===

Git is a distributed version control system. Each application on
Cloudnode has its own repository. On every push command the Node VM is
updated with the latest version of your application. An automatic
restart ensures that the most recent version goes live after the push
command completes.

Cloudnode Remote Branches Special Directories Submodules

Cloudnode Remote
~~~~~~~~~~~~~~~~

When creating a new Cloudnode App with the command line client, a Git
remote pointing to Cloudnode is automatically configured. If you wish to
configure the remote manually or re-add the remote under a different
name, you can:

::

    $ git remote add cloudnode git@cloudno.de:demoapp.git

In this example Cloudnode (the third argument to git) is the name of the
remote and demoapp should be replaced with your app name.

Branches

Cloudnode will ignore branches other than master if they are pushed.
Only the master branch is used for deployment.

You can, of course, push any local branch to the master branch of the
Cloudnode remote. The syntax for that is:

::

    $ git push cloudnode demobranch:master

In this example Cloudnode (the second argument to git) is the name of
the remote and demobranch is the name of the local branch being deployed
to Cloudnode.

Special Directories
~~~~~~~~~~~~~~~~~~~

A couple directories are handled specially by the Cloudnode app compiler
when receiving your app code. The following directories will be ignored
if they exist in your Git repository, so they can be used by the
platform for special purposes:

mnt/ Used for mounting your app's Cloud Storage. log/ Used for log
collection. See Logging for details and usage. tmp/ Writeable directory
available for transient file storage. See Platform Prerequisites for
details and usage.

Submodules
~~~~~~~~~~

Git submodules are supported on the Cloudnode platform.

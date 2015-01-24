Git
===

Git is a distributed version control system. Each application on
Cloudnode has its own repository. On every push command the Node VM is
updated with the latest version of your application. An automatic
restart ensures that the most recent version goes live after the push
command completes.

-  :ref:`cloudnode-remote`
-  :ref:`branches`
-  :ref:`special-directories`
-  :ref:`submodules`

.. _cloudnode-remote:

Cloudnode Remote
~~~~~~~~~~~~~~~~

When creating a new Cloudnode app with the command line client, a Git
remote pointing to Cloudnode is automatically configured. If you wish to
configure the remote manually or re-add the remote under a different
name, you can use the Git remote command. The remote repository URL (SSH or HTTPS)
is displayed in the application details.

::

    $ git remote add cloudnode https://git.cloudno.de/demoapp.git

In this example Cloudnode (the third argument to git) is the name of the
remote and demoapp should be replaced with your app name.

.. _branches:

Branches
~~~~~~~~

Cloudnode will ignore branches other than master if they are pushed.
Only the master branch is used for deployment.

You can, of course, push any local branch to the master branch of the
Cloudnode remote. The syntax for that is:

::

    $ git push cloudnode demobranch:master

In this example Cloudnode (the second argument to git) is the name of
the remote and demobranch is the name of the local branch being deployed
to Cloudnode.

.. _special-directories:

Special Directories
~~~~~~~~~~~~~~~~~~~

A couple directories are handled specially by the Cloudnode app compiler
when receiving your app code. The following directories will be ignored
if they exist in your Git repository, so they can be used by the
platform for special purposes:

**/mnt** - Used for mounting your app's Cloud Storage.

**/log** - Used for log collection. See Logging for details and usage.

**/tmp** - Writeable directory available for transient file storage. See Platform Prerequisites for
details and usage.

.. _submodules:

Submodules
~~~~~~~~~~

Git submodules are supported on the Cloudnode platform.

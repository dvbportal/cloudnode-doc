Prerequisites
=============

Since Cloudnode is a cloud hosting environment, your app must conform to
a couple different requirements and prerequisites in order to run on it.
By following these best practices in app architecture and design, you
can ensure that your app will run well on the Cloudnode platform.

-  :ref:`required-software`
-  :ref:`best-practices`
-  :ref:`read-only-filesystem`
-  :ref:`logs`
-  :ref:`dependency-management`
-  :ref:`app-initialization`
-  :ref:`git-pre`

.. _required-software:

Required Software
-----------------

The workflow used to develop and deploy apps on Cloudnode depends on
Git, Node.js, npm and our command line client, which in fact is a node
app itself. The tools are available for all major OS'es. See the
following links

-  git - \ http://git-scm.com/\  - The distributed version control
   system
-  node.js - \ http://nodejs.org\  - The node server
-  cloudnode (optional) - **npm install cloudnode-cli -g** - The `Cloudnode command
   line </cloudnode-command-line>`_

.. _best-practices:

Best Practices
--------------

Take care to keep the size of your app small.

Do not include large files (documents, media files, data files, etc.) in
your app. These should be hosted on an outside asset store such as
Amazon S3.

Only include modules that you will use.

Sensitive data and passwords
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Make sure to keep sensitive data outside of your code. It is recommended
to store sensitive data using `environment variables </api#env>`_.

.. _read-only-filesystem:

Read-only Filesystem
--------------------

Cloudnode apps are not able to write to file filesystem in general.
However there are a couple special locations to which you can write
files.

Cloud storage (/mnt)
~~~~~~~~~~~~~~~~~~~~

All Cloudnode apps have access to limited persistent file storage under
/mnt. Cloud storage is persistent between requests and app instances.

Cloud storage is designed to store files generated from within your app
(e.g. generated stylesheets or asset packages). See `Cloud
Storage </cloud-storage>`_ for details.

Temporary files (/tmp)
~~~~~~~~~~~~~~~~~~~~~~

The /tmp directory in your app root is writeable (for files of
reasonable size), but anything written to it should not be expected to
endure over hours.

.. _logs:

Logs
----

Logs on the Cloudnode platform should be considered transient. It is
possible to tail the last several 100 lines through the command line
or the dashboard.

See :ref:`troubleshooting` for full details.

.. _dependency-management:

Dependency Management
---------------------

If your app depends on any npm packages, they need to be installed into
your Node VM. The easiest way is to list them in the "package.json" file.
See `Node package manager </node-package-manager>`_ for details.

.. _app-initialization:

App Initialization
------------------

Node looks for a startup file normally called **server.js** to boot your
application. You can choose a different file and directory, when you
create the application. For details see the `Cloudnode command
line </cloudnode-command-line>`_.

.. _git-pre:

Git
---

\ `Git <http://git-scm.com>`_\  is the only way to push code to
Cloudnode for deployment. This means your app must be part of a Git
repository. You don’t necessarily need to use Git for version control
during development, but when it comes time to deploy to Cloudnode, your
app code does need to be committed to a Git repo.

Deployment is as easy as **git push origin master**. See the `Quick
Start Guide </quick-start-guide>`_ for more details.

For additional help on using Git see the excellent help files at GitHub
especially the setup and troubleshooting guides when using ssh key and
key phrases: \ http://help.github.com/\

Git Submodules
~~~~~~~~~~~~~~

Git submodules are supported on the Cloudnode platform.

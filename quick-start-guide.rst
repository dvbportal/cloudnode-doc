Quick Start Guide
=================

If this is your first time using Cloudnode, be sure to first install the
command line client and look over the platform prerequisites before
proceeding. Also, make sure you have a working Node installation,
otherwise any node commands listed below will not work.

-  :ref:`create-new-app`
-  :ref:`init-new-node`
-  :ref:`commit-new-node`

.. _create-new-app:

Create a new cloudnode app
--------------------------

Go to \ `My Apps <https://cloudno.de/myapps>`_\ , click on ``New
Application`` and fill in the form. This will actually:

-  Create a new sub-domain for your application
-  Provision a virtual machine for your application
-  Setup a git repository to hold your application code

.. _init-new-node:

Initialize your local working copy
----------------------------------

The easiest way is to use the `command line
client <cloudnode-command-line.html>`_ to setup your local working copy. If
this is the first time you are using the command line client make sure
to enter your credentials first, or you will get the error ``ERROR [HTTP
401] No authentication data sent``. Details on installing and entering
the credentials can be found `here <cloudnode-command-line.html>`_.

.. note:: **Important note for Windows users:** The ``cloudnode app init`` command
   is not yet supported. Please execute the steps 1.-7. one by one because
   git automation is not yet supported.

::

    $ cloudnode app init <app name>
    cloudnode info initializing git repo for <app name> into folder <app name>
    cloudnode info cloning the repo git clone cloudnode@git.cloudno.de:/git.. .git <app name>
    cloudnode info clone complete
    cloudnode info writing app data to config
    cloudnode info writing app files
    cloudnode info processing the initial commit
    cloudnode info attemping to start the new app.
    cloudnode info hello started.
    cloudnode info Some helpful app commands:

     cd ./<app name>
     curl http://<app name>.cloudno.de/
      cloudnode app info
      cloudnode app logs
      cloudnode app stop|start|restart

This single command automates the following steps, which could also have
been executed instead:

1. Create a local sub directory for the application
2. Initialize a local repository (git init)
3. Clone the remote repo and the the remote origin URL (git clone ...)
4. Create a sample server.js file with a simple ``Hello World``
   application
5. Add the new file to the local repository (git add .)
6. Commit the changes (git commit -am "Initial commit")
7. Push the changes live (git push origin master)

You can also launch the application locally to see if it works by
running **node server.js** and navigating to http://127.0.0.1:8080/ in
a web browser. Use any port number and IP address; they will be
transparently overridden when your app is deployed on Cloudnode.

.. _commit-new-node:

Commit to your new app and deploy
---------------------------------

To commit changes to your application use the normal git workflow:

-  Edit your files (vi server.js)
-  Commit the changes (git commit -am "Change log")
-  Push the changes online (git push origin master)

Commit the changes
~~~~~~~~~~~~~~~~~~

::

    $ git commit -am "Message changed"
    Created commit f57b7a0: Message changed
    1 files changed, 1 insertions(+), 1 deletions(-)

Push the changes online
~~~~~~~~~~~~~~~~~~~~~~~

::

    $ git push origin master
    Counting objects: 5, done.
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 315 bytes, done.
    Total 3 (delta 1), reused 0 (delta 0)
    To cloudnode@git.cloudno.de:/git/hs/62-6fc0d44abf9974b91625cc10ff118871.git
     5f3a0f9..f57b7a0  master -> master
    Syncing repo with your node VM
    From /git/hs/62-6fc0d44abf9974b91625cc10ff118871.git/.
     5f3a0f9..f57b7a0  master     -> origin/master
    Updating 5f3a0f9..f57b7a0
    Fast forward
     server.js |    2 +-
     1 files changed, 1 insertions(+), 1 deletions(-)

    ====  Compiling hello...
    ====  Restarting your app: hello
    ====  App restarted
    ====  App successfully deployed to http://hello.cloudno.de

      Finished.

Now your new version is deployed on Cloudnode and the application has
been restarted. You can see it running in your browser at the
.cloudno.de URL listed in the push output.

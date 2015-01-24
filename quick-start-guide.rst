Quick Start Guide
=================

If this is your first time using Cloudnode, be sure to first install Git
and look over the `platform prerequisites <prerequisites.html>`_
before proceeding. Also, make sure you have a working Node.js installation,
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

Method 1:

Git is the only tool you need to push your app online. First clone the empty repository
that has been created in the last step. Lookup the HTTPS clone URL from the
application details and use Git to clone a local copy:

::

    $ git clone https://git.cloudno.de/git/<user>/1924-b4..5f.git hello
    Cloning into 'hello'...
    Username for 'https://git.cloudno.de': <user>
    Password for 'https://<user>@git.cloudno.de': <password>
    warning: You appear to have cloned an empty repository.
    Checking connectivity... done.

.. note:: Use your Cloudnode user name as <user> and your API key as <password>.
   The API key is shown in your `account details <https://cloudno.de/account?admin>`_.

Once your local copy is setup, continue with :ref:`commit-new-node`.

Method 2:

Use the `command line client <cloudnode-command-line.html>`_ to setup your local working copy. If
this is the first time you are using the command line client make sure
to enter your credentials first, or you will get the error ``ERROR [HTTP
401] No authentication data sent``. Details on installing and entering
the credentials can be found `here <cloudnode-command-line>`_.


.. note:: **Important note for Windows users:** The ``cloudnode app init`` command
   is not yet supported. Please use method 1 to initialize your working copy.

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
3. Clone the empty repository from the remote origin URL (git clone ...)
4. Create a sample server.js file with a simple ``Hello World``
   application
5. Add the new file to the local repository (git add .)
6. Commit the changes (git commit -m "Initial commit")
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
-  Stage the changes (git add .)
-  Commit the changes (git commit -m "Change log")
-  Push the changes online (git push origin master)

Hello World sample (server.js)
------------------------------

.. code-block:: javascript

    //
    // This simple web server written in Node responds with "Hello World" for every request.
    //
    var http = require('http');
    var util = require('util');
    var app_port = process.env.app_port || 8080;
    var app_host = process.env.app_host || '127.0.0.1';

    http.createServer(function(req, res) {
        res.writeHead(200, {'Content-Type': 'text/plain'});
        res.write('Hello World from Cloudnode\n\n');
        res.end();
    }).listen(app_port);
    console.log('Web server running at http://' + app_host + ':' + app_port);

Package.json
~~~~~~~~~~~~

Though not strictly required, it is a good idea to add a package.json file to your project.
Later when you are using pre-built modules like express, you can add these dependencies in
the corresponding section and the platform will use `npm </node-package-manager>`_ to add
those dependencies when deploying.

.. code-block:: json

  {
    "name": "helloworld",
    "version": "0.0.1",
    "private": true,
    "dependencies": {
    }
  }

Commit the changes
~~~~~~~~~~~~~~~~~~

::

    $ git add .
    $ git commit -m "Initial commit"
    Created commit f57b7a0: Message change
    1 files changed, 1 insertions(+), 1 deletions(-)

Push the changes online
~~~~~~~~~~~~~~~~~~~~~~~

::

    $ git push origin master
    Counting objects: 5, done.
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 315 bytes, done.
    Total 3 (delta 1), reused 0 (delta 0)
    To cloudnode@git.cloudno.de:/git/hs/62-6f..71.git
     5f3a0f9..f57b7a0  master -> master
    Syncing repo with your node VM
    From /git/hs/62-6f..71.git/.
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

Your new version is now deployed on Cloudnode and the application has
been restarted. You can see it running in your browser at the
.cloudno.de URL listed in the push output.

Node.js
=======

**Current versions: 0.12, 4.x, 5.x (01/01/16)**

Node.js is a non-blocking, evented I/O framework using the V8 JavaScript
engine.

We host Node.js applications in their own VMs, which we call Node
Machines. Cloudnode is based on the Nodester platform. During the beta
stage, we may need to shut the service down for upgrades or service
without notice. You should join our `community
channel <https://slackin.cloudno.de/>`_ to share any feedback
and get important announcements that can affect running apps.

-  `Preparing for deployment <#preparing>`_
-  `Deploying to Cloudnode <#deploying>`_
-  `Dependencies <#dependencies>`_

.. _preparing:

Preparing for deployment
~~~~~~~~~~~~~~~~~~~~~~~~

You can name the main file of your app like you want. Just make sure to
specify that name, when you use the "create app" command. You can also
specify any port you like as parameter to the listen function (in this
sample port 8124). The platform will transparently override the
parameter with the port of your Node VM which is in effect.

.. code-block:: javascript

    var http = require('http');
    http.createServer(function (req, res) {
      res.writeHead(200, {'Content-Type': 'text/plain'});
      res.end('Hello World\n');
    }).listen(8124, "127.0.0.1");
    console.log('Server running at http://127.0.0.1:8124/');

Whenever a port needs to be specified as a parameter for other function
calls, use the environment variable "app\_port" to use the port in use
by your Node VM like in the following example:

::

    var webrepl = require('webrepl');
    var port = process.env["app_port"];

    webrepl.start(port);
    console.log("Web repl started (Listening on port " + port + ")");

.. _deploying:

Deploying to Cloudnode
~~~~~~~~~~~~~~~~~~~~~~

To create an app with the the Cloudnode command line use the following
command:

::

    $ cloudnode app create <appname> <startfile>
              - Creates a new app named <appname>, <startfile> is optional

Deployment is done with every Git push command. Additionally the
application is restarted to activate the changes introduced with the push
command.

.. _dependencies:

Dependencies
~~~~~~~~~~~~

When your repository includes sub modules, these are also pushed to the
Node Machine.

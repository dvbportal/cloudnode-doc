Cloudnode Command Line
======================

**Current version: 0.2.23 (see also: how to update,
changelog)**

The Cloudnode command line tool is an interface to the `Cloudnode Web
API </api>`_ and includes support for creating apps, reading log files,
managing apps and user accounts, setting up domains, and configuring
apps.

The command line tool is itself a Node.js application the runs on the
client side. See the `Prerequisites </prerequisites>`_ for details.

If you don't want to install software on your local computer, use the
developer shell which comes pre-installed with the command line and many 
more tools.

Installation
------------

If you haven't already done, sign up for a Cloudnode account. You will
need to enter your credentials into the command line tool to authorize
most of the requests.

The command line tool can be installed using
`npm </node-package-manager>`_ which also takes care to resolve
dependencies.

::

    $ npm install cloudnode-cli

The above command does not require root rights and installs the tools in
your home directory. Make sure that your PATH includes
~/node\_modules/.bin If you are root you can install the tools globally
using the -g flag.

Usage
-----

After having installed the client, enter your credentials. This needs to
be done only once. The user name is the same as in your Cloudnode name, the
password is the API key shown on your \ `account
page <https://cloudno.de/account?admin>`_\ .

::

    $ cloudnode user setup <username> <password>

    cloudnode info verifying credentials
    cloudnode info user verified..
    cloudnode info writing user data to config

Now start the client by typing "cloudnode". It will show a list of the
available commands.

::

    $ cloudnode

    cloudnode info showing all available sub commands
    cloudnode status
    cloudnode coupon
    cloudnode apps
    cloudnode app
    cloudnode user
    cloudnode appdomain
    cloudnode domain
    cloudnode npm
    cloudnode appnpm
    cloudnode info For more help, type cloudnode help <command>

The commands are divided into three types: general commands, user and
app commands.

General Commands
~~~~~~~~~~~~~~~~

The status command checks the platform status and displays the number of
hosted and running applications.

::

    $ cloudnode status

The apps command displays all your applications together with their port
and running status.

::

    $ cloudnode apps

User Commands
~~~~~~~~~~~~~

Type "cloudnode user" to get an overview of the commands in this
category:

::

    $ cloudnode user
    cloudnode user register <coupon-code> - Register a user
    cloudnode user setup <username> <password> - Setup this user
    cloudnode user setpass <password>
                   - Set a new password for this user
    cloudnode user setkey </path/to/sshkey>
                   - Set an sshkey (if no argument, ~/.ssh/id_rsa.pub is used)
    cloudnode user create <username> <password> <email address>
                   <file containing ssh public key> <coupon code> - Create a user

App Commands
~~~~~~~~~~~~

Type "cloudnode app" to get an overview of the commands in this
category:

::

    $ cloudnode app
    cloudnode <appname> is not required if inside an app directory after you call setup
    cloudnode app setup <appname> - Configure this app for future app commands
    cloudnode app info <appname> - Returns app specific information
    cloudnode app logs <appname> - Returns app logs
    cloudnode app stop|start|restart <appname> - Controls app status.
    cloudnode app create <appname> <startfile>
                  - Creates a new app named <appname>, <startfile> is optional.
    cloudnode app init <appname> - Fetches the remote repo and sets it up.
    cloudnode app clone <appname> - Fetches the remote repo.

NPM Commands
^^^^^^^^^^^^

Type "cloudnode npm" or "cloudnode appnpm" to get an overview of the
commands in this category:

::

    $ cloudnode npm
    cloudnode All arguments after install|update|uninstall will be sent to npm as packages.
    cloudnode npm install <packages> - Installs the list of specified packages to this app.
    cloudnode npm update <packages> - Update the list of specified packages to this app.
    cloudnode npm uninstall <packages> - Removes the list of specified packages to this app.

Because every node application is running in its own virtual machine,
you need to install every module you application depends on.

Domain Commands
^^^^^^^^^^^^^^^

The domain command are used to setup and manage custom domains for you
appications. See the `Custom Domains </custom-domains>`_ chapter for
additional information on this.

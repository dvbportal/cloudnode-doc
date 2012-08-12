Node Package Manager
====================

**Current version: npm 1.1.4 (03/18/12) (see also: how to update,
changelog)**

Cloudnode uses \ `npm <http://npmjs.org/>`_\  for dependency management.
For an introduction and additional information see the Author's
\ `article on How To
Node <http://howtonode.org/introduction-to-npm>`_\ . If you need more
specific information, the best place to look is npm’s help system
itself, which is very extensive. Just use npm help .

When you application depends on some other modules use the Cloudnode
command line to install the required packages into your VM. Additional
dependencies wil be resolved by npm. If your application requires for
instance express, run the following command:

::

    $ cloudnode npm install express

All arguments after install will be sent to npm as package names. You
can also use the npm command to update and uninstall packages. To get an
overview of all npm commands run "cloudnode npm":

::

    $ cloudnode npm
    cloudnode All arguments after install|update|uninstall will be sent to npm as packages.
    cloudnode npm list - Lists the installed npm packages for this app.
    cloudnode npm install <packages> - Installs the list of specified packages to this app.
    cloudnode npm update <packages> - Update the list of specified packages to this app.
    cloudnode npm uninstall <packages> - Removes the list of specified packages to this app.

Remember that each application runs in its own isolated environment. You
need to handle dependencies for each application individually. When you
want to share program code among your applications and that code might
also be useful for other node users, consider to publish your own npm
package.

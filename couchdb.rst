CouchDB
=======

The Cloudnode platform offers a CouchDB database option to store
persistent data. The database is connected through a fast local network.
We also provide a SSL secured remote connection, which can be used to
access the database remotely or for replication.

CouchDB Administration
~~~~~~~~~~~~~~~~~~~~~~

The "Databases" tab lists your databases. From here you can also
create new databases, delete existing database or manage your databases
using the Futon Web GUI. You can add sharing rules and manage your map
reduce functions. Clicking on a database name opens the database detail
page, where you find your API key and URLs to externally access you
database.

CouchDB Credentials
~~~~~~~~~~~~~~~~~~~

Your app's environment is populated with variables that contain all data
to access the CouchDB. To do so select the CouchDB during application
creation. The environment will receive the follow variables:

-  "DBHOST"="ip address"
-  "DBUSER"="CouchDB user name"
-  "DBPWD"="CouchDB password" (also called CouchDB apikey)

You can check these values from the "Manage App" screen by clicking "Get
Env".

Usage Example
~~~~~~~~~~~~~

We plan to provide example apps that demonstrate how to use Node.js and
CouchDB. We are currently preferring cradle to access CouchDB. Cradle
can be installed using npm. For details on using npm with your Node VM
see `Node package manager </node-package-manger>`_.

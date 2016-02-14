MongoDB
=======

The Cloudnode platform offers a MongoDB database option to store
persistent data. The database is connected through a fast local network.
We also provide access to the Mongo shell and tools through the 
`Developer Shell </cloudnode-developer-shell>`_.

MongoDB Administration
~~~~~~~~~~~~~~~~~~~~~~

The "Databases" tab lists your databases. From here you can also
create new databases, delete existing database or manage your databases
using the Web GUI. Clicking on a database name opens the database detail
page, where you find your API key and URL to connect internally to your
database from your apps. You can also view database and collection metrics.

MongoDB Credentials
~~~~~~~~~~~~~~~~~~~

Your app's environment is populated with variables that contain all data
to access the database. To do so, select the MongoDB during application
creation. The environment will receive the follow variables:

-  "DBHOST"="MongoDB host name"
-  "DBUSER"="MongoDB user name"
-  "DBPWD"="MongoDB password" (also called MongoDB apikey)

You can check these values from the "Manage App" screen by clicking "Get
Env". You are the owner of the database. You can create additional users
and admins using the mongo shell or programmatically from your app. 

MongoDB Backups
~~~~~~~~~~~~~~~

Every database running on the Cloudnode platform is backed up on a daily basis.
The backup are stored for at least 14 days. You can download your backups
from the database details page and store them in another safe place.

Usage Example
~~~~~~~~~~~~~

We plan to provide example apps that demonstrate how to use Node.js and
MongoDB. We are currently preferring `mongoose <http://mongoosejs.com/>`_ to access MongoDB. 
Mongoose can be installed using npm. For details on using npm with your Node VM
see `Node package manager </node-package-manger>`_.

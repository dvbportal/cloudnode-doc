Redis
=====

The Cloudnode platform offers fully managed, hosted Redis instances for
your Node.js apps. \ `Redis <http://redis.io>`_\  is an open source,
advanced key-value store. It works out-of-the-box with Express and many
other Node.js apps and modules. The database instances are on a fast
local network connection and offer superior speed compared to other
hosted solutions.

Redis Administration
~~~~~~~~~~~~~~~~~~~~

The "My Databases" tab lists your databases. From here you can also
control your instances, create new Redis instances and delete existing
ones. Clicking on a database name opens the detail page, where you find
your authorization code and port number to access the Redis instance.
From here you can also access log and configuration files and manage the
instance.

Redis Authorization
~~~~~~~~~~~~~~~~~~~

Your app's environment is populated with variables that contain all data
needed to access the Redis Database. Tot do so select the Redis database
during application creation. The environment will receive the following
variables:

-  redis\_host="host name"
-  redis\_port="port number"
-  redis\_auth="autorization code"

You can check these values from the "Manage App" screen by clicking "Get
Env".

Redis Backups
~~~~~~~~~~~~~

Every database running on the Cloudnode platform is backed up on a daily basis.
The backup are stored for at least 14 days. You can download your backups
from the database details page and store them in another safe place.


Usage Example
~~~~~~~~~~~~~

The preferred client package to access Redis is
\ `node\_redis <https://github.com/mranney/node_redis>`_\  by mranney.
It comes with docs and samples.

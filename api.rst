API
===

Cloudnode is build on a RESTful API that allows to execute all commands
from the web frontend, the command line tool or a future client-side
app.

We are currently running the "stable" version of Node.js v0.10.35 and we
support Node.js VMs, we call Cloudnode machines. This means that you can
install your own NPM modules. Git is required to push updates to your
Cloudnode machine. The following API calls are defined:

-  :ref:`api_status`
-  :ref:`api_user`
-  :ref:`api_app`
-  :ref:`api_apps`
-  :ref:`api_env`
-  :ref:`api_npm`
-  :ref:`api_appdomains`
-  :ref:`api_cli-commands`
-  :ref:`api_git`

.. _api_status:

Status
~~~~~~

::

    Get Status :: GET

    /status - Returns platform status and number of apps running

    $ curl https://cloudno.de/status

.. _api_user:

User
~~~~

::

    Register User :: POST (Coupon is required.)

    /user - creates user account (pass in user and password and email
    and id\_rsa.pub string) Ensure that all + in the ssh key are
    substituted for their %2B counter parts, else your key will break.
    Run this on your command line to copy your RSA string and swap out
    the plus signs: "cat ~/.ssh/id\_rsa.pub \| sed s/'+'/'%2B'/g \|
    pbcopy"

    $ curl -X POST -d "user=testuser&password=123& \
      email=chris@cloudno.de&rsakey=ssh-rsa AAAAB3NzaC1yc..." https://cloudno.de/user

::

    Update User :: PUT

    /user - update user account (pass in password and/or RSA key - "cat
    ~/.ssh/id\_rsa.pub \| sed s/'+'/'%2B'/g \| pbcopy")

    $ curl -X PUT -u "testuser:123" -d "password=test" https://api.cloudno.de/user
    $ curl -X PUT -u "testuser:123" -d "rsakey=1234567" https://api.cloudno.de/user

::

    Delete User :: DELETE

    /user - delete user account (requires basic auth)

    $ curl -X DELETE -u "testuser:123" https://api.cloudno.de/user

.. _api_app:

App
~~~

::

    Create Application :: POST

    /app - create nodejs app for hosting (requires basic auth and
    returns the port address required for use along with a git repo to
    push to)

    $ curl -X POST -u "testuser:123" -d "appname=a&start=hello.js" https://api.cloudno.de/app

::

    Change Application :: PUT

    /app - update starting app name (requires basic auth, appname, and
    starting page and returns the port address required for use along
    with a git repo to push to and running status of the app)

    $ curl -X PUT -u "testuser:123" -d "appname=a&start=hello1.js" https://api.cloudno.de/app

::

    Start/Stop Application :: POST

    /app - start and stop your hosted nodejs app (requires basic auth,
    appname, and running=true\|false and returns the port address
    required for use along with a git repo to push to)

    $ curl -X PUT -u "testuser:123" -d "appname=a&running=true" https://api.cloudno.de/app

::

    Delete Application :: DELETE

    /app - delete nodejs app (requires basic auth and appname)

    $ curl -X DELETE -u "testuser:123" -d "appname=test" https://api.cloudno.de/app

::

    Application Information :: GET

    /app/ - get nodejs app info (requires basic auth and appname)

    $ curl -u "testuser:123" https://api.cloudno.de/app/appname

.. _api_apps:

Apps
~~~~

::

    All Applications Information :: GET

    /apps - get all nodejs app info(requires basic auth)

    $ curl -u "testuser:123" https://api.cloudno.de/apps

.. _api_env:

Env
~~~

::

    Create/Update Environment :: PUT

    /env - create/update environment key/value pair (requires basic
    authentication, appname and key/value)

    $ curl -X PUT -u "testuser:123" -d "appname=test&key=color&value=red" https://api.cloudno.de/env

::

    Delete Environment :: DELETE

    /env - delete environment key/value pair (requires basic
    authentication, appname and key/value)

    $ curl -X DELETE -u "testuser:123" -d "appname=test&key=color" https://api.cloudno.de/env

::

    Get Environment :: GET

    /env - get all environment key/value pairs (requires basic
    authentication and appname)

    $ curl -u "testuser:123" https://api.cloudno.de/env/test

.. _api_npm:

NPM
~~~

::

    Install/Upgrade/Uninstall NPM Packages :: POST

    /npm - Allows you to manage the NPM packages for an application.

    $ curl -X POST -u "testuser:123" -d "appname=a&action=install&package=express" \
           https://api.cloudno.de/npm

    $ curl -X POST -u "testuser:123" -d "appname=a&action=update&package=express" \
           https://api.cloudno.de/npm

    $ curl -X POST -u "testuser:123" -d "appname=a&action=uninstall&package=express" \
           https://api.cloudno.de/npm

.. _api_appdomains:

Appdomains - Add DNS A Record
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    Create Application Domain :: POST

    /appdomains - create app domain for hosting example.com (requires
    basic auth)

    $ curl -X POST -u "testuser:123" -d "appname=test&domain=example.com" \
           https://api.cloudno.de/appdomains

::

    Delete Application Domain :: DELETE

    /appdomains - delete app domain for hosting example.com (requires
    basic auth)

    $ curl -X DELETE -u "testuser:123" -d "appname=test&domain=example.com" \
           https://api.cloudno.de/appdomains

::

    Application Domain Information :: GET

    /appdomains - get list of your domains (requires basic auth)

    $ curl -u "testuser:123" https://api.cloudno.de/appdomains

.. _api_cli-commands:

CLI Commands
~~~~~~~~~~~~

You can install our Command Line Interface by running "npm install
cloudnode-cli"

    `cloudnode <command> <param1> <param2>`

Commands are:

::

    $ cloudnode coupon <email address>
    $ cloudnode user create <username> <password> <email address> \
                <file containing ssh public key> <coupon code>
    $ cloudnode user setup <username> <password>

The commands below require you to have run 'user setup' before:

::

    $ cloudnode user setpass <new password>

You should run user setup after running setpass.

::

    $ cloudnode user setkey <file containing ssh public key>
    $ cloudnode apps list
    $ cloudnode app create <app-name> <initial js file>
    $ cloudnode app info <app-name>
    $ cloudnode app logs <app-name>
    $ cloudnode app start <app-name>
    $ cloudnode app restart <app-name>
    $ cloudnode app stop <app-name>
    $ cloudnode app gitreset <app-name>
    $ cloudnode npm install <app-name> <package name>
    $ cloudnode npm upgrade <app-name> <package name>
    $ cloudnode npm uninstall <app-name> <package name>
    $ cloudnode appdomain add <app-name> <domain-name>
    $ cloudnode appdomain delete <app-name> <domain-name>
    $ cloudnode appdomains

.. _api_git:

Git
~~~

Deploying and updating your Node.js application is simple.

::

    $ curl -X POST -u "testuser:123" -d "appname=myapp&start=hello.js" \
           https://api.cloudno.de/app

Upon creating or changing your application via our API, you will receive
a Git repo URL from our API response. Add a Cloudnode remote to your
project as follows:

::

    $ git remote add cloudnode the_url_returned_by_our_api

Finally push your updates to your new Cloudnode environment as follows:

::

    $ git push cloudnode master

Start your application.

::

    $ curl -X PUT -u "testuser:123" -d "appname=myapp&running=true" \
           https://api.cloudno.de/app

Visit your application via http://myapp.cloudno.de

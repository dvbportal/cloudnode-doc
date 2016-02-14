.. _troubleshooting:

Troubleshooting
===============

If you need help with your login or with creating / updating your
application, please see the following guides:

-  :ref:`login`
-  :ref:`api`
-  :ref:`ssh`
-  :ref:`logs`

.. _login:

Login to the Cloudnode web site
-------------------------------

With Cloudnode you don't need to remember passwords, nor you need to
worry about leaked or hacked passwords, because we simply don't use
passwords and rely on OpenID / OAuth instead. Use your existing account
at one of the supported providers to login into our web site.

.. _api:

Using the API / CLI
-------------------

The API uses basic authentication over a secure SSL connection. We plan
to change this as soon as the Nodester platform supports OAuth. The user
name is the same as in your Cloudnode name. Instead of a password an API key is
used. The API key is maintained by the platform and is shown on \ `your
account <https://cloudno.de/account?admin>`_\  page. **You need to
create at least one application to get access to your API key.**

To test the platform and the physical connection, use the status
command:

::

    $ cloudnode status
    cloudnode info checking api status for: api.cloudno.de
    cloudnode info using secure connection
    cloudnode info status up
    cloudnode info appshosted 23
    cloudnode info appsrunning 13

This ensures, that the platform is up and running and that you can open
a secure connection to it.

The next step is to check your credentials by running a command, that
requires authentication.

::

    $ cloudnode apps
    cloudnode info hello on port 8062 running: empty

This command will list all your applications. If you get an ERROR
instead, setup the cloudnode client with your user name and API key as a
password.

::

    $ cloudnode user setup <user name> <api key>
    cloudnode info verifying credentials
    cloudnode info user verified..
    cloudnode info writing user data to config

You are now ready to use the command line tool.

.. _ssh:

SSH issues
----------

If you have SSH issues, you may consider to use Git over HTTPS, which is easier to use.

If you want to use SSH, make sure that you have uploaded your public SSH key to \ `your
account <https://cloudno.de/account?ssh>`_\ . Compare the fingerprint
that is displayed on your account page with the one displayed when
running the following command on your local computer:

::

    $ ssh-keygen -l -f .ssh/id_rsa.pub

    2048 ab:f2:46:70:30:48:31:05:79:e2:eb:f5:95:38:08:50 .ssh/id_rsa.pub

If you have problems with your SSH key being accepted, make sure that
there are **no line breaks** in the file. The block should start with
the ssh- identifier followed by the basse64 encoded key block and an
email address or other identifier like in the following sample:

With your SSH key on file, you can create your first application. The
ssh connection will not work, until you have created an application.

After your first app is created, the next step is testing your
connection by running *ssh cloudnode@git.cloudno.de*. If your key works,
you should get a success message:

::

    $ ssh cloudnode@git.cloudno.de

    Hi <user>! You've successfully authenticated, but Cloudnode does not provide shell access.
    Connection to git.cloudno.de closed.

Permission denied (publickey)
-----------------------------

This is usually caused when ssh cannot find your keys. Make sure your
key is in the default location, *~/.ssh*. If you run ssh-keygen again
and just press enter at all 3 prompts it will be placed here
automatically. Then you can add the contents of id\_rsa.pub to your
account.

Finding out what keys ssh is using
----------------------------------

Finding what keys ssh is offering to the server is fairly simple. Run
*ssh -vT cloudnode@git.cloudno.de* and look at the output:

::

    debug1: Authentications that can continue: publickey
    debug1: Next authentication method: publickey
    debug1: Trying private key: /home/user/.ssh/id_rsa
    debug1: Trying private key: /home/user/.ssh/id_dsa
    debug1: No more authentication methods to try.
    Permission denied (publickey).

SSH private key passphrases
---------------------------

Using a private key without a passphrase is basically the same as
writing down that random password in a file on your computer. Anyone who
gains access to your drive has gained access to every system you use
that key with. The solution is obvious, add a passphrase.

::

    $ ssh-keygen -p
    Enter file in which the key is (/home/user/.ssh/id_rsa):
    Key has comment '/home/user/.ssh/id_rsa'
    Enter new passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved with the new passphrase.

When you use a passphrase protected key, you need to add it to your
ssh-agent. It stores it securely and you don't have to reenter your
passphrase. The use of the agent is mandatory, as on most systems git
eats stdin and you won't be able to type in your passphrase during git
operations.

.. _logs:

Analysing the application log files
-----------------------------------

Whenever your application throws an exception, it will be logged to you
applications's main log file. You can also use the **console.log()**
instruction to write to that file.

You can view the log file from the "My Apps" management page. You can
also use the command line to tail your application log file. Run the
"cloudnode app logs" command from your application directory.

::

    $ cloudnode app logs

    cloudnode info Checking config..
    cloudnode info Munging require paths..
    cloudnode info Globallizing Buffer
    cloudnode info Reading file...
    cloudnode info Cloudnode wrapped script starting (32623) at  Wed, 06 Apr 2011 23:17:40 GMT
    cloudnode info [INFO] You asked to listen on port 8080 but cloudnode will use port 8007 instead..
    cloudnode info Server running
    cloudnode info

Cloudnode Google Group
----------------------

For additional help visit the \ `Cloudnode Community
Slack Channel <https://slackin.cloudno.de/>`_\ .

Open a ticket
-------------

If you are not finding what you are looking for, open a ticket from your dashboard and we will help you.

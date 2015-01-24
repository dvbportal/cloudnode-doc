Custom Domains
==============

Cloudnode allows you to have applications written and hosted on Cloudnode
respond to requests from your own domain names. For example, if you own
the domain hardtoremember.com and the application
hardtoremember.cloudno.de, then you can configure things such that
visitors to hardtoremember.com are served by the Node app. The app is still
created and hosted on Cloudnode servers.

To accomplish this, you need to:

-  Own a domain.
-  Configure it to point to the Cloudnode platform.

To own a domain, you can use any popular registrar service such as
GoDaddy or EasyDNS. To configure it to point to the Cloudnode platform,
you need to create a "CNAME" record. See instructions for how to do this
with GoDaddy or with EasyDNS.

DNS can be tricky, so if you need help, just ask in the Cloudnode group.

Example CNAME Record
~~~~~~~~~~~~~~~~~~~~

::

    www.example.com. CNAME example.cloudno.de

Make sure to use the symbolic name and not an IP address, because IP
addresses are changing.

Steps to activate a custom domain on Cloudnode
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Custom domains are added as routes to you application using the
`Cloudnode command line </cloudnode-command-line>`_. To add the domain
www.example.com to your application:

1. Go to your configured application directory
2. Run the following command line:

::

    $ cloudnode appdomain add www.example.com

After these steps your application should be reachable under the URL
http://www.example.com.

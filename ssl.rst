SSL
===

Secure Sockets Layer is a protocol to encrypt traffic over the internet.
We support SSL to access all sites including the `API </api>`_. To access the API use the
following URL:

    https://api.cloudno.de/

We also support SSL for every hosted application on a paid plan. When SSL is
enabled, the application can be accessed by using HTTPS, e.g., https://<appname>.cloudno.de.

Our service also includes SSL endpoints for applications running on a custom domain. In this
case obtain a certificate for your domain and upload it to our load balancers through the
application detail page. Once installed the complete traffic of your application is encrypted.

We encourage to use SSL for every application and therefor don't bill anything extra for the use
of SSL. We are able to offer this free service, because we use SNI, which doesn't require an extra
IP address for every application. SNI is nowadays supported on all modern OSes and browsers,
including those on mobile.

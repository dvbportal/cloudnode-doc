Cloudnode Developer Shell
=========================

The Developer Shell provides you with command-line access using computing
resources hosted on the Cloudnode platform. It makes it easy for you to 
manage your projects from your browser without the  need to install the
`Cloudnode Command Line </cloudnode-command-line>`_ and other tools locally
on your system. All tools are always available when you need them.

Developer Shell features:

- A ephemeral compute engine instance running Ubuntu 14.04 LTS
- Command-line access to the instance from your web browser using a terminal window
- About 5 GB persistant disk storage mounted as your $HOME directory
- Cloudnode Command Line and other tools (node, git, docker, ...) preinstalled and ready to use
- Read-only access to all your managed apps running on the platform

You can also use the Developer Shell to perform tasks which would normally require a Linux
machine even if you are running a PC or another device.

.. note:: **Beta** 
   This is a Beta feature that is not covered by a SLA and may be subject to changes.

Getting Started
~~~~~~~~~~~~~~~

To open the Developer Shell navigate to your Dashboard > Applications 
page. Slide the Shell window open by dragging from the bottom or by
using the window controls. Click the center button called "Activate
Cloudnode Developer Shell".

This will:

- Provision a virtual compute instance
- Open a terminal window in the browser
- Mount your persistent /home drive
- Mount your managed /app device (readonly)

Virtual machine instance
~~~~~~~~~~~~~~~~~~~~~~~~

When you launch Developer Shell the platform provisions a docker-based 
compute instance running an Ubuntu 14.04 Linux operating system. Shell
instances persist while your Shell session is active and terminate after
a hour of inactivity.

Command-line access
~~~~~~~~~~~~~~~~~~~

The Developer Shell provides command-line access to the virtual machine
instance in a browser-based terminal window.

Persistent disk storage
~~~~~~~~~~~~~~~~~~~~~~~

Developer Shell provisions 5GB of persistent disk storage mounted as your
$HOME directory. This storage will unlike the instance itself not time out
on inactivity. All our file stored in your home directory, including projects,
scripts annd configuration files

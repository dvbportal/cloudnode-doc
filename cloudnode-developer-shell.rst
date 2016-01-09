Cloudnode Developer Shell
=========================

The Developer Shell provides you with command-line access using computing
resources hosted on the Cloudnode platform. It makes it easy for you to 
manage your projects from your browser without the  need to install the
`Cloudnode Command Line </cloudnode-command-line>`_ and other tools locally
on your system. All tools are always available when you need them.

-  :ref:`getting_started`
-  :ref:`features`

Developer Shell features:

- An ephemeral compute engine instance running Ubuntu 14.04 LTS
- Command-line access to the instance from your web browser using a terminal window
- About 5 GB persistant disk storage mounted as your $HOME directory
- Cloudnode Command Line and other tools (node, git, docker, ...) preinstalled and ready to use
- Read-only access to all your managed apps running on the platform

You can also use the Developer Shell to perform tasks which would normally require a Linux
machine even if you are running a PC or another device.

.. note:: **Beta**

   This is a Beta feature that is not covered by a SLA and may be subject to changes.

.. _getting_started:

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

.. _features:

Features
~~~~~~~~

Developer Shell has the following features:

- An ephemeral virtual machine instance
- Terminal access from a web browser
- 5 GB persistent disk storage
- Preinstalled Cloudnode CLI and other tools (node, git, docker, ...)
- Language support for Javascript, Python, C and C++
- Read-only access to all your managed apps running on the platform

Virtual machine instance
------------------------

When you launch Developer Shell the platform provisions a docker-based 
compute instance running an Ubuntu 14.04 Linux operating system. Shell
instances persist while your Shell session is active and terminate after
a hour of inactivity.

Command-line access
-------------------

The Developer Shell provides command-line access to the virtual machine
instance in a browser-based terminal window. You can open multiple sessions
to the same instance.

Persistent disk storage
-----------------------

Developer Shell provisions 5GB of persistent disk storage mounted as your
$HOME directory. This storage will unlike the instance itself not time out
on inactivity. All our file stored in your home directory, including projects,
scripts annd configuration files like .bashrc, .cloudnoderc and .vimrc persist
between sessions. Your $HOME directory is private to you and cannot be addressed
by other users.

Installed software
------------------

The virtual machine comes with the following pre-installed tools.

================  ===============================================
**Type**          **Installed**
----------------  -----------------------------------------------
Shell             bash, sh
Linux Utils       Standard Ubuntu Utils
Editor            vi(m)
Build Tools       make, npm, nvm
Compiler          Python 2.7, Node.js 0.12.9 and 4.2.4, gcc 4.8.4
Source Control    git 1.9.1
Additional Tools  Docker 1.9.1, Cloudnode-cli 0.2.23
================  ===============================================

Additional software can be installed as Docker containers or using apt.

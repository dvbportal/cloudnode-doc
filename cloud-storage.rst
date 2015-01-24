Cloud Storage
=============

Every application on Cloudnode runs in a `virtual
machine <node-vm>`_ with its own disk storage. The disk holds a full
checkout of the application's `Git </git>`_ repository. So you have
access to modules, sub-modules and static resources, you have checked in.
The disk also holds all Node modules you have installed using the
`npm </node-package-manager>`_ command or through dependencies in the application's
package.json descriptor. The VM contains also a minimum set of directories
to get Linux running like **/etc**.

Special Directories
~~~~~~~~~~~~~~~~~~~

You should not assume, that there is write access to the disk except to
the **/mnt** and **/tmp** directories. Your application can use these
directories to store dynamic data. As the names suggest, **/tmp** can be
used to store volatile files and **/mnt** can be used to store permanent
files. These will always "follow" your application and will be mounted at
**/mnt**.

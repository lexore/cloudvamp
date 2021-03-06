 CVEM - Cloud Virtual Elasticity Manager
========================================

1. INSTALLATION
===============

1.1 REQUISITES
--------------

CVEM is based on python, so Python 2.6 or higher runtime and standard library must
be installed in the system.

CVEM uses the library cpyutils. Follow the instructions from 
https://github.com/grycap/cpyutils to install it.

1.2 INSTALLING
--------------

### 1.2.1 GETTING CloudVAMP FROM GITHUB

Download CloudVAMP from github:

```  
$ cd /tmp
$ git clone https://github.com/grycap/cloudvamp
```
    
or

```
$ cd /tmp 
$ wget https://github.com/grycap/cloudvamp/archive/master.zip
$ unzip cloudvamp-master.zip
$ mv cloudvamp-master cloudvamp
```

### 1.2.2 INSTALL IN SYSTEM PATH

Enter the CVEM directory in the downloaded files and perform the setup installation.

```
$ cd /tmp/cloudvamp/cvem
$ python setup install
```

### 1.2.3 INSTALL IN A SPECIFIC PATH

Select a proper path where to install the CVEM service (i.e. /usr/local/cvem, 
/opt/cvem or other). This path will be called CVEM_PATH.

```
$ cp -r cd /tmp/cloudvamp/cvem /usr/local
```

Finally you must copy (or link) $CVEM_PATH/scripts/cvem file to /etc/init.d directory.

```
    $ ln -s /usr/local/cvem/scripts/cvem /etc/init.d
```

1.3 CONFIGURATION
-----------------

In case that you want the CVEM service to be started at boot time, you must 
execute the next set of commands:

On Debian Systems:

```
$ chkconfig cvem on
```

On RedHat Systems:

```
$ update-rc.d cvem start 99 2 3 4 5 . stop 05 0 1 6 .
```

Or you can do it manually:

```
$ ln -s /etc/init.d/cvem /etc/rc2.d/S99cvem
$ ln -s /etc/init.d/cvem /etc/rc3.d/S99cvem
$ ln -s /etc/init.d/cvem /etc/rc5.d/S99cvem
$ ln -s /etc/init.d/cvem /etc/rc1.d/K05cvem
$ ln -s /etc/init.d/cvem /etc/rc6.d/K05cvem
```

Adjust the installation path by setting the DAEMON variable at /etc/init.d/cvem 
to the path where the CVEM cvemd.py file is installed (e.g. /usr/local/cvem/cvemd.py),
or set the name of the script file (cvemd.py) if the file is in the PATH.
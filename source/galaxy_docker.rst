Galaxy docker instance on Laniakea
==================================

The Laniakea's Galaxy Docker application run a Galaxy Docker container inside a Centos 7 virtual machine.
It support the following Docker image:

- `bgruening/galaxy-stable <https://hub.docker.com/r/bgruening/galaxy-stable/tags>`_
- `bgruening/galaxy-rna-workbench <https://hub.docker.com/r/bgruening/galaxy-rna-workbench/tags>`_
- `laniakeacloud/galaxy-epigen <https://hub.docker.com/r/laniakeacloud/galaxy-epigen/tags>`_
- `laniakeacloud/galaxy-covacs:19.01_nowf <https://hub.docker.com/r/laniakeacloud/galaxy-covacs/tags>`_
- `laniakeacloud/galaxy-gdc_somatic_variant:19.01_nowf <https://hub.docker.com/r/laniakeacloud/galaxy-gdc_somatic_variant/tags>`_


*******************
Configuration Files
*******************

- ``/etc/galaxy/.myenv.sh`` file that contain and define the environmental variables of the container
- ``/etc/galaxy/tool_data_tables`` directory containing the tool_data_table_conf.xml files

*********************
Environment variables 
*********************

The Galaxy docker configuration is slighty different from the default one (link bgruening), only few environment variable were changed to make the galaxy configuration on Docker like the one present on the virtual machine.

::

  GALAXY_CONFIG_TOOL_DATA_TABLE_CONFIG_PATH=<tool_data_table_conf.xml specific for the flavor> 
  GALAXY_CONDA_PREFIX=<docker path to _conda> 
  GALAXY_CONFIG_ADMIN_USERS=<admin_user email selected in the laniakea dashboard>
  GALAXY_CONFIG_BRAND=<brand selected in  selected in the laniakea dashboard> 
  GALAXY_CONFIG_REQUIRE_LOGIN=true
  GALAXY_CONFIG_ALLOW_USER_CREATION=true
  GALAXY_CONFIG_ALLOW_USER_IMPERSONATION=false
  GALAXY_CONFIG_NEW_USER_DATASET_ACCESS_ROLE_DEFAULT_PRIVATE=true
  GALAXY_CONFIG_CONDA_AUTO_INIT=true
  GALAXY_CONFIG_CONDA_AUTO_INSTALL=true
  

*******************  
CVMFS configuration
*******************

The cvmfs selected in the lanikaea dashboard is automatically configured and mounted inside the docker directory ``/cvmfs``.
The cvmfs configuration files are in the directory ``/etc/cvmfs`` both in the VM and in the container.  

-------------------
Galaxy docker usage
-------------------

****************************
Galaxy docker log inspection
****************************
Enter in the Virtual Machine using ssh protocol an use the command:

::

  $ sudo docker logs galaxydocker

---------------------

*************************
Enter inside galaxydocker
*************************

In order to access to the Galaxy container execute the command

::

  $ sudo docker exec -it galaxydocker bash

---------------------

####################################################
Location of main directories inside the Galaxydocker
####################################################
Inside the container the mains Galaxy directory are present in ``/export``:

- ftp: ``/export/ftp``
- database: ``/export/database``
- conda: ``/export/tool_deps/_conda``

##########################
Check Galaxy configuration
##########################

In order to see specific Galaxy configuration explore the docker environment variables using, inside the container, the command: 

::

  $ echo $GALAXY_CONFIG

------------------------


---------------------------------
Galaxy Docker usage videotutorial
---------------------------------

.. raw:: html

       <a href="https://asciinema.org/a/273497" target="_blank"><img src="https://asciinema.org/a/273497.svg" /></a>

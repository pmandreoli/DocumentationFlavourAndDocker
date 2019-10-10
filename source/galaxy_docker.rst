Galaxy docker instance on Laniakea
==================================

the ansible role ansible-role-galaxycloud-docker run Galaxy docker inside a Virtual Machine Centos 7.
support the following docker image:

- `bgruening/galaxy-stable <https://hub.docker.com/r/bgruening/galaxy-stable/tags>`_
- `bgruening/galaxy-rna-workbench <https://hub.docker.com/r/bgruening/galaxy-rna-workbench/tags>`_
- `laniakeacloud/galaxy-epigen <https://hub.docker.com/r/laniakeacloud/galaxy-epigen/tags>`_
- `laniakeacloud/galaxy-covacs:19.01_nowf <https://hub.docker.com/r/laniakeacloud/galaxy-covacs/tags>`_
- `laniakeacloud/galaxy-gdc_somatic_variant:19.01_nowf <https://hub.docker.com/r/laniakeacloud/galaxy-gdc_somatic_variant/tags>`_

--------------------------
Docker engine installation
--------------------------

The docker engine is installed using the role indigo-dc.docker and the docker image location in defined on directory ``/export``

---------------------------
Galaxy docker configuration
---------------------------

*********************
Environment variables 
*********************

The Galaxy docker configuration is slighty different from the default one (link bgruening), only few environment variable were changed to make the galaxy configuration on Docker like the one present on the virtual machine.

:: 

  ``GALAXY_CONFIG_TOOL_DATA_TABLE_CONFIG_PATH=`` <tool_data_table_conf.xml specific for the flavor> 
  ``GALAXY_CONDA_PREFIX=`` <docker path to _conda> 
  ``GALAXY_CONFIG_ADMIN_USERS=`` <admin_user email selected in the laniakea dashboard>
  ``GALAXY_CONFIG_BRAND=``  <brand selected in  selected in the laniakea dashboard> 
  ``GALAXY_CONFIG_REQUIRE_LOGIN=``true
  ``GALAXY_CONFIG_ALLOW_USER_CREATION=``true
  ``GALAXY_CONFIG_ALLOW_USER_IMPERSONATION=``false
  ``GALAXY_CONFIG_NEW_USER_DATASET_ACCESS_ROLE_DEFAULT_PRIVATE=`` true
  ``GALAXY_CONFIG_CONDA_AUTO_INIT=``true
  ``GALAXY_CONFIG_CONDA_AUTO_INSTALL=``true

*******************  
CVMFS configuration
*******************

the config file are created using jinja2 for the cvmfs selected in the dashboard and mounted inside the docker directory /etc/cvmfs

after the docker run the selected Cern vm filesystem is mounted in ``/cvmfs`` directory 


-----------------
Galaxy docker use
-----------------

*********************
Galaxy log inspection
*********************

in order to check the galaxy log from the vm use the command

::

  $ sudo docker logs galaxydocker

---------------------

*************************
Enter inside galaxydocker
*************************

In order to access to the docker execute the command

::

  $ sudo docker exec -it galaxydocker bash

---------------------

#########################################################
Location of principal directories inside the Galaxydocker
#########################################################

the principal galaxy directory location are present in ``/export``:

- ftp: ``/export/ftp``
- database: ``/export/database``
- conda: ``/export/tool_deps/_conda``




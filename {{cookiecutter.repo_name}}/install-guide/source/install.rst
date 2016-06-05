.. _install:

Install and configure
~~~~~~~~~~~~~~~~~~~~~

This section describes how to install and configure the
{{cookiecutter.service}} service, code-named {{cookiecutter.codename}}, on the controller node.

This section assumes that you already have a working OpenStack
environment with at least the following components installed:
Compute, Image Service, Identity.

Prerequisites
-------------

Before you install and configure the {{cookiecutter.service}} service, you must create a
database, service credentials, and API endpoints.

#. To create the database, complete these steps:

   * Use the database access client to connect to the database
     server as the ``root`` user:

     .. code-block:: console

        $ mysql -u root -p

   * Create the ``{{cookiecutter.codename}}`` database:

     .. code-block:: console

        CREATE DATABASE {{cookiecutter.codename}};

   * Grant proper access to the ``{{cookiecutter.codename}}`` database:

     .. code-block:: console

        GRANT ALL PRIVILEGES ON {{cookiecutter.codename}}.* TO '{{cookiecutter.codename}}'@'localhost' \
          IDENTIFIED BY '{{cookiecutter.codename|upper}}_DBPASS';
        GRANT ALL PRIVILEGES ON {{cookiecutter.codename}}.* TO '{{cookiecutter.codename}}'@'%' \
          IDENTIFIED BY '{{cookiecutter.codename|upper}}_DBPASS';

     Replace ``{{cookiecutter.codename|upper}}_DBPASS`` with a suitable password.

   * Exit the database access client.

#. Source the ``admin`` credentials to gain access to
   admin-only CLI commands:

   .. code-block:: console

      $ source admin-openrc.sh

#. To create the service credentials, complete these steps:

   * Create the ``{{cookiecutter.codename}}`` user:

     .. code-block:: console

        $ openstack user create --domain default --password-prompt {{cookiecutter.codename}}

Install and configure components
--------------------------------


Finalize installation
---------------------


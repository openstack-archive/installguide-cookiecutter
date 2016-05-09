.. _install:

Install and configure
~~~~~~~~~~~~~~~~~~~~~

This section describes how to install and configure the
{{service}} service, code-named {{codename}}, on the controller node.

This section assumes that you already have a working OpenStack
environment with at least the following components installed:
Compute, Image Service, Identity.

Prerequisites
-------------

Before you install and configure the {{service}} service, you must create a
database, service credentials, and API endpoints.

#. To create the database, complete these steps:

   * Use the database access client to connect to the database
     server as the ``root`` user:

     .. code-block:: console

        $ mysql -u root -p

   * Create the ``{{codename}}`` database:

     .. code-block:: console

        CREATE DATABASE {{codename}};

      * Grant proper access to the ``{{codename}}`` database:

        .. code-block:: console

           GRANT ALL PRIVILEGES ON {{codename}}.* TO '{{codename}}'@'localhost' \
             IDENTIFIED BY '{{codename|upper}}_DBPASS';
           GRANT ALL PRIVILEGES ON {{codename}}.* TO '{{codename}}'@'%' \
             IDENTIFIED BY '{{codename|upper}}_DBPASS';

        Replace ``{{codename|upper}}_DBPASS`` with a suitable password.

     * Exit the database access client.

#. Source the ``admin`` credentials to gain access to
   admin-only CLI commands:

   .. code-block:: console

      $ source admin-openrc.sh

#. To create the service credentials, complete these steps:

   * Create the ``{{codename}}`` user:

     .. code-block:: console

        $ openstack user create --domain default --password-prompt {{codename}}

Install and configure components
--------------------------------


Finalize installation
---------------------


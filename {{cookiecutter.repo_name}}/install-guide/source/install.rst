.. _install:

Install and configure
~~~~~~~~~~~~~~~~~~~~~

This section describes how to install and configure the
{{cookiecutter.service}} service, code-named {{cookiecutter.codename}}, on the controller node.

This section assumes that you already have a working OpenStack
environment with at least the Identity service, the Compute service,
the Image service installed.

Prerequisites
-------------

Before you install and configure the {{cookiecutter.service}} service,
you must create a database, service credentials, and API endpoints.

#. To create the database, complete these steps:

   * Use the database access client to connect to the database
     server as the ``root`` user:

     .. code-block:: console

        $ mysql -u root -p

   * Create the ``{{cookiecutter.codename}}`` database:

     .. code-block:: mysql

        CREATE DATABASE {{cookiecutter.codename}};

   * Grant proper access to the ``{{cookiecutter.codename}}`` database:

     .. code-block:: mysql

        GRANT ALL PRIVILEGES ON {{cookiecutter.codename}}.* TO '{{cookiecutter.codename}}'@'localhost' \
          IDENTIFIED BY '{{cookiecutter.codename|upper}}_DBPASS';
        GRANT ALL PRIVILEGES ON {{cookiecutter.codename}}.* TO '{{cookiecutter.codename}}'@'%' \
          IDENTIFIED BY '{{cookiecutter.codename|upper}}_DBPASS';

     Replace ``{{cookiecutter.codename|upper}}_DBPASS`` with a suitable password.

   * Exit the database access client.

     .. code-block:: mysql

        exit;

#. Source the ``admin`` credentials to gain access to
   admin-only CLI commands:

   .. code-block:: console

      $ source admin-openrc

#. To create the service credentials, complete these steps:

   * Create the ``{{cookiecutter.codename}}`` user:

     .. code-block:: console

        $ openstack user create --domain default --password-prompt {{cookiecutter.codename}}

   * Add the ``admin`` role to the ``{{cookiecutter.codename}}`` user:

     .. code-block:: console

        $ openstack role add --project service --user {{cookiecutter.codename}} admin

   * Create the {{cookiecutter.codename}} service entities:

     .. code-block:: console

        $ openstack service create --name {{cookiecutter.codename}} --description "{{cookiecutter.service}}" {{cookiecutter.service|lower}}

#. Create the {{cookiecutter.service}} service API endpoints:

   .. code-block:: console

      $ openstack endpoint create --region RegionOne \
        {{cookiecutter.service|lower}} public http://controller:XXXX/vY/%\(tenant_id\)s
      $ openstack endpoint create --region RegionOne \
        {{cookiecutter.service|lower}} internal http://controller:XXXX/vY/%\(tenant_id\)s
      $ openstack endpoint create --region RegionOne \
        {{cookiecutter.service|lower}} admin http://controller:XXXX/vY/%\(tenant_id\)s

Install and configure components
--------------------------------


Finalize installation
---------------------


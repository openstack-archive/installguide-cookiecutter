.. _install-rdo:

Install and configure for Red Hat Enterprise Linux and CentOS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


This section describes how to install and configure the {{cookiecutter.service}} service
for Red Hat Enterprise Linux 7 and CentOS 7.

.. include:: common_prerequisites.txt

Install and configure components
--------------------------------

#. Install the packages:

   .. code-block:: console

      # yum install

.. include:: common_configure.txt

Finalize installation
---------------------

Start the {{cookiecutter.service}} services and configure them to start when
the system boots:

.. code-block:: console

   # systemctl enable openstack-{{cookiecutter.codename}}-api.service

   # systemctl start openstack-{{cookiecutter.codename}}-api.service

2. Edit the ``/etc/{{cookiecutter.codename}}/{{cookiecutter.codename}}.conf`` file and complete the following
   actions:

   * In the ``[database]`` section, configure database access:

     .. code-block:: none

        [database]
        ...
        connection = mysql+pymysql://{{cookiecutter.codename}}:{{cookiecutter.codename|upper}}_DBPASS@controller/{{cookiecutter.codename}}

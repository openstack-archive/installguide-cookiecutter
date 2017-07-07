{%- macro set_header_markup(header_text_length) -%}
{%- set servicelength = cookiecutter.service|length -%}
{%- for _ in range(0, servicelength + header_text_length) -%}={%- endfor -%}
{%- endmacro -%}
{%- macro set_header(header_text) -%}
{{ set_header_markup(header_text|length) }}
{{cookiecutter.service}}{{header_text}}
{{ set_header_markup(header_text|length) }}
{%- endmacro -%}
{{ set_header(" service") }}

.. toctree::
   :maxdepth: 2

   get_started.rst
   install.rst
   verify.rst
   next-steps.rst

The {{cookiecutter.service}} service ({{cookiecutter.codename}}) provides...

This chapter assumes a working setup of OpenStack following the
`OpenStack Installation Tutorial
<https://docs.openstack.org/project-install-guide/ocata/>`_.

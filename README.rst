=================
Gunicorn-instance
=================

Overview
========

This is an Ansible role for installing and configuring gunicorn sites.
Use like this::

    dependencies:
    - role: gunicorn-instance
      instance_name: foo
      program_dir: /usr/local/foo
      program_name: foo
      config_dir: /etc/foo
      user: foo
      log_dir: /var/log/foo
      virtualenv: /usr/local/foo-virtualenv
      port: 8002
      python: python3

Variables
=========

- ``program_name``: The name of the program, such as "enhydris".
- ``instance_name``: A name that will be used in various places (log
  file name, supervisor program name) to identify the instance. (The
  distinction between ``program_name`` and ``instance_name`` is mostly
  useful when there are many instances of a single program running on
  one server; for example, three instances of "enhydris", that is,
  "kyy", "emy" and "ypaat", may be running on one server. When there is
  only one instance running, it doesn't matter, you can still use, for
  example, "naturebank" and "filotis".)
- ``program_dir``: The directory in which the server should run.
- ``config_dir``: The directory in which the ``run_gunicorn`` executable
  will be created. The role creates it if necessary. Very often another
  role places other configuration files in it.
- ``user``: Operating system user. It will be created, and the service
  will be run as this user.
- ``log_dir``: Log directory (created and chowned).
- ``virtualenv``: The python virtualenv directory in which gunicorn will
  be installed and from where it will be run. Usually another role also
  installs the application's stuff in there.
- ``port``: The gunicorn server for that instance will be listening to
  this port.
- ``python``: The default is "python", for python 2. You can specify
  "python3" instead (the apparent inconsistency is because of Debian,
  where packages are named, e.g., ``python-dev`` and ``python3-dev``).
- ``wsgi_location``: The Python module in which ``wsgi.py`` is in. By
  default, this is ``program_name``.

Meta
====

Written by Antonis Christofides

| Copyright (C) 2015 TEI of Epirus
| Copyright (C) 2015 National Technical University of Athens
| Copyright (C) 2015 Antonis Christofides

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see http://www.gnu.org/licenses/.

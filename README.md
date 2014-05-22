Installation
============
Python
------
We are currently running python 2.7 on all systems. We try our best to stay up
to date on the latest security patches.

We use the following python libraries (most of these can, and probably should,
be installed via pip):
- [django](https://www.djangoproject.com/) (specifically the geodjango library)
- [requests](http://docs.python-requests.org/en/latest/)
- [pico](https://github.com/fergalwalsh/pico)
- [south](http://south.readthedocs.org/en/latest/installation.html#installation)
  _Make sure to configure properly_

GeoDjango
---------
- [gis](https://docs.djangoproject.com/en/dev/ref/contrib/gis/install/) install
instructions give platform specific instructions for all the packages you need
to get this working.

Postgres
--------
The database that we are slowly migrating towards is postgres. The installation
instructions for this vary from system to system. If you find a good one for
your system, link to it here.

We will also be using [*postgis*](http://postgis.net/) extensions for geometry
support in postrges.  This has already been installed on the server. For me,
on Linux, my package manager had postgis, so it was fairly simple. Hopefully
this is true for brew, etc.

I am using the following tutorial to set up models that support postgis-backing:
[Using the Django ORM as a standalone component](https://jystewart.net/2008/02/18/using-the-django-orm-as-a-standalone-component/)

Geos
----
If this does not come by default with postgis, you will probably need
[geos](http://trac.osgeo.org/geos/) as well. TBH, I don't remember exactly
where this dependency comes in to the system. If you discover where this is
required, please update the README.

Database Schema
===============
To install and update the database schema, go into django_utils and run
`django-admin.py syncdb --settings=settings_geo`.

Sensors
=======
To load the sensors into the database, go to djange_utils and open
`orm/load.py`. Set the file path to the appropriate path on your machine, save
and run `django-admin.py shell --settings=settings_geo`
In the shell, execute
```python
from orm import load
load.import_sensors()
```

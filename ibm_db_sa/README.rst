IBM_DB_SA
=========

The IBM_DB_SA adapter provides the Python/SQLAlchemy interface to IBM Data Servers.

Version
--------
3.3.2 (2015/05/31)

Prerequisites
--------------
1. Python2.7 or Python3.4
2. SQLAlchemy o.7.3 or above.
3. IBM_DB driver and IBM_DB_DBI wrapper 1.0.1 or higher

Install and Configuration
=========================
  1. To install IBM_DB_SA from source
    Standard Python setup should be used::
        python setup.py install

Connecting
----------
A TCP/IP connection can be specified as the following::

	from sqlalchemy import create_engine

	e = create_engine("db2+ibm_db://user:pass@host[:port]/database")

For a local socket connection, exclude the "host" and "port" portions::

	from sqlalchemy import create_engine

	e = create_engine("db2+ibm_db://user:pass@/database")

Supported Databases
-------------------
- IBM DB2 Universal Database for Linux/Unix/Windows versions 9.7 onwards

Known Limitations in ibm_db_sa adapter for DB2 databases
-------------------------------------------------------------
1) Non-standard SQL queries are not supported. e.g. "SELECT ? FROM TAB1"
2) For updations involving primary/foreign key references, the entries should be made in correct order. Integrity check is always on and thus the primary keys referenced by the foreign keys in the referencing tables should always exist in the parent table.
3) Unique key which contains nullable column not supported
4) UPDATE CASCADE for foreign keys not supported
5) DEFERRABLE INITIALLY deferred not supported
6) Subquery in ON clause of LEFT OUTER JOIN not supported
7) PyODBC and Jython/zxjdbc support is experimental

Not Supported / Not Tested
---------------------------
- Python 3 has will test

Credits
-------
ibm_db_sa for SQLAlchemy was first produced by IBM Inc., targeting version 0.4.
The library was ported for version 0.6 and 0.7 by Jaimy Azle.
Port for version 0.8 and modernization of test suite by Mike Bayer.


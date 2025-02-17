OpenSearch Curator Python API
================================

The OpenSearch Curator Python API helps you manage your indices and
snapshots.

.. note::

   This documentation is for the OpenSearch Curator Python API.  Documentation
   for the OpenSearch Curator *CLI* -- which uses this API and is installed
   as an entry_point as part of the package -- is available in the
   `Elastic guide`_.

.. _Elastic guide: http://www.elastic.co/guide/en/opensearch/client/curator/current/index.html

Compatibility
-------------

The OpenSearch Curator Python API is compatible with the 5.x OpenSearch versions, 
and supports Python versions 2.7, and 3.5+.

Installation
------------

Install the ``opensearch-curator`` package with `pip
<https://pypi.python.org/pypi/opensearch-curator>`_::

    pip install opensearch-curator

Example Usage
-------------

::

    import opensearchpy
    import curator

    client = opensearchpy.OpenSearch()

    ilo = curator.IndexList(client)
    ilo.filter_by_regex(kind='prefix', value='logstash-')
    ilo.filter_by_age(source='name', direction='older', timestring='%Y.%m.%d', unit='days', unit_count=30)
    delete_indices = curator.DeleteIndices(ilo)
    delete_indices.do_action()

.. TIP::
    See more examples in the :doc:`Examples </examples>` page.

Features
--------

The API methods fall into the following categories:

* :doc:`Object Classes </objectclasses>` build and filter index list or snapshot list objects.
* :doc:`Action Classes </actionclasses>` act on object classes.
* :doc:`Utilities </utilities>` are helper methods.

Logging
~~~~~~~

The OpenSearch Curator Python API uses the standard `logging library`_ from Python.
It inherits two loggers from ``opensearchpy``: ``opensearch`` and
``opensearchpy.trace``. Clients use the ``opensearch`` logger to log
standard activity, depending on the log level. The ``opensearchpy.trace``
logger logs requests to the server in JSON format as pretty-printed ``curl``
commands that you can execute from the command line. The ``opensearchpy.trace``
logger is not inherited from the base logger and must be activated separately.

.. _logging library: http://docs.python.org/3.6/library/logging.html

Contents
--------

.. toctree::
   :maxdepth: 2

   objectclasses
   actionclasses
   filters
   utilities
   examples
   Changelog

License
-------

Copyright (c) 2012–2019 OpenSearch <http://www.elastic.co>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


Indices and tables
------------------

* :ref:`genindex`
* :ref:`search`

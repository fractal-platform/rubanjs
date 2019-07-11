
.. include:: include_announcement.rst

====
Ruban
====

    The Ruban class is a wrapper to house all Fractal related modules.


Initiating of Ruban
=====================

----------
Parameters
----------

1. ``provider`` - ``string|object``: A URL or one of the Ruban provider classes.
2. ``net`` - ``net.Socket`` (optional): The net NodeJS package.
3. ``options`` - ``object`` (optional) The Ruban :ref:`options <ruban-module-options>`


-------
Example
-------

.. code-block:: javascript

    import Ruban from 'ruban';

    const ruban = new Ruban('http://127.0.0.1:8546', net, options);

    > ruban.fra
    > ruban.utils
    > ruban.wallet


------------------------------------------------------------------------------


Ruban.modules
=====================

    This Static property will return an object with the classes of all major sub modules, to be able to instantiate them manually.

-------
Returns
-------

``Object``: A list of modules:
    - ``Fra`` - ``Function``: the Fra module for interacting with the Fractal network see :ref:`ruban.fra <fra>` for more.
    - ``Net`` - ``Function``: the Net module for interacting with network properties see :ref:`ruban.fra.net <fra-net>` for more.
    - ``Admin`` - ``Function``: the Admin module for interacting with the Fractal network see :ref:`ruban.admin <admin-module>` for more.

-------
Example
-------

.. code-block:: javascript

    Ruban.modules
    > {
        Fra(provider, net?, options?),
        Net(provider, net?, options?),
        Admin(provider, net?, options?),
    }


.. include:: include_package-core.rst

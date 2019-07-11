options
=====================

An Ruban module does provide several options for configuring the transaction confirmation worklfow or for defining default values.
These are the currently available option properties on a Ruban module:

.. _ruban-module-options:

--------------
Module Options
--------------

:ref:`defaultAccount <ruban-module-defaultaccount>`

:ref:`defaultBlock <ruban-module-defaultblock>`

:ref:`defaultGas <ruban-module-defaultgas>`

:ref:`defaultGasPrice <ruban-module-defaultaccount>`

:ref:`transactionBlockTimeout <ruban-module-transactionblocktimeout>`

:ref:`transactionConfirmationBlocks <ruban-module-transactionconfirmationblocks>`

:ref:`transactionPollingTimeout <ruban-module-transactionpollingtimeout>`

:ref:`transactionSigner <ruban-module-transactionSigner>`

-------
Example
-------

.. code-block:: javascript

    import Ruban from 'ruban';

    const options = {
        defaultAccount: '0x0',
        defaultBlock: 'latest',
        defaultGas: 1,
        defaultGasPrice: 0,
        transactionBlockTimeout: 50,
        transactionConfirmationBlocks: 24,
        transactionPollingTimeout: 480,
        transactionSigner: new CustomTransactionSigner()
    }

    const ruban = new Ruban('http://localhost:8545', null, options);

------------------------------------------------------------------------------

.. _ruban-module-defaultblock:

defaultBlock
=====================

.. code-block:: javascript

    ruban.defaultBlock
    ruban.fra.defaultBlock
    ...

The default block is used for all methods which have a block parameter.
You can override it by passing the block parameter if a block is required.

Example:

- :ref:`ruban.fra.getBalance() <fra-getbalance>`
- :ref:`ruban.fra.getCode() <fra-code>`
- :ref:`ruban.fra.getTransactionCount() <fra-gettransactioncount>`
- :ref:`ruban.fra.getStorageAt() <fra-getstorageat>`
- :ref:`ruban.fra.call() <fra-call>`
- :ref:`new ruban.fra.Contract() -> myContract.actions.myAction().call() <contract-call>`

-------
Returns
-------

The ``defaultBlock`` property can return the following values:

- ``Number``: A block number
- ``"latest"`` - ``String``: The latest block (current head of the blockchain)

Default is ``"latest"``

------------------------------------------------------------------------------

.. _ruban-module-defaultaccount:

defaultAccount
=====================

.. code-block:: javascript

    ruban.defaultAccount
    ruban.fra.defaultAccount
    ruban.fra.Contract.defaultAccount
    ...

This default address is used as the default ``"from"`` property, if no ``"from"`` property is specified.

-------
Returns
-------

``String`` - 20 Bytes: Any Fractal address. You need to have the private key for that address in your keystore. (Default is ``undefined``)

------------------------------------------------------------------------------

.. _ruban-module-defaultgasprice:

defaultGasPrice
=====================

.. code-block:: javascript

    ruban.defaultGasPrice
    ruban.fra.defaultGasPrice
    ruban.fra.Contract.defaultGasPrice
    ...

The default gas price which will be used for a request.

-------
Returns
-------

``string|number``: The current value of the defaultGasPrice property.


------------------------------------------------------------------------------

.. _ruban-module-defaultgas:

defaultGas
=====================

.. code-block:: javascript

    ruban.defaultGas
    ruban.fra.defaultGas
    ruban.fra.Contract.defaultGas
    ...

The default gas which will be used for a request.

-------
Returns
-------

``string|number``: The current value of the defaultGas property.

------------------------------------------------------------------------------

.. _ruban-module-transactionblocktimeout:

transactionBlockTimeout
=====================

.. code-block:: javascript

    ruban.transactionBlockTimeout
    ruban.fra.transactionBlockTimeout
    ruban.fra.Contract.transactionBlockTimeout
    ...

The ``transactionBlockTimeout`` will be used over a socket based connection. This option does define the amount of new blocks it should wait until the first confirmation happens.
This means the PromiEvent rejects with a timeout error when the timeout got exceeded.


-------
Returns
-------

``number``: The current value of transactionBlockTimeout

------------------------------------------------------------------------------

.. _ruban-module-transactionconfirmationblocks:

transactionConfirmationBlocks
=====================

.. code-block:: javascript

    ruban.transactionConfirmationBlocks
    ruban.fra.transactionConfirmationBlocks
    ruban.fra.Contract.transactionConfirmationBlocks
    ...

This defines the number of blocks it requires until a transaction will be handled as confirmed.


-------
Returns
-------

``number``: The current value of transactionConfirmationBlocks

------------------------------------------------------------------------------


.. _ruban-module-transactionpollingtimeout:

transactionPollingTimeout
=====================

.. code-block:: javascript

    ruban.transactionPollingTimeout
    ruban.fra.transactionPollingTimeout
    ruban.fra.Contract.transactionPollingTimeout
    ...

The ``transactionPollingTimeout``  will be used over a HTTP connection.
This option does define the amount of polls (each second) it should wait until the first confirmation happens.


-------
Returns
-------

``number``: The current value of transactionPollingTimeout

------------------------------------------------------------------------------


.. _ruban-module-transactionSigner:

transactionSigner
=================

.. code-block:: javascript

    ruban.fra.transactionSigner
    ...



The ``transactionSigner`` property does provide us the possibility to customize the signing process
of the ``fra`` module and the related sub-modules.

The interface of a ``TransactionSigner``:

.. code-block:: javascript

    interface TransactionSigner {
        sign(txObject: Transaction): Promise<SignedTransaction>
    }

    interface SignedTransaction {
        messageHash: string,
        v: string,
        r: string,
        s: string,
        rawTransaction: string
    }



-------
Returns
-------

``TransactionSigner``: A JavaScript class of type TransactionSigner.

------------------------------------------------------------------------------

setProvider
=====================

.. code-block:: javascript

    ruban.setProvider(myProvider)
    ruban.fra.setProvider(myProvider)
    ...

Will change the provider for its module.

.. note:: When called on the umbrella package ``ruban`` it will also set the provider for all sub modules ``ruban.fra``, etc.

----------
Parameters
----------

1. ``Object|String`` - ``provider``: a valid provider
2. ``Net`` - ``net``: (optional) the node.js Net package. This is only required for the IPC provider.

-------
Returns
-------

``Boolean``

-------
Example
-------

.. code-block:: javascript

    import Ruban from 'ruban';

    const ruban = new Ruban('http://localhost:8545');

    // or
    const ruban = new Ruban(new ruban.providers.HttpProvider('http://localhost:8545'));

    // change provider
    ruban.setProvider('ws://localhost:8546');
    // or
    ruban.setProvider(new ruban.providers.WebsocketProvider('ws://localhost:8546'));

------------------------------------------------------------------------------

providers
=====================

.. code-block:: javascript

    ruban.providers
    fra.providers
    ...

Contains the current available providers.

----------
Value
----------

``Object`` with the following providers:

    - ``Object`` - ``HttpProvider``: The HTTP provider is the only supported provider for now.

-------
Example
-------

.. code-block:: javascript

    const Ruban = require('ruban');

    const ruban = new Ruban('http://localhost:8545');

------------------------------------------------------------------------------

currentProvider
=====================

.. code-block:: javascript

    ruban.currentProvider
    ruban.fra.currentProvider
    ...

Will return the current provider.


-------
Returns
-------

``Object``: The current provider set.

-------
Example
-------

.. code-block:: javascript

    if (!ruban.currentProvider) {
        ruban.setProvider('http://localhost:8545');
    }

.. include:: include_announcement.rst

===============
Getting Started
===============

The rubanjs library is a collection of modules which contain specific functionality for the Fractal ecosystem.

- The ``ruban-fra`` is for the Fractal blockchain and smart contracts
- The ``ruban-utils`` contains useful helper functions for DApp developers.


.. _adding-ruban:

Adding rubanjs
==============

.. index:: npm

First you need to get rubanjs into your project. This can be done using the following methods:

- npm: ``npm install rubanjs``

After that you need to create a ruban instance and set a provider.
For  rubanjs, check ``ruban.givenProvider``. If this property is ``null`` you should connect to your own local or remote node.

.. code-block:: javascript

    // in node.js use:
    const Ruban = require('rubanjs');
    const {TextEncoder, TextDecoder} = require('utils');

    const ruban = new Ruban('http://local-or-remote:8545/rpc', null, {textEncoder: new TextEncoder(), textDecoder: new TextDecoder()});

    // in browser environment:
    const Ruban = require('rubanjs');

    const ruban = new Ruban('http://local-or-remote:8545/rpc', null, {});

    // in React Native, IE11, and Edge Browsers:
    const Ruban = require('rubanjs');
    const {TextEncoder, TextDecoder} = require('text-encoding');

    const ruban = new Ruban('http://local-or-remote:8545/rpc', null, {textEncoder: new TextEncoder(), textDecoder: new TextDecoder()});

That's it! now you can use the ``ruban`` object.

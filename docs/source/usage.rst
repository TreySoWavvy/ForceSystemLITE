Configuration
=====

Every installation contains a **ModuleScript** known as ``Configuration``, that is located within the ``Force_Dependents`` Folder.
This Module is the overhead settings file that controls all the important aspects of your system, including **energy usage**, and **who gets abilities**.

In order for your system to properly work, you **must** configure this file to meet the needs of your particular group. It **will not work "fresh out the box"** without first being modified.

We will go over all the important configurations below.


Force Levels vs Force Roles
------------
To understand the system, you must know that Force Abilities are scaled on a **level system** from **1** to **5**:

- (1): Apprentice
- (2): Novice
- (3): Adept
- (4): Master
- (5): Grand Master

This system operates similarly to most **Admin Systems**, in which you can only use the ability of **your level and below**. A Novice cannot use a Master's ability, but a Master can use all abilities Master and below.

All abilities have a `Level` property contained within their ModuleScript. Developers can adjust this level as they see fit, based on the importance of the ability or its rarity.

Freeplay Mode
------------
**Freeplay Mode** is exactly as it sounds. It allows **all** players who join the game to be given a. 
To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']


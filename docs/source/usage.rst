Configuration
=====

Every installation contains a **ModuleScript** known as ``Configuration``, that is located within the ``Force_Dependents`` Folder.
This Module is the overhead settings file that controls all the important aspects of your system, including **energy usage**, and **who gets abilities**.

In order for your system to properly work, you **must** configure this file to meet the needs of your particular group. It **will not work "fresh out the box"** without first being modified.

We will go over all the important configurations below.


Force Mastery Levels vs Force Roles
------------
To understand the system, you must know that Force Abilities are scaled on a **Mastery System** from **1** to **5**:

- (1): Apprentice
- (2): Novice
- (3): Adept
- (4): Master
- (5): Grand Master

This system operates similarly to most **Admin Systems**, in which you can only use the ability of **your level and below**. A Novice cannot use a Master's ability, but a Master can use all abilities Master and below.

All abilities have a ``Level`` property contained within their ModuleScript. Developers can adjust this level as they see fit, based on the **importance** of the ability or its **rarity**.


**Force Roles**, however, **subvert** the **level system**. Force Roles allow developers to give abilities of **all** levels to a player, regardless of what their actual Mastery Level is.
A helpful analogy is the Jedi Temple Guard, whose abilities are taught at different stages of a Jedi's training. These sets of abilities can be assigned to players to give them different abilities at different levels, disregarding the mastery.


Freeplay Mode
------------
**Freeplay Mode** is precisely as it sounds. It assigns a **Force Role** or a specific **Mastery Level** to all players who join the game. 

This setting is purely for enabling a "Free Play" environment where all players can use the force system, and helps test the system or support open-world gameplay.

To enable this gameplay aspect, set ``Configuration["FREEPLAY_ENABLED"]`` to ``true``. 

To designate what **Mastery Level** players receive upon joining, set ``Configuration["FREEPLAY_LEVEL"] (number)`` to a number **matching** an already created level (i.e, 1-5). Numbers outside this range won't be accepted or read.

Conversely, if you wish to assign a **Force Role** to players upon joining instead, set ``Configuration["FREEPLAY_ROLE"] (string)`` to match a **Force Role** already created in your ``ROLE`` table (more or that below)


All players who **didnt already have abilities assigned to them** will now be able to access the ones specified here. So that you know,** players who already have abilities assigned or purchased will still retain those abilities.** 


Natural Birth Mode
------------
**Natural Birth** Mode was designed to allow players to experience the Force System **naturally**, while providing existing users with consistent opponents.
This keeps force-based gameplay from being stagnant, allowing players on opposing (*and sometimes the same*) teams to join and have a percent chance of randomly obtaining a force **Mastery Level**

This setting can be enabled by setting ``Configuration["NATURAL_BORN_ENABLED"] (bool)`` to ``true``, and the percent chance can be controlled by changing ``Configuration["NATURAL_BORN_CHANCE"] (int)`` to a number between ``0`` and ``1`` (default is ``.15`).

.. code-block:: lua

   Configuration["NATURAL_BORN_ENABLED"] = false;									--// Whether or not players have a chance of being randomly given force abilities upon joining.
   Configuration["NATURAL_BORN_CHANCE"] = .15;										--// The percent chance they have to get it.




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


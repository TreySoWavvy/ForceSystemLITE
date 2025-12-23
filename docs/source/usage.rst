Configuration
=====

Every installation contains a **ModuleScript** known as ``Configuration``, that is located within the ``Force_Dependents`` Folder.
This Module is the overhead settings file that controls all the important aspects of your system, including **energy usage**, and **who gets abilities**.

In order for your system to properly work, you **must** configure this file to meet the needs of your particular group. It **will not work "fresh out the box"** without first being modified.

We will go over all the important configurations below.


Force Mastery Levels vs Force Roles
------------
To understand the system, you must know that Force Abilities are scaled on a **Mastery System** from **1** to **5**:

- (1): **Apprentice** - The bare minimum force level. All players default to this. No abilities.
- (2): **Novice** - The entry level force level. Basic abilities begin here.
- (3): Adept
- (4): Master
- (5): Grand Master - The supreme force user. Has access to all abilities.

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

.. code-block:: lua
   Configuration["FREEPLAY_ENABLED"] = false; 		--// Whether free play mode is enabled or not.
   Configuration["FREEPLAY_LEVEL"] = 6; 				--// What level of mastery all players are given during freeplay.
   Configuration["FREEPLAY_LEVEL_ROLE"] = "None";	--// Give all players a force role upon joining.

   
**Note**: players who already have abilities assigned or purchased will still retain those abilities.** 


Natural Birth Mode
------------
**Natural Birth** Mode was designed to allow players to experience the Force System **naturally**, while providing existing users with consistent opponents.
This keeps force-based gameplay from being stagnant, allowing players on opposing (*and sometimes the same*) teams to join and have a percent chance of randomly obtaining a force **Mastery Level**

This setting can be enabled by setting ``Configuration["NATURAL_BORN_ENABLED"] (bool)`` to ``true``, and the percent chance can be controlled by changing ``Configuration["NATURAL_BORN_CHANCE"] (int)`` to a number between ``0`` and ``1`` (default is `.15`).

.. code-block:: lua

   Configuration["NATURAL_BORN_ENABLED"] = false;	--// Whether or not players have a chance of being randomly given force abilities upon joining.
   Configuration["NATURAL_BORN_CHANCE"] = .15;		--// The percent chance they have to get it.


Force Energy
------------
**Force Energy** is a stamina that can be consumed upon using an ability. All abilities can consume stamina if it is enabled, and players wont be able to use that ability if they don't have enough.
The base energy players can spawn with can be set with the ``Configuration["BASE_ENERGY"]`` property. Upon using energy, a delay will occur before they begin regenerating that energy.

The **Rate** and **Delay** can be customized to enable unique energy regeneration.

**Note:** It is **highly** that this setting is enabled to allow for **fair usage** of force abilities in live gameplay. Failure to configure this properly may result in power imbalances within the game and potential abuse by Force Users.

.. code-block:: lua

   Configuration["ENERGY_ENABLED"] = false; --// Whether energy consumption is enabled or not.
   Configuration["BASE_ENERGY"] = 250;     --// The base energy all players spawn with.
   Configuration["INITIAL_ENERGY_REGEN_DELAY"] = 5;     --// How many seconds after energy is consumed, the user will begin regenerating their energy.

   Configuration["ENERGY_REGEN_RATE"] = 2.5;   --// The amount of energy that will be regenerated.
   Configuration["REGEN_RATE_DELAY"] = .15;    --// The delay between energy regen ticks.



Defining Force Roles
------------
To create a set of force abilities, you can assign them to a **Role**. Roles can be created in the ``ROLE`` table within the ``Configuration`` ModuleScript.
Any number of roles can be created, and abilities must be listed as an ``array``.
Below is an example of some specific roles within a Jedi Order group:

.. code-block:: lua

Configuration["ROLE"] = { --// Assignable roles & the abilities they have.
	["Temple Guard"] = {"Force Push", "Force Pull", "Force Fortitude", "Force Foresight", "Force Sever"};

	["Jedi Sentinel"] = {"Force Teleport", "Force Cloak"};

   ["Jedi Consular"] = {"Force Heal", "Force Sense"};
}

These will be used later when assigning them to players. 
**Note:** Roles supersede Mastery Levels. Meaning if a player is assigned an ability via a role, they can use it regardless of their actual level.


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


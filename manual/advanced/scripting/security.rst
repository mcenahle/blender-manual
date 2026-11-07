
********************
Scripting & Security
********************

The ability to include Python scripts within blend-files is valuable for advanced tasks
such as rigging and automation. However, it poses a security risk since
Python does not restrict what a script can do.
Therefore, you should only run scripts from sources you know and trust.
Automatic execution is disabled by default;
however, some blend-files need this to function properly.

When a blend-file tries to execute a script and is not allowed, a dialog will appear.
It warns that allowing the scripts may be unsafe and offers the following choices:

.. figure:: /images/advanced_scripting_security_autorun-scripts-dialog.jpg

   An Auto-run warning in the Info editor's header.

Continue Safely
   Keeps the file open without running its scripts.
Allow Execution
   Allows scripts for the current file. Saved files are reloaded so their scripts can run.

Choosing *Allow Execution* does not enable *Auto Run Python Scripts* in the Preferences.


Scripts in Blend-Files
======================

Auto Execution
--------------

Here are the different ways blend-files may automatically run scripts.

Registered Text-Blocks
   A text data-block can have its *Register* option enabled which means it will load on start.
Animation Drivers
   Python expressions can be used to *Drive* values and are often used in more advanced rigs and animations.


Manual Execution
----------------

There are other ways scripts in a blend-file may execute that require user
interaction (therefore will run even when auto execution is off),
but you should be aware that this is the case since it is not necessarily obvious.

- Running a script in the Text editor.
- Rendering with Freestyle, because Freestyle uses scripts to control line styles.


Controlling Script Execution
============================

Blender provides a number of ways to control whether scripts
from a blend-file are allowed to automatically execute.

First, the File Browser has the *Trusted Source* option for controlling auto execution
on a case-by-case basis. Files can also be opened without using the File Browser,
so the default can be changed as described below.


Setting Defaults
----------------

In the Preferences, there is the toggle to
:ref:`Auto Run Python Scripts <bpy.types.PreferencesFilePaths.use_scripts_auto_execute>`.
This means the *Trusted Source* option in the File Browser will be enabled by default,
and scripts can run when blend-files are loaded without using the File Browser.
Once enabled, certain directories can be excluded;
a typical configuration would be to trust all paths except for the download directory.

.. warning::

   This is a global default. Opening blend-files from the internet or other untrusted sources while it is enabled
   can run malicious code. Prefer enabling *Trusted Source* for individual files when possible.

.. figure:: /images/animation_drivers_troubleshooting_autorun-user-preference.png

   The Auto Run Python Scripts checkbox.


Command Line
------------

You may want to perform batch rendering or some other task from the command line,
running Blender without an interface.
In this case, the Preferences are still used but you may want to override them:

- Enable with ``-y`` or ``--enable-autoexec``
- Disable with ``-Y`` or ``--disable-autoexec``


Example
^^^^^^^

To render an animation in background mode, allowing drivers and other scripts to run:

.. code-block:: sh

   blender --background --enable-autoexec my_movie.blend --render-anim

.. note::

   These command-line arguments can be used to start a regular Blender instance and
   will still override the Preferences.

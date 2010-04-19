===========================================================================
VimDown, crude package management for Vim scripts with minimal dependencies
===========================================================================

:Author:    Jon-Michael Deldin
:Contact:   dev@jmdeldin.com
:Homepage:  http://github.com/jmdeldin/VimDown
:Version:   0.1

VimDown downloads the latest versions of scripts from `Vim.org`_. It is designed to
be used with Tim Pope's `pathogen.vim`_, but masochists can manually modify their
runtime path (``:h runtimepath``).

.. _`Vim.org`: http://www.vim.org
.. _pathogen.vim: http://www.vim.org/scripts/script.php?script_id=2332

Compared to GetLatestVimScripts (``:h glvs``), VimDown works with color schemes and other
plugins that need to be installed to certain directories.

Requirements
------------

- Python 2.5+

Configuration
-------------

1. Backup your "~/.vim" directory and relocate it for now to avoid duplicate
   scripts.

2. Create the "~/.vim/bundle" directory.

3. Download `pathogen.vim`_ to "~/.vim/bundle/pathogen/autoload/"

4. Add the following to your ".vimrc"::

    " Note: This should point to wherever pathogen resides
    set runtimepath+=$HOME/.vim/bundle/pathogen
    call pathogen#runtime_append_all_bundles()"
    call pathogen#helptags()

5. Create "~/.vim/bundles.csv" (this is the default location, but you can pass
   a ``--file`` argument to ``vimdown``)

6. The "bundles.csv" format is similar to GetLatestVimScripts::

    ScriptId, Name,           Directory
    294,      Align.vim,
    .
    .
    .
    3065,     mayansmoke.vim, colors

..

    :ScriptId:       The ``script_id`` parameter in the URL on vim.org. For
                     example, the script_id in
                     ``http://www.vim.org/scripts/script.php?script_id=3065``
                     is **3065**.

    :Name:           Script name, saved as ``bundle/<name>``.

    :Directory:      Optional directory to create. For example, color schemes
                     are normally uploaded to vim.org as a ``.vim`` file, so we need to
                     create a "colors" directory.

Usage
-----

Call ``vimdown`` from your shell to update all scripts.

::

    $ ./vimdown -h
    Usage: vimdown [options]

    Options:
      -h, --help            show this help message and exit
      -f FILENAME,   --file=FILENAME
                            Bundle CSV file
      -d BUNDLE_DIR, --directory=BUNDLE_DIR
                            Bundle directory (e.g., ~/.vim/bundle)

Caveats
-------

This script has only been tested on OS X 10.6.3. This will not work under
Windows ``cmd.exe`` due to the shell commands used (``unzip``, ``mv``, and
``tar``), but I think it'll work under Cygwin.

Related Projects
----------------

- Vimana_ -- ``apt-get`` for Vim plugins (Perl with CPAN dependencies)

.. _Vimana: http://github.com/c9s/Vimana

- vim-addon-manager_  -- unclear usage, as of 2010-04-18 (pure VimL)

.. _vim-addon-manager: http://github.com/MarcWeber/vim-addon-manager

- get.rb_ -- pretty similar to VimDown, but it is written in Ruby and doesn't
  handle Vimballs

.. _get.rb: http://github.com/sunaku/.vim/blob/master/bundle/get.rb

.. vim: set ft=rst:


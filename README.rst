Mac OS X development setup
##########################

.. contents:: Table of Contents
    :local:

Step 1: check for system updates
================================

Go to: **Apple Icon -> About this Mac -> Software updates**

Step 2: install Homebrew and Homebrew-Cask
==========================================

**Homebrew** is a package manager for macOS. **Homebrew-Cask** extends Homebrew and brings support
for packages allowing to install macOS applications and large binaries.

.. code-block:: shell

  $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  $ brew tap homebrew/cask

Step 3: install iTerm2
======================

.. code-block:: shell

  $ brew cask install iterm2

Preference modifications:

* Go to **iTerm2 -> Preferences -> General -> Closing** and uncheck **Confirm "Quit iTerm2 (Cmd+Q)" command**
  under the section Closing.
* Go to **iTerm2 -> Preferences -> Profiles -> Default -> Text** and ensure that font is set to
  **13pt Menlo Regular**
* Download and install an iTerm theme (https://github.com/mbadolato/iTerm2-Color-Schemes)

Step 4: install the Fish shell
==============================

.. code-block:: shell

  $ brew install fish
  $ curl -L https://get.oh-my.fish | fish
  $ echo "/usr/local/bin/fish" | sudo tee -a /etc/shells
  $ chsh -s /usr/local/bin/fish

Step 5: install basic packages using ``brew`` and ``brew cask``
===============================================================

.. code-block:: shell

  $ brew install gdbm gettext gnutls go gnupg iproute2mac jpeg jpegoptim libgcrypt libffi libksba \
    libtasn1 libusb nano ncurses openssl sqlite wget
  $ brew cask install firefox gimp google-chrome spotify vlc

Step 6: prepare the ``Workspace`` directory
===========================================

.. code-block:: shell

  $ mkdir ~/Workspace

Step 7: set up Python and related dependencies
==============================================

Install Python
--------------

.. code-block:: shell

  $ brew install python python3

Install basic Python packages & tools
-------------------------------------

.. code-block:: shell

  $ pip install cookiecutter cryptography Pillow pipenv virtualenvwrapper

Prepare the ``.virtualenvs`` directory
--------------------------------------

.. code-block:: shell

  $ mkdir ~/.virtualenvs

Step 8: set up Ruby and related dependencies
===========================================+

Install rbenv
-------------

.. code-block:: shell

  $ brew install rbenv rbenv-default-gems ruby-build
  $ eval "$(rbenv init -)"
  $ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
  $ echo bundler >> ~/.rbenv/default-gems
  $ CFLAGS=-O3 rbenv install 2.5.3
  $ rbenv global 2.5.3

Install basic Ruby packages and tools
-------------------------------------

.. code-block:: shell

  $ gem install pry rails

Step 9: set up NodeJS and related dependencies
==============================================

Install NodeJS
--------------

.. code-block:: shell

  $ brew install node

Install global NPM packages
---------------------------

.. code-block:: shell

  $ npm install -g eslint npm-check-updates

Step 10: set up Git
===================

.. code-block:: shell

  $ brew install git

Step 11: set up PostgreSQL
==========================

Install PostgreSQL
------------------

.. code-block:: shell

  $ brew install postgresql
  $ brew services start postgresql

First login to PostgreSQL
-------------------------

.. code-block:: shell

  $ createdb (whoami)
  $ psql

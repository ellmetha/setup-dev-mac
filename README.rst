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
  $ brew tap caskroom/cask

Step 3: install basic packages using ``brew`` and ``brew cask``
===============================================================

.. code-block:: shell

  $ brew install bash-completion gdbm gettext gnutls go gnupg iproute2mac jpeg jpegoptim libgcrypt \
    libffi libksba libtasn1 libusb nano ncurses openssl sqlite
  $ brew cask install etcher firefox gimp google-chrome keybase limechat slack skype virtualbox vlc

Step 4: install iTerm2
======================

.. code-block:: shell

  $ brew cask install iterm2

Preference modifications:

* Go to **iTerm2 -> Preferences -> General** and uncheck **Confirm "Quit iTerm2 (Cmd+Q)" command**
  under the section Closing.
* Go to **iTerm2 -> Preferences -> Profiles -> Default -> Text** and ensure that font is set to
  **13pt Menlo Regular**

Step 5: prepare the ``Workspace`` directory
===========================================

.. code-block:: shell

  $ mkdir ~/Documents/Workspace

Step 6: set up Python and related dependencies
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

Step 7: set up NodeJS and related dependencies
==============================================

Install NodeJS
--------------

.. code-block:: shell

  $ brew install node

Install global NPM packages
---------------------------

.. code-block:: shell

  $ npm install -g eslint npm-check-updates

Step 8: set up Git
==================

Install Git
-----------

.. code-block:: shell

  $ brew install git

Configure Git completion
------------------------

.. code-block:: shell

  $ curl "https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash" --silent --output "$HOME/.git-completion.bash"

Step 9: set up bash
===================

Create the ``.bash_aliases`` file
---------------------------------

.. code-block:: shell

  alias brewup='brew update; brew upgrade; brew prune; brew cleanup; brew doctor'
  alias cdworkspace='cd ~/Documents/Workspace'

Create the ``.bash_profile`` file
---------------------------------

.. code-block:: shell

  export GPG_TTY=$(tty)
  export EDITOR=nano
  export PS1="\[\033[1;34m\]\!\[\033[0m\] \[\033[1;35m\]\u\[\033[0m\]:\[\033[1;35m\]\W\[\033[0m\]λ "

  # Completion
  if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
  fi
  . ~/.git-completion.bash

  # Aliases
  if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
  fi

  # Virtualenvwrapper
  export WORKON_HOME=$HOME/.virtualenvs
  export PROJECT_HOME=$HOME/Documents/Workspace
  source /usr/local/bin/virtualenvwrapper.sh

Step 10: set up Atom editor
==========================

Install Atom editor
-------------------

.. code-block:: shell

  $ brew cask install atom

Install basic Atom packages and themes
--------------------------------------

.. code-block:: shell

  $ apm install atom-sort-projects block-comment busy-signal editorconfig highlight-selected \
    intentions language-restructuredtext linter linter-eslint linter-flake8 linter-ui-default \
    monokai react

Step 11: set up Docker
======================

.. code-block:: shell

  $ brew cask install docker

Step 12: set up PostgreSQL
==========================

Install PostgreSQL
------------------

.. code-block:: shell

  $ brew install postgresql
  $ brew services start postgresql

First login to PostgreSQL
-------------------------

.. code-block:: shell

  $ createdb `whoami`
  $ psql

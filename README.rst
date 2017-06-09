Mac OS X development setup
##########################

Step 1: check for system updates
================================

Go to: **Apple Icon -> About this Mac -> Software updates**

Step 2: install Homebrew and Homebrew-Cask
==========================================

.. code-block:: shell

  $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  $ brew tap caskroom/cask

Step 3: install packages using brew
===================================

.. code-block:: shell

  $ brew list
  adns
  bash-completion
  gdbm
  gettext
  git
  gmp
  gnutls
  go
  gnupg
  icu4c
  iproute2mac
  jpeg
  jpegoptim
  libassuan	libgpg-error
  libgcrypt
  libffi
  libksba
  libtasn1
  libunistring
  libusb
  nano
  ncurses
  nettle
  node
  npth
  openssl
  p11-kit
  pinentry
  python
  python3
  readline
  sqlite
  xz
  $ brew cask list
  atom
  etcher
  firefox
  gimp
  google-chrome
  iterm2
  libreoffice
  limechat
  meld
  skype
  vlc

Step 4: install common Python packages & tools
==============================================

.. code-block:: shell

  $ pip install pipenv virtualenvwrapper

Step 5: set up bash
===================

.. code-block:: shell

  $ mkdir ~/Documents/Workspace
  $ curl "https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash" --silent --output "$HOME/.git-completion.bash"

.bash_aliases
-------------

.. code-block:: shell

  alias brewup='brew update; brew upgrade; brew prune; brew cleanup; brew doctor'
  alias cdworkspace='cd ~/Documents/Workspace'

.bash_profile
-------------

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

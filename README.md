TabbedMux
=========

GNU Screen and TMux have become part of most users' work flow when using SSH to access remote systems as have tabbed GUI terminal emulators. Unfortunately, this leads to the situation of have many tabs open: some for the local machine and some for TMux sessions to remote system. Two problems arise:

  1. It's easy to start programs in local windows, then loose the ability to access them remotely later.

  2. Remote systems will often have many windows open, resulting in nested layers of windows (“windows” in tabs in windows).

TabbedMux connects to remote systems using SSH, starts TMux, and creates one tab in a GUI window for each TMux window that exists in the remote system. All the tabs from all the systems are promoted to a single layer (i.e., no nesting).

Note: window means two different things to GTK+ and TMux. It's confusing. Sorry.

INSTALLATION
------------

For Ubuntu 14.04 or later:

    sudo apt-add-repository ppa:apmasell/ppa
    sudo apt-get update
    sudo apt-get install tabbedmux

For everyone else:

  1. Install the Vala compiler 0.22 or later.
  2. Install development headers for GTK+ 3.10, Gee 0.8, Vte 2.90, libnotify, and libssh2 1.4, or newer versions.
  3. `make && sudo make install`
  4. Install tmux 1.8 or later on the local system and any remote systems you wish to access.

BUGS
----

The TMux library has an issue that can cause multiple sessions to blend together. Since most users don't use this feature, it's not a big deal. It's fixed after 1.9. http://sourceforge.net/p/tmux/tickets/94/

Occasionally, stuff comes back from no apparent session and TabbedMux will create a dead tab.

TMux's model makes it rather difficult to have multiple GTK+ windows because of the way resizing works. For now, everything is stuck in a single window.

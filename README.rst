ferm README
===========

The 'go-rewrite' branch is my attempt and re-writing ferm in golang. LOL


Description
-----------

ferm is a frontend for ``iptables``. It reads the rules from a structured
configuration file and calls iptables(8) to insert them into the
running kernel.

ferm's goal is to make firewall rules easy to write and easy to
read. It tries to reduce the tedious task of writing down rules, thus
enabling the firewall administrator to spend more time on developing
good rules than the proper implementation of the rule.

To achieve this, ferm uses a simple but powerful configuration
language, which allows variables, functions, arrays, blocks. It also
allows you to include other files, allowing you to create libraries of
commonly used structures and functions.

ferm, pronounced "firm", stands for "For Easy Rule Making".


Installing ferm
---------------

  make install

The package does not need to be compiled, just make sure you have ``perl``
(which is present in any base Linux system) and ``iptables`` (including
``iptables-save`` and ``iptables-restore``), and a kernel supporting
``netfilter``.

Run the make install script as root to install the package in
its best location so it can be reached from the command line when
called. The manual page will also be installed.

That's all!


Uninstalling ferm
-----------------

  make uninstall

Ferm can now be quickly removed from the system by issuing a "make
uninstall" command (as root, of course). This will not remove any
configuration files of course!


Getting started
---------------

The ferm(1) man page provides extensive documentation about the ferm
syntax.  To get started, try one of the example files, and modify it
for your needs.

If your machine is already firewalled and you wish to switch to ferm,
the ``import-ferm`` script comes handy.  It converts the current
firewall rules to a ferm configuration file:

  import-ferm > /etc/ferm/ferm.conf

After that, let ferm install the new ruleset:

  ferm /etc/ferm/ferm.conf

Be careful, don't lock yourself out of remote machines!  Use the
interactive mode (``--interactive``, ``-i``) often!

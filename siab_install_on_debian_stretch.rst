SiaB install on debian stretch
===============================

This document is a SEBA in a BOX(SiaB) installation on debian 9 (stretch).

Hardware spec.
---------------

* CPU: 8 cores (minimum)  / 16 cores (recommended)
* Memory: 16 GiB (minimum) / 32 GiB (recommended)
* Disk: 20 GiB (minimum) / 50 GiB (recommended)

Prerequisites
---------------

I assume debian 9 (stretch) GNU/Linux is installed and updated.
The user should have a sudo privilege.::

    ~$ sudo apt update
    ~$ sudo apt upgrade
    ~$ sudo reboot

Install packages
-----------------

Install the necessary packages before building SiaB.::

    ~$ sudo apt install -y git make bridge-utils

Install SEBA
-------------

Create a directory to install SEBA.::

    ~$ mkdir cord
    ~$ cd cord

Clone automation-tools and helm-charts git source.::

    ~/cord$ git clone https://github.com/iorchard/automation-tools
    ~/cord$ git clone https://gerrit.opencord.org/helm-charts

Go to automation-tools directory and patch SiaB Makefile for debian.::

    ~/cord$ cd automation-tools
    ~/cord/automation-tools$ patch -p0 < seba-in-a-box-for-debian.patch

Run Makefile with make command. I'll run ponsim.::

    ~/cord/automation-tools$ cd seba-in-a-box
    ~/cord/automation-tools/seba-in-a-box$ make ponsim
     ...
    echo "SEBA-in-a-Box installation finished!"
    SEBA-in-a-Box installation finished!

It will take about 10 minites so take a coffe break.

To go back to pristine state, run 'make reset-kubeadm'.

Now you can go to xos-gui with http://<server-ip>:30001/.








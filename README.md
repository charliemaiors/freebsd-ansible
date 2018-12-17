Role Name
=========

This role will manage a FreeBSD installation and from package upgrade to src compile.

Requirements
------------

No requirement

Role Variables
--------------

This roles relies on these variables:

* base_compile: boolean variable used as flag for source code compile (using [build](https://www.freebsd.org/cgi/man.cgi?build(7)) method).
* update: used as enumerative it could be simple or full, when is settled to "simple" only the target host will be updated, when is settled to "full" also the jails (if there any) will be updated.
* release: in case of a major (or minor) release set this variable (like when you type ```freebsd-update upgrade -r <release>```)
* handle_ports: used in case of port fetch or extract (using ```portsnap```)
* components: is a list of components of the main system like ports, src, base-dbg (see [bsdinstall](https://www.freebsd.org/doc/handbook/using-bsdinstall.html)) 

Dependencies
------------

No dependencies

Example Playbook
----------------

This is an example playbook:

    - name: FreeBSD
      hosts: all
      become: true
      vars:
        - components:
        - src
      roles:
        - { role: freebsd-ansible, base_compile: true, release: "12.0-RELEASE"}

License
-------

BSD

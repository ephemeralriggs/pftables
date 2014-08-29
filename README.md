pftables
========

Minimal rc script to save / restore pf tables to / from disk upon reboots

While the [FreeBSD Handbook on pf](https://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/firewalls-pf.html) explains the simple steps necessary to make pf tables survive a reboot, it does not point to an already existing script.
This rc script provides a minimum solution.
It expects the following variables to be set in /etc/rc.conf:

```
pftables_enable="YES"
pftables_list="NameOfTable1 NameOfTable2 NameOfTable3" # ...and so on
pftables_dir="/path/to/existing/dir/where/tables/should/be/stored"
```

The tables mentioned in `pftables_list` are the same names as in pf.conf.
The script will then save all the mentioned tables upon system shutdown and restore them upon system startup.

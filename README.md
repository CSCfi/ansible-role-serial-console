ansible-role-serial
=========

Add serial console output for the grub and kernel boot options (ttyS0,115200)

Requirements
------------

**HP**

ansible-role-hp-spp contains tools, hponcfg for changing iLO settings and conrep for BIOS.

Changes on an HP XL450 (SL4510 Apollo):

iLO4 changes:
 - set Serial Command Line Interface to: 115200

BIOS changes (done with conrep, installed by ansible-role-hp-spp):

    <Section name="System_COMA" helptext="Settings for UART 1 on systems that support it.">COM2</Section>
    <Section name="System_COMA_IRQ" helptext="Settings for UART 1 on systems that support it.">IRQ3</Section>
    <Section name="System_Virtual_Serial_Port" helptext="Virtual Serial Port Settings for systems that support it.">COM1</Section>
    <Section name="System_Virtual_Serial_Port_IRQ" helptext="Virtual Serial Port IRQ Settings for systems that support it.">IRQ4</Section>

A reboot and iLO reset is needed.

**DELL**

This role also works on Dell servers. No changes needed in BIOS/iDRAC for an R430 to make this work:

<pre>
ipmitool -H host.example.com -e ? -U user -P password -I lanplus sol activate
</pre>

Role Variables
--------------


see defaults/main.yml

Dependencies
------------


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-role-hp-serial }

License
-------

MIT

Author Information
------------------


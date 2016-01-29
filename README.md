ansible-role-hp-serial
=========

Add serial console output for the grub and kernel boot options (ttyS0,115200)

Requirements
------------

ansible-role-hp-spp contains tools, hponcfg for changing iLO settings and conrep for BIOS.

Changes on an HP XL450 (SL4510 Apollo):

iLO4 changes:
 - set Serial Command Line Interface to: 115200

BIOS changes (done with conrep, installed by ansible-role-hp-spp):

<pre>
  <Section name="System_COMA" helptext="Settings for UART 1 on systems that support it.">COM2</
Section>
  <Section name="System_COMA_IRQ" helptext="Settings for UART 1 on systems that support it.">IR
Q3</Section>

  <Section name="System_Virtual_Serial_Port" helptext="Virtual Serial Port Settings for systems that support it.">COM1</Section>
  <Section name="System_Virtual_Serial_Port_IRQ" helptext="Virtual Serial Port IRQ Settings for systems that support it.">IRQ4</Section>
</pre>

A reboot and iLO reset is needed.

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


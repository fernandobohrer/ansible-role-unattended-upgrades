# Ansible Role: unattendedupgrades

An Ansible role that deploys and configures the unattendedupgrades package so that security updates are automatically installed on Linux boxes.

## 🚀 Motivation

Keeping track and installing security updates and patches can be challenging. It would be nice to automate this task.

## 📑 Role Variables

Check `defaults/main.yml`.

## 🧰 Dependencies

None.

## ⚡ Quick start

An example of how integrate this role to an Ansible playbook can be found here:

```yml
---
- name: Deploy unattendedupgrades
  hosts: all
  become: true
  gather_facts: true
  roles:
    - fernandobohrer.unattendedupgrades
```

If you want to install the security patches between 0500 and 0600 AM and automatically restart the machines if required, use the example below instead:

```yml
---
- name: Deploy unattendedupgrades
  hosts: all
  become: true
  gather_facts: true
  vars:
    unattended_upgrade_automatic_reboot: true
    apt_daily_upgrade_timer_on_calendar: "*-*-* 05:00"
    apt_daily_upgrade_timer_randomized_delay_sec: 60m
  roles:
    - fernandobohrer.unattendedupgrades
```

## ⚙️ Compatibility

This role was tested on and is confirmed to work with the following Linux distributions:

- `Debian 12`
- `Ubuntu 22.04`
- `Ubuntu 24.04`

Details can be found in the [Molecule][01] scenarios available in the `molecule` folder.

## ⚠️ Warning

This Ansible role was tested on the above mentioned Linux distributions considering their default configuration. Your environment might have a different configuration or requirements which might conflict with the options that this role uses.

With the above in mind, it is **imperative** that you familiarize yourself with what this role does and test it on non-production machines **before** applying it to machines in a production environment.

## 📝 License

This project is licensed under the terms of the [MIT license][02].

[01]: https://github.com/fernandobohrer/ansible-molecule-scenarios
[02]: /LICENSE

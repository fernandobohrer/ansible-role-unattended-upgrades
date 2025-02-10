# Ansible Role: unattended_upgrades

An Ansible role that deploys and configures the `unattended-upgrades` package so that security updates are automatically installed on Linux boxes.

## 🚀 Motivation

Keeping track and installing security updates and patches can be challenging. It would be nice to automate this task.

## 📑 Role Variables

Check [here][01].

## 🧰 Dependencies

None.

## ⚡ Quick start

An example of how integrate this role to an Ansible playbook can be found here:

```yml
---
- name: Deploy unattended-upgrades
  hosts: all
  become: true
  gather_facts: true
  roles:
    - fernandobohrer.unattended_upgrades
```

If you want to install the security patches between 0500 and 0600 AM and automatically restart the machines if required, use the example below instead:

```yml
---
- name: Deploy unattended-upgrades
  hosts: all
  become: true
  gather_facts: true
  vars:
    untnd_pgrds__automatic_reboot: true
    untnd_pgrds__apt_daily_upgrade_timer_randomized_delay: 60m
    untnd_pgrds__apt_daily_upgrade_timer_on_calendar: "*-*-* 05:00"
  roles:
    - fernandobohrer.unattended_upgrades
```

## ⚙️ Compatibility

This role was tested on and is confirmed to work with the following Linux distributions:

- `Debian 12`
- `Ubuntu 22.04`
- `Ubuntu 24.04`

Details can be found in the [Molecule][02] scenarios available in the `molecule` folder.

## ⚠️ Warning

This Ansible role was tested on the above mentioned Linux distributions considering their default configuration. Your environment might have a different configuration or requirements which might conflict with the options that this role uses.

With the above in mind, it is **imperative** that you familiarize yourself with what this role does and test it on non-production machines **before** applying it to machines in a production environment.

## 📝 License

This project is licensed under the terms of the [MIT license][03].

[01]: defaults/main.yml
[02]: https://github.com/fernandobohrer/ansible-molecule-scenarios
[03]: /LICENSE

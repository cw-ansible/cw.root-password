<!--

---
lang: american
---
-->

[![Build Status](https://travis-ci.org/cw-ansible/cw.root-password.svg?branch=master)](https://travis-ci.org/cw-ansible/cw.root-password)
[![Tweet this](http://img.shields.io/badge/Tweet-it00aced.svg)](https://twitter.com/intent/tweet?tw_p=tweetbutton&via=renard_0&url=https%3A%2F%2Fgithub.com%2Fcw-ansible%2Fcw.root-password&text=Run%20linux%20from%20a%20%23tmpfs%20filesystem%20in%20%23RAM.)
[![Follow me on twitter](http://img.shields.io/badge/Twitter-Follow-00aced.svg)](https://twitter.com/intent/follow?region=follow_link&screen_name=renard_0&tw_p=followbutton)


# Root Password

This role can be used to change the root password on a server.

## Usage

Include `cw.root-password` role to your playbook.

## Description

With this role you can provide a cleartext password. It used `chpasswd` on
old distributions or use the `user` Ansible module on modern distributions.
If you use the a new distribution the password is hashed using a `sha512`
algorithm.

Just be aware that the root password is not encrypted in any means, thus do
not use this module if this is an issue for you or if you are not in a
trusted environment.

The main purpose of this role is to setup and change the root password on a
massive amount of servers having the password depending on the hostname.

For each server, the root password is `ABC:passwd-base:ZYX` where `ABC` are the
first 3 letters of the hostname and `ZYX` the last 3:

    root_password: '{{ (ansible_hostname)[0:3] }}:passwd-base:{{ (ansible_hostname)[0:-3] }}'


## Configuration

See specific documentation in `defaults/main.yml`


## Copyright

Author: Sébastien Gross `<seb•ɑƬ•chezwam•ɖɵʈ•org>` [@renard_0](https://twitter.com/renard_0)

License: WTFPL, grab your copy here: http://www.wtfpl.net

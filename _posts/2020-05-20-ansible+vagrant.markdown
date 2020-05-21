---
layout: post
title: Ansible + Vagrant 
date: 2020-05-20 19:20
comments: true
categories: [devops]
tags: [devops]
keywords: vagrant, ansible, devops
description: DevOps Books
seo:
  date_modified: 2020-05-13 20:00:00 -0300
---
---

<!--more-->

# Ansible

```
.
├── _provision
│   └── main.yml
│   └── _tasks
│       └── main.yml
│   └── _vars
│       └── main.yml
|
├── _vagrant-box
│   └── Vagrantfile
```

# Vagrant


```sh

  #Vagrantfile
  
  Vagrant.require_version ">= 2.2.0"

  Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/trusty64"
    config.vm.network "public_network"

    config.ssh.insert_key = false

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "../provision/main.yml"
    end

  end
```

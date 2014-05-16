---
layout: post
title: "Vagrant + Puppet: A case study in provisioning development environments"
date: 2014-05-15 08:06:24 +0200
comments: true
published: false
categories:
- devops
- puppet
- vagrant
---
Over the past four weeks, I worked on a side-project to learn puppet.
On my company laptop, I am running Windows 7. But that is not a well-suited environment for development.
So I installed a VirtualBox running Ubuntu and all my development tools (like IntelliJ IDEA).

Some of my colleagues also got interested in this setup, so I provided them a base box with some tools already installed.
But keeping that up-to-date is a tedious task. So I picked this base-box as a side-project and tried to provision this using puppet.

To kick-start the provisioning, I used vagrant.

So, I can proudly present the results of this project. I would appreciate any feed-back on this blog or on github.

<!-- more -->

# How to start?

* Install [Vagrant](http://www.vagrantup.com) 
* Clone the [vagrant-dev](http://github.com/rattermeyer/vagrant_dev) git repository
* And run ``vagrant up`` in this directory

This should give you a running box. You still need to re-install VirtualBox guest additions and the like. Have a look at the README

# Experiences
## Puppet
Puppet is an awesome tool. But I had my difficulties with it and the development process of creating modules.

* I think there are a lot of modules, on the net, you can easily use (good)
* But often, I have the feeling that these are only a starting point for your own customizations (bad)

Am not sure, if I have specific requirements, but I guess every environment is specific, but more often than not, I had the urge to modify a module in a certain way.
That does not necessarily mean, that the modules are bad, they probably fulfill the requirements of their authors. But to create a re-usable module requires
a lot of effort, one should not underestimate. I know this for sure, because the modules, I created are mostly not reusable. They are missing tests, do not follow conventions and should expose more parameters and customization options.

Then there are some minor work-arounds in puppet, that I do not quite understand, why they are needed. For example, to create nested directories, you need to provide an array to the files resource, because no ``mkdir -p`` is supported directly.

Beside this, I would now say, that I am confident, to be able to create puppet modules if I need to. 

## Vagrant
Vagrant itself was quite easy to understand and learn. But creating a base box by hand was a tedious task. You should have your checklist ready or you are doing it multiple times or you use a tool like ``packer.io``, which was the way, I went with in the end.

Also I found an easy way to create a base box, I kept away from the preseeding. Especially, I have the impression, that ``partman`` is difficult to understand at first glance and not much material is available on the web really explaining the config parameters.

# What is missing
* Tests: If you have infrastructure as code, you should also test it. Which is possible.
* Support for proxies: In many enterprises you are forced to go through a proxy (and you have to explicitly configure it). I would like to check the vagrant proxy plugin
* Provisioning of my custom / additional git scripts that make life easier, when working with git.

# What am I going to try out
* Testing
* Proxy Support
* Vagrant and multi machine deployments to allow one Oracle DB machine and a development machine.
* Setting up ``apt-cache`` and ``squid`` on my development machine to speed-up the process of looking up packages and libraries.

# What is annoying
* Oracle stuff is not easily available on the web. So I skipped this for now.

More to follow...

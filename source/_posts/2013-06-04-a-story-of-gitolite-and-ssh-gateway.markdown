---
layout: post
title: "A story of Gitolite &amp; SSH Gateway"
date: 2013-06-04 02:07
comments: true
categories:
- SSH
- Gitolite
---

Gitolite is a really good project. What I like most is that it is
simple to install and you can wrap your head around it. I got
interested a lot in other projects like GitLab our Gitorious. But they
are a pain to install and configure.

My setup for gitolite was quite redimentary unlil now. I had a Debian
virtual machine hosting gitolite and the repository. Everyone that had
to access this machine could do it on the private network or a VPN
connection. Everything worked like a charm...

Until I had to make the repositories available to the outside world...
But git was not the only service that required the SSH port on my
firewall. I had to make it somehow play nice with other friends. After
some searching I diceided, thanks to the nicely done article
[Configuring an SSH Gateway](http://tumblr.spantz.org/post/211936636/configuring-an-ssh-gateway),
that I had to give access to gitolite through an SSH Gateway. The
cornerstone of method is the use of SSH keys and the
`authorized_keys`'s `command` options. If you do not want to read the
article, the idea behind the SSH Gateway is to identify an SSH
"service" as a user account on the gateway, the real user beeing
identified thanks to its SSH key. The gateway then connects to the
right machine and the right user (which it know though its key).
Nicely simple once you understand the trick. Reminds you of something
? Yes, yes, the exact same trick that allow gitolite to make its magic
operate. Gitolite identify the real user though its SSH key and then
"just" check some permisions to check if she have the right to acccess
this repo. I should have though of it before hearing of the SSH
Gateway.


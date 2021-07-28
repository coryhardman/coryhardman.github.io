---
layout: post
title: Passwords are great...
date: '2021-07-28'
author: Cory Hardman
tags: 
modified_time: '2021-07-28'
---

I am working on a product called
[Verify](https://www.veritone.com/veritone-verify/). One of its stated
objectives is to kill the use of passwords. I believe that in order to replace
something, you need to understand why it exists in the first place. In the case
of passwords, where you the use and hatred is ubiquitous, there has to be
a compelling reason for the ongoing use. So lets explore why passwords are
great.

Passwords are nominally a `something you know factor` of the three standard 
authentication factors (1 - `something you know`, 2 - `something you have`, and 3 - `something 
you are`). Passwords have become the de facto authentication mechanism 
for most of the digital age. The de facto status has come because Passwords 
have a ton of great properties compared to the other factors: 

* Passwords are always with a person. A user always knows what they know.
* Don’t depend on physical attributes about a person that may change. People lose fingers, have grease fire incidents and scare their face, etc.
* Don’t require extra hardware. Most interactive devices have a keyboard input mechanism of some sort.
* Revocable -- You can always change a password and say the old password is no longer valid if you believe it has been compromised
* Easy to implement in just about every context from app on mobile device, website on desktop, to command line interfaces. 
* Easily shared -- while not a great security property, users can and do share
    passwords with each other. Look no further than Netflix account sharing where
    this is a feature.
* Every digital user has used a password and thus user training is not
    required. This is a key premise of [Troy Hunt's essay on Why [insert thing
    here] is not a password
    killer](https://www.troyhunt.com/heres-why-insert-thing-here-is-not-a-password-killer/). 
  * As an aside, I think the same effect is occurring with SMS OTP mechanisms.
      Users are seeing this form of authentication more and more and becoming
      aware of how it works and thus more companies implement this flow instead of
      some alternative "something you have" factor.

As you can see, passwords have a lot of benefits and these are the reasons
password use continues to endure. Any product that attempts to unseat passwords
will need to provide compelling alternatives to each of these points. In a 
follow up, I'm going to write about why passwords suck. In particular about 
the attacks and the unfortunate policies that have been created in an effort to 
combat those attacks -- ultimately why those policies are failing users and 
companies that rely on passwords still.


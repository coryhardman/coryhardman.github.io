---
layout: post
title: Passwords are great...and suck!
date: '2021-08-01'
author: Cory Hardman
tags: 
modified_time: '2021-08-01'
---

I am working on a product called
[Verify](https://www.veritone.com/veritone-verify/). One of its stated
objectives is to kill the use of passwords. I believe that in order to replace
something, you need to understand why it exists in the first place. In the case
of passwords, where you the use and hatred is ubiquitous, there has to be
a compelling reason for the ongoing use. So lets explore why passwords are
great and talk about why ultimately they still suck and need to be replaced.

Passwords are nominally a something you know factor of the three standard authentication factors (something you know, something you have, and something you are). Historically they have become the de facto authentication mechanism for most of the digital age. The de facto status has come because Passwords have a ton of great properties compared to the other factors. Such as:

* In theory, passwords are always with a person. A user always knows what they know.
* Don’t depend on physical attributes about a person that may change. People lose fingers, have grease fire incidents and scare their face, etc.
* Don’t require extra hardware. Most interactive devices a keyboard input mechanism of some sort.
* Revocable -- You can always change a password and say the old password is no longer valid if you believe it has been compromised
* Easy to implement on just about every context from app on mobile device, website on desktop, to CLI. Requiring very little special software beyond bcrypt. 
* Easily shared -- while not a great security property, users can and do share
  passwords with each other. Look no further than Netflix account sharing where
this is a feature.
* Every digital user has used a password and thus user training is not
  required. This is a key premise of [Troy Hunt's essay on Why [insert thing
here] is not a password
killer](https://www.troyhunt.com/heres-why-insert-thing-here-is-not-a-password-killer/). I think there is an often overlooked reason passwords are so widespread. Everything that attempts to replace them has a big lift around education of users.
  * As an aside, I think the same effect is occuring with SMS OTP mechanisms.
Users are seeing this form of authentication more and more and becoming
aware of how it works and thus more companies implement this flow instead of
some alternative "something you have" factor.

As you can see, passwords have a lot of benefits and these are the reasons
password use continues to endure.  

Attacks:
* Phishing -- Tricking users into typing their password into an attacker controlled website
* Database breaches -- Attackers dumb databases as the password has to be stored by the authenticator
* Password Spraying attacks -- Attackers simply attempt to use common passwords on known usernames on many websites
* Password brute force attacks -- Attackers simply guess the password, generally pretty easy as most passwords are < 10-15 bits of entropy (<32k guesses)

Policies to combat (most don’t work):
* Security images -- Doesn’t provide any value -- The website shows a security image to the user while they are logging in, in theory the attacker wouldn’t know what the security image should be shown. However attackers simply pipe the security image through to the user
Security strength requirements -- Idea is to require users to provide stronger, harder to guess, passwords. If a user participates it does help against brute force and spray attacks. However users typically work around this by reusing the password, which means the password is only secure until one of the many places the user used the password has a database breach
* Fixed Password rotation policies -- doesn’t provide any value -- many password systems will require a person to rotate their password on a regular basis. The logic of a password rotation is that a user’s password may have been compromised, so it should be changed. So if you have a policy to change every 30 days and the password is compromised on day 2, the attacker still gets 28 days to do whatever damage they want. So in order to defend against this, you need to rotate on Day 1. The argument iterable becomes as ridiculous as you play it out. Generally: if a system requires regular password rotations it is fulfilling a compliance requirement incorrectly (ahum Okta). 
  * Note: An alternative to this policy is to look for signs that passwords have been compromised. Such as having browser extensions looking for users using their password on other websites or looking for the password in password breaches. When compromise is detected, then require a password rotation
* Security Questions  -- doesn’t provide much value -- Concept is that the password could be compromised, user choose bad passwords (low entropy) so what if you tried to have something that was unique for this website. Hence enter the “security question” idea. If a user has a strong password, the security question worsens security as they tend to be used in recovery situations. However they in theory could help increase the complexity the attacker needs to guess, but they are trivially phished and hence gotten around quite easily. Generally: if a high security system has security questions, you should be very concerned about the security of that system (ahum Okta)
* Time based auto logout/reauth -- The idea is to force the user to logout on a regular schedule, many banks have a 10-20 minute session idle limit and force a reauth after that. This can be great at helping limit the damage to session hijacking but can harm your ability to defend against phishing attacks as users are use to typing in their password nearly constantly to interact with your product. 
* Password guessing limits -- Many systems put in place an exponential cooldown period on password guessing, this helps defend against bruteforce and spraying attacks. This is a good way to compensate for lower entropy passwords
* Injecting artificial password correctness delays -- The slower you can tell a bruce forcer if the password they type in is correct the fewer passwords they can guess given a time bound. This is a good way to compensate for lower entropy passwords. But can be taken to an extreme to give a poor good user experience.

Most systems have combinations and slight variants of these policies. When done correctly (a context aware concept) the policies can make passwords back into being a strong factor while authenticating a user. However you will notice, there is almost no policy that defends against phishing attacks. This is because something you know factors are phishable. 

So passwords are already being relegated to just one of many factors in most high security systems. In the context of Verify, it will be thought of as one of Numerous Factors. As such we will have a lot more flexibility to dramatically decrease the pain points of passwords (no rotations, lower entropy requirements, not asked reguirely). We will instead use passwords intelligently given the context considerations such as:
What interface is the user being challenged in? A CLI likely won’t have a camera. 
How sensitive is the service they are logging into?
Other factor considerations: device fingerprint, behavior analysis, location, etc


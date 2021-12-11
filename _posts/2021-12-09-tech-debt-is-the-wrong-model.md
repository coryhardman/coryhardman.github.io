---
layout: post
title: Tech debt is the wrong model
date: '2021-12-09'
author: Cory Hardman
tags: 
modified_time: '2021-12-10'
---

I think tech debt is the wrong mental model to describe software issues or deficits. In fact, it is dangerous mental model because it gives the wrong impression: you can pay it down by writing a check. The alternative that I encourage everyone to adopt: Software systems are a forward progression and every previous iteration was optimized for the constraint on them. Therefore, nothing is debt but instead a change that would improve the software system in a different dimension than has been previously prioritized. 

To back up and work up to this better mental model. I roughly believe all software written is  optimized for the exact constraint imposed on the engineers who wrote it. constraint like:

* Amount of time wanting to be spent on it (aka the need to ship). Note, time wanting to be spent is not only management or client demands. It can also come from engineers wanting to move onto the next project, get the promo, etc. Also note willingness to spend more time decreases as things get "good enough"
* Desired features. Both explicitly requested and the imaged desires of consumers of the software system.
* Reliability objectives. Such as SLA of uptime, confidence in builds ability to go to production, etc
* Willingness to spend human cycles vs machine cycles to do things. For example automated database schema changes vs hiring a DB Admin to manual make the changes. Think of automation as an upfront cost whereas human manual effort as a marginal cost. 

Most of the time the constraint are not well defined ahead of time. They are discovered over the course of writing the software and the interactions between all interested parties. For example: it may be initially desirable that the system has a push on green deployment paradigm, but as shipping date approaches it is a trade off to ship with a more manual push paradigm. Similarly: engineering thinks a feature, while not requested explicitly, should be implemented and thus it ships with the product. 

This means that all interested parties are using roughly a greedy algorithm to find the optimized for the given constraint to "finish" the software system and once the software ships it has been reached. Trade offs were made: product wanted internationalization, engineering wanted load testing and push on green deployments, etc but in the end the software system was considered good enough by all voting parties and thus optimized for the constraint.

At this point: one would call the lack of load testing, push on green and internationalization as tech debt. But is it? Debt is something that you have to pay off. Perhaps it turns out the product is not straining under the load and the market fit isn't demanding support for more languages. Turns out: these were imaged desired features or reliability objectives and not things that were critical to the product.

However, perhaps, team is seeing it as hard to add new features to the product in a reliable way. They do light refactoring to add the needed abstractions to the data model for new features and the pushes keep needing to be rolled back. This is taking up a lot of engineering cycles, human manual effort, needing to hand hold each of these releases. At this point you could say the lack of push on green is tech debt. However as we saw above, calling every imaged desirable thing as tech debt can mean you spend cycles on things that are not needed. The software system has a clearly present explicit feature need: releases should not consume so much engineering cycles. Thus making this a feature or reliability enhancement rather than debt to be paid. 

Treating software as only on a progression vs an accumulation of debt that has to be paid can free everyone's mind and has some desirable affects:

* Instead of product needing to give engineering x% of their time to "pay down debt", product and engineering get to consider the work as partners. Meaning both product and engineering are advocating for the work and are bought in on the trade offs
* Shifts understanding of the developers from thinking the software project is hopelessly broken to thinking, the product is as good as it has needed to be to this point and now there are simply different requirements. This small positive prospective change removes fatalistic thinking and empowers owners to know nothing about the product is immutable.
* Makes improvements purposeful. There is an explicit objective that everyone
    knows is the desired outcome and everyone moves in the same direction. The
    counter to this is to have a "tech debt week" or "debt repayment sprint".
    Firstly: 99% of potential improvements are larger than 1 or a team of
    unprepared+uncoordinated engineer(s) can accomplish within 1 week or
    sprint. Secondly: these turn into cycles of engineers doing the things
    management never gave them the room to work on before now and they have no
    hope of actually finishing and thus increasing the things that need to be
    supported without sufficient staffing.

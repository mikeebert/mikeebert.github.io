---
layout: post
title: Three JVM Gotchas: Null stacktraces, Jackson JSON recursion, DNS
Caching
date: '2017-10-23'
tags: []
---

Recently the team and I came across a few JVM gotchas that were such
doozies I wanted to write them down in case anyone else comes across
them and is scratching their heads- or more likely, I myself come across
them again in a few months and need to remember how to fix them.

#### The case of the missing Stacktrace
For the past couple weeks we've had an error showing up sporadically in our logs for a `NullPointerException` that had no stacktrace whatsoever. We knew what route it was hitting and had a good hunch of where it was happening, but unfortunately we couldn't pin point without the stacktrace.

#### Your serializer is a straight up app killer
`jackson` will serialize your objects

#### It's Noon on a Sunday, do you know where your DNS is?
The JVM can cache DNS lookups

#### Chrome caches your SSL certificates

---
layout: post
title: "JVM Got-me: where is my stacktrace???"
date: '2017-12-07'
tags: [java]
---

Recently the team (which includes a couple of very experienced Java devs) and I came across a few JVM gotchas that I wanted to write down just in case anyone else comes across them and is scratching their heads. Here's the first one:

### The case of the missing Stacktrace
A couple of weeks ago we had a `NullPointerException` showing up in our logs that had no stacktrace whatsoever. Our JavaScript client was hitting an endpoint so our server logs told us which controller and action it was, but that was all we had to go on. Fortunately the action was just a few lines so we had a pretty good idea what was happening, but the more curious issue to us was why there wasn't any stacktrace.

Fortunately for us, this is a pretty common 'gotcha' and there are several StackOverflow threads and blog posts that pointed us to the Oracle docs. [Here's a pretty succint post on the topic.](https://plumbr.io/blog/java/on-a-quest-for-missing-stacktraces).

As it turns out, once the JVM sees an error over and over, as an optimization it will recompile and just throw an empty stacktrace instead of reporting the entire thing over and over again. It's not very difficult to trigger this either. I purposefully created a link on a page to trigger the exception locally, and I only had to quickly click on it about 20 times to see the stacktrace disappear from the logs.

If we don't want our stacktraces to disappear then the solution is pretty simple, we'd just need to add `-XX:-OmitStackTraceInFastThrow` to our JVM startup paramaters.

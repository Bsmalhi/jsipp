# JSIPp

[![Build Status](https://travis-ci.org/rkday/jsipp.png?branch=master)](https://travis-ci.org/rkday/jsipp)
[![Coverage Status](https://coveralls.io/repos/rkday/jsipp/badge.png?branch=master)](https://coveralls.io/r/rkday/jsipp?branch=master)

## What is this?

This is an experimental rewrite of [SIPp](http://sipp.sourceforge.net) in Java, designed to be compatible with the same XML files and command-line arguments, and have roughly equal performance, but to provide a cleaner, smaller, more modular base for faster future development.

## Why a rewrite in Java?

A lot of function in SIPp - the hashed wheel timer, select/epoll loops, XML parsing - is part of the Java standard library or available in other common libraries like Netty. Being able to rely on standard implementations of these, and focus on the test-tool-specific logic, should make SIPp a lot smaller, more stable and easier to manage (the C++ version is currently at over 20,000 lines of code compared to under 2,000 in this Java version).

Java is also able to roughly match the performance of C++, which is crucial as one of SIPp's main applications is in performance testing.

Also, one of the main issues with SIPp was the lack of good unit test support - Java's unit testing (for example, with JUnit) seems much more mature than the C++ test libraries.

## What's the status?

https://github.com/rkday/jsipp/wiki/Current-Status has a full overview.

## How can I use it?

It's usable with `java -jar jsipp-0.0.5.jar -sf message.xml -r <rate per second> <server>:<port>`.

To see the results, an ncurses UI and a web UI are available - see https://github.com/rkday/jsipp/wiki/ZeroMQ#sample-programs.

## How can I contribute?

See the [design notes](https://github.com/rkday/jsipp/blob/master/design.md) for an overview, and [the SIPp docs](http://sipp.sourceforge.net/doc/reference.html) for a list of the function that needs to be ported over. In particular, more keywords would be great, as would more in-call actions, CSV file injection and maybe 3PCC - I'm planning to focus my own efforts on transport protocols and media handling early on, rather than tackling those areas.

Feedback on the [planned future directions](https://github.com/rkday/jsipp/blob/master/future-directions.md) would also be useful, especially if there are use-cases it doesn't cover.

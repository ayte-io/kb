---
title: Dogma
---

This is a dedicated page that summarizes basic principles on creating 
and publishing a project, be it library, application, plugin, 
configuration management extension or anything else. Call it manifesto 
if you want.

## Projects for people, not vice versa

Every released project, be it library, service or anything else, must be
targeted to reduce end user effort. It is easy to find oneself in 
situation where management requires more resources than saved by a 
specific solution. Try to avoid it.

## No unfinished releases

Any project release must be fully completed and must not contain any 
functionality that is not completely working, hasn't been tested but 
complex enough to be tested, working not as intended and so on.

## No parts of future functionality in releases

Releases must not contain any functionality scheduled for future 
releases and/or that is not documented at all, so neither end users may 
misuse it nor it may change it's contract in later release while 
somebody is already using it.

Beta functionality doesn't count towards functionality described above, 
but should be explicitly marked so end users would be aware it may 
change with one of future releases.

## No undocumented released features

Release should not be performed until every complex released feature is
properly documented. Users must not be forced to dive in source code to
find answers they're looking for, unless it is related to some fine
tuning.

## Appropriate testing

Released features must be tested accordingly. While single library may 
require only unit tests, most of functionality require higher-level 
tests as well, e.g. if library provides some concurrency primitives, 
they must undergo stress tests, and if distributed consensus is 
involved, then testing application should be built around and undergo
stress test as well.

It is OK to use completely separated projects for testing as long as
they are used in release pipeline (for example, one repo with 
distributed consensus algorithm, and another repo with application that 
consumes it), i.e. project must not be released before undergoing 
corresponding tests, but it's OK if testing X requires updating Y as 
well.

## Target everyone

Released projects must not target only specific case, because it 
significantly reduces reusability and simplicity of maintenance.

When it's possible, don't bind to specific framework, unless project 
functionality is tied to that framework.

When creating general-purpose functionality, write it in C/C++ and 
provide bindings for popular languages, unless this kind functionality
requires maximum performance that should be achieved from within target
language.

## Automate all the things

All routine tasks should be automatized as much as possible. This must
be done mostly to reduce friction and keep maintainer resources spent on
addressing issues within issues themselves.

## No shortenings

Released projects API, even internal, must not shorten any names. This 
is important because a) improper naming clutters users even more, while 
they're usually just trying to keep whole domain in mind and b) using 
intuitive naming schema allows user to find symbols faster. User must be 
sure that string comparison function is called `compare_strings`, and 
not some kind of frankenstein of natural language chunks.

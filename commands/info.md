---
description: Use `ri` command to access Ruby documentation for classes, modules, and methods.
argument-hint: whatever to look up
allowed-tools: Bash(ri:*), Bash(which ri), Task, Bash(head:*), Bash(wc:*), Bash(grep:*)
---

# Rule

The `<execute>ARGUMENTS</execute>` will execute the main procedure.

# Role

You are a expert Ruby developer to look up Ruby documentation using your `ri` skill.

# Definition

<procedure name="main">
    <description>Look up Ruby documentation using `ri` skill.</description>
    <parameter name="query">The class, module, or method to look up in Ruby documentation.</parameter>
    <step>1. active the `ruby:ri` skill.</step>
    <step>2. use skill to look up the {query}.</step>
    <return>Return the documentation result.</return>
</procedure>

# Task

<execute name="main">$ARGUMENTS</execute>


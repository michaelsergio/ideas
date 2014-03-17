# Select Index

# Purpose

A tool where you pipe a command output to.
This tool records the output for later use.
Invoking the tool again with a number argument will return the text.

# Implementation
Record data to usual directory 
On linux this is /var/lib
On OS X I think this is /usr/local


# Example run
Without tool:
ls 
a.txt
b.txt
c.txt
d.txt

With tool:
ls | sindex
1. a.txt
2. b.txt
3. c.txt
4. d.txt

> vi `sindex 2`
turns into 
> vi b.txt

# Flags

Get components based on last lines formats rather than by lines
--list ['org.apache.cordova', 'a.b.c']
--csv a,b,c,d,

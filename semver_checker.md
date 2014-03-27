Semantic Versioning Checker
================================
A lot of projects don't follow Semantic Versioning.

Take OpenSSL whos api breaks almost every release.
Currently its at 1.0.2.

This project intends to shame such projects.


Flow
------
This tool will pull the commit history from a repo.

Look at all the public prototypes (user configurable).

Every commit that introduced a change to will increase the MAJOR number by 1.
Every other commit will increase the MINOR by 1 and set the PATCH to 0. 
unless it has the word fix in the commit message, in which case 
it will increase the PATCH number by 1.

It should leave a blame trail of when the version number was changed with a
reference to the commits and changes.

Terms
---------
Repo: Git first, maybe svn later.
Public Prototypes: Header files in C/C++. Top level functions in JS.


Configure
--------------
Whitelist/Blacklist that increment version number for: 
* Commit Ids
* Commit keyword (default "fixes")


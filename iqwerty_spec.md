International Qwerty iqwerty
=============================
In OSX, there exists a mode which captures long keyholds and 
presents a selection of key choices.

This specification is an attempt to port this functionality 
over to linux using ibus.

ApplePressAndHoldEnabled Emulation describes the keymap used by the 
current implementation on OSX 10.9 Mavericks.


Implementation Strategy
=========================
Attempt to do this with ibus-table first.
If that doesn't yield satisfactory result, do ibus plugin directly.



User Interface 
====================
In phase 1, using the same mechanism that ibus provides is the preferred choice.
It is worth considering emulating the same UI style that OSX uses.

It provides a UI with the following structure:
```
---------------------------
| à  á  â  ä  æ  ã  å  ā  | 
| 1  2  3  4  5  6  7  8  |
 -  -----------------------
  v
  a
 ```
 If there is enough space, the 'v' arrow is left aligned.
 If there is not, it is right aligned (in this example it would be under the 8).

 The interface component is also clickable.

Extensions
==================
One of the weaknesses of this interface in my opinion is the lack of 
customizability.

I want to be able to map certain keys to other unicode characters.

On a en_US keyboard, I want to be able to type a Euro Sign '€'.
Currently, this involves knowing the magic incantation on my keyboard,
bringing up a character map applet or searching for the glyph online.
This is an awful waste of effort. 

The user should know that the Euro symbol is a currency symbol.
Since the currency symbol on a en_US keyboard is '$' (shift-4), 
the user should be able to hold shift-4 and see a range of international 
currency keys outside of the locale.
```
Example (¢ € ₹ ₴ ฿ ¥ £)
```

Format
-----------
This should be able to be customized via a text based keymap configuration file.
The format is as follows:
```
    <BaseKey>:<Space|UnicodeKey>+
```
An example:
```
a:àáâ æãåā
```
The Mapping (right side) is an indexed map to the basekey.
Spaces represent, unindexed characters.
The UI behavior should be not to response or display the keymap.

In the example above, (1-based) index 4 is missing and will not be displayed.
Index 5 will contain æ.


Next/Prev
------------
If a mapping contains more than 10 characters, 
the '0' key is reserved for a next character.

This will move the "page" to the right.
Pages beyond 2 will have the '1' key reserved for previous.
The same turn right rule applies for pages beyond page 2 that consist of more 
than 8 characters.

It is worth considering allowing the '0' key to hold the last character,
rather than a reference to the next page.
For consistencies sake, this will not be allowed. 
The use case is if a user is looking quickly for a character and is banging 
away at the next page ('0') key, he does not accidentally insert a key.
Instead, he is met with a noop.


Quick Pick
-----------
(Option)
Double tap a letter to pick the first character.
So holding 'a' and pressing 'a' again will use the first choice.
These reduces finger movement.


ApplePressAndHoldEnabled Emulation
=====================================
The order described for each letter is show on the OSX UI in a 1-based array.
For example: holding the letter 'a' brings up a "picker" showing 8 choices. 
Pressing '5' transforms the typed a onscreen into 'æ'.
```
a
----
àáâäæãåā

s
----
ßśš

ddfghjk

l
----
ł

e
----
èéêëēėę

y
----
ÿ

u
----
ûüùúū

i
----
îïíīįì

o
----
ôöòóœøōõ

z
----
žźż

c
----
çćč

n
----
ñń
```


Possible Additions
======================
(Assuming en_US keyboard)
$ for currency keys.
```
" for international quotation marks “ ” « »「　」„ “
~ for OS keys ⌘ ⌥ ⇧ ⎋ ⇥ ⏎ ⌫ ⌽
? for ¿ (OSX calls these surrogate pairs according [surrogates])
Mathematical and logical symbols.
```

An APL configuration file because wtf not [apl].


Apologies
===========
Since I'm dealing with the brutal field of internalization, I apologize
for any mistakes, insults, or omissions to this document.
I am an Ugly American Programmer [america] and intend to insult 
everyone equally.  


References
=============
[america]: http://www.codinghorror.com/blog/2009/03/the-ugly-american-programmer.html)
[apl]: http://en.wikipedia.org/wiki/APL_(programming_language))
[currency]: http://en.wikipedia.org/wiki/Currency_(typography))
[surrogate]: http://en.wikipedia.org/wiki/Unicode_input)


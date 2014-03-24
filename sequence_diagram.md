Sequence Diagrams
==================

There exists no command line sequence diagram tools.
Seriously, WTF?

I want a .dot file style tool where I input interactions and it generates a graph for you, output as a png.

Online Example
-----------------
Input:
    title Authentication Sequence

    Alice->Bob: Authentication Request
    note right of Bob: Bob thinks about it
    Bob->Alice: Authentication Response
    Alice-->Bob: Dotted Arrow
    A->+B: Box for fn call
    B-->-A: End box
    A->A: self call

    alt Condition separated with dotted line and alt in corner
      A->B: text
    else condition name on bottom
      A->B: text
    end

    loop Looks same as alt but with loop in top left
      A->B: text
    end



[OnlineTool]:https://www.websequencediagrams.com/


Running
-----------
make compatible with graphviz options

    seqgraph -Tpng example.seq > example.png

Formats
-----------
SVG, PNG, and PDF
SVG is probably the easisest.
With that I should be able to serialize to PNG.
PDF if I need to.

Styles
----------
CSS Styling for boxes.
Minimal Boxes
UML Style
Colors
Start Actor at top (for existing objects)  or inline (for creating new objects)


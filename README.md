ShapeUp

Goal is a facial shape manager for Blender, for shapekey based facial rigs.

Refactoring of the functioning prototype is in progress.

In the end it should handle correctives and inbetweens based on their naming, as well as have filtered UI lists, and handle import and export of shapes.

Some terminology:
- hero shapes: simple shape keys with no drivers. Examples: jawOpen, lipCornerPuller, browLowerer, eyesClosed
- combination shapes/correctives/combos: shape keys that are driven by 2 or more hero shapes and are used as a corrective difference in deltas. Examples: jawOpen_lipCornerPuller, browLowerer_eyesClosed
- inbetweens/inbetween shapes: shape keys that are driven by a hero shape and act as an inbetween corrective. Examples: jawOpen_10, eyesClosed_50
- inbetween combos: a combination of inbetweens and combos. Examples: jawOpen_10_lipCornerPuller, eyesClosed_25_browLowerer_50
- puppet: a mesh, typically a head, with shape keys for the expressions.
- FACS: Facial action coding system

How it looks so far - 

![Screenshot 2023-01-04 095558](https://user-images.githubusercontent.com/78473045/210447810-a6890c5f-d933-4160-b126-aba8e6cda581.png)

TODO:
- clean up/re write code to be more readable and organized as it's becoming a bit messy:
  -  ̶r̶e̶-̶w̶r̶i̶t̶e̶ ̶s̶h̶a̶p̶e̶ ̶u̶p̶d̶a̶t̶e̶ ̶w̶i̶t̶h̶ ̶n̶e̶w̶ ̶l̶o̶g̶i̶c̶:̶
    - r̶e̶-̶w̶r̶i̶t̶e̶ ̶h̶e̶r̶o̶ ̶u̶p̶d̶a̶t̶e̶
    - r̶e̶-̶w̶r̶i̶t̶e̶ ̶c̶o̶m̶b̶o̶ ̶u̶p̶d̶a̶t̶e̶:
      - r̶e̶m̶e̶d̶y̶ ̶w̶r̶i̶t̶e̶ ̶3̶+̶ ̶c̶o̶m̶b̶o̶ ̶u̶p̶d̶a̶t̶e̶ ̶(̶s̶e̶t̶_̶c̶o̶m̶b̶o̶_̶k̶e̶y̶s̶ ̶f̶u̶n̶c̶t̶i̶o̶n̶ ̶t̶o̶ ̶a̶c̶c̶o̶m̶o̶d̶a̶t̶e̶ ̶f̶o̶r̶ ̶d̶o̶w̶n̶s̶t̶r̶e̶a̶m̶ ̶c̶o̶m̶n̶b̶o̶s̶)̶
    -  ̶r̶e̶-̶w̶r̶i̶t̶e̶ ̶i̶n̶b̶e̶t̶w̶e̶e̶n̶ ̶u̶p̶d̶a̶t̶e̶
  - re-write shape export with new logic:
  
    - -̶ ̶c̶o̶m̶b̶i̶n̶e̶ ̶d̶e̶l̶t̶a̶ ̶d̶i̶f̶f̶e̶r̶e̶n̶c̶e̶s̶ ̶f̶r̶o̶m̶ ̶a̶r̶b̶i̶t̶r̶a̶r̶y̶ ̶n̶u̶m̶b̶e̶r̶ ̶o̶f̶ ̶m̶e̶s̶h̶e̶s̶
    
    - -̶ ̶e̶x̶p̶o̶r̶t̶ ̶t̶o̶ ̶a̶ ̶s̶p̶e̶c̶i̶f̶i̶c̶ ̶f̶o̶l̶d̶e̶r̶
    - combine export methods
  - delete unnecessary code and re-factor classes carried over
- filter the list on the left to only display hero shapes, re-sort alphabetically. Alternatively create a filtered list without values, like the one on the right but only with hero shapes, and different menu with the complete list with values.
- explore quickset (setting the selected shape to 1 and everything else to 0)
- explore other export options, like alembic
- create a build function that builds the shape network based on selected shapes and their naming
  - while getting a dedicated button, this willl be covered by the new update logic. 
-  ̶e̶x̶p̶l̶o̶r̶e̶ ̶t̶h̶e̶ ̶p̶o̶s̶s̶i̶b̶i̶l̶i̶t̶y̶ ̶o̶f̶ ̶u̶p̶d̶a̶t̶i̶n̶g̶ ̶m̶u̶l̶t̶i̶p̶l̶e̶ ̶s̶h̶a̶p̶e̶s̶ ̶a̶t̶ ̶o̶n̶c̶e̶ ̶b̶a̶s̶e̶d̶ ̶o̶n̶ ̶n̶a̶m̶i̶n̶g̶
- explore by state updates
- explore freezing shapes:
  - Basically define back existing upstream shapes (?)
- explore multi selection inside the UI List

- extras like :
  - eye/teeth connect 
  - generate meniscus
  - jaw extract 
  - k̶e̶y̶l̶i̶n̶e̶ ̶i̶m̶p̶o̶r̶t̶ ̶
  - f̶a̶c̶e̶ ̶s̶e̶t̶ ̶i̶m̶p̶o̶r̶t̶ ̶ 
  - split
  - combine
  - live copy using geo nodes
  - live relax using geo nodes and corrective smooth
- a transfer tool based on a sparse alignment mesh and a layered joint system
- pose editor for saving, naming and mixing poses
- animation menu for importing and managing QC roms


-----------
Simple flow chart for the update process:

![Untitled Diagram(5)](https://user-images.githubusercontent.com/78473045/207794114-774d9fef-8a2a-42a1-bcd8-1784db41452a.jpg)


More detailed flow chart on how the corrective update process:

![Untitled Diagram(8)](https://user-images.githubusercontent.com/78473045/208491537-5fd8cd7e-8f50-4eea-aa75-04c3ce108637.jpg)


More detailed flow chart on how to get a corrective delta difference between a raw combo shape and a tweaked corrective vie shape keys:

![Untitled Diagram(4)](https://user-images.githubusercontent.com/78473045/207691890-0ae56f25-1c5b-4925-8649-5208a7960650.jpg)

Instead of the shape key approach the difference in vert position is calculated vie the difference mesh approach.

--------------

Some expressions for non linear corrective drivers. Credit goes to sourvinos and bandages from blenderartists. - 

(sqrt(s1 * s2)) * (s1 + s2) / 2 .9,.1 - .150 | .5,.5 - .25 | .3,.7 - .229

sin(pi/2 * s1)*sin(pi/2 * s2) .9,.1 - .155 | .5,.5 - .5 | .3,.7 - .405

sin(sqrt(pi/2 * s1))*sin(sqrt(pi/2 * s2)) .9,.1 - .358 | .5,.5 - .6 | .3,.7 - .549


These do look weird if there are correctives as well as inbetweens, the later having a linear activation/deactivation expression. Here's an expression that is probably used by many studios for that reason. While less correct, it's probably more suitable for animation as the result doesn't have hickups while blending deltas.

(((s2>0) * (s1)) + ((s1>0) * (s2)) )/2

-------------

More detailed flow chart on how the inbetween update process:

![Untitled Diagram(6)](https://user-images.githubusercontent.com/78473045/207964779-400980f5-fd57-4919-ad71-85a8e269d51c.jpg)

Little bit of background on the inbetween expression. (Thanks to bandages from blenderartists for that)

Take the case of 3 different keys, one to trigger fully at input 0.33, the next to interpolate in from input 0.33 to maximum at input 0.67, as the first one likewise interpolates out, and then a final one. Might as well interpolate linearly.

First thing you’re doing is a simple remap operation: input 0.33-0.67 -> SK2 0-1. First you find your range: 0.34 (0.67-0.33). You subtract your minimum bound from your input, then you divide by your range. 0.33-0.33/0.34 = 0. 0.67-0.33/0.34 = 1. Clamp it. I think there’s a python clamp(). Maybe saturate(), I dunno what they call it.

That gives you a 0-1 value out of each shapekey. How do you interpolate out? If they’re clamped, most easily by checking them in reverse order: SK2 = SK2 - SK3. SK1 = SK1 - (SK2 + SK3).

So let’s establish a little bit of nomenclature:
i = input value
SK1 = output for shapekey1
a = min bound of SK1
A = max bound of SK1
b = min bound of SK2
etc

To clarify, at i=A, you’re getting SK1 at 1.0 and no other shapekeys. At B, you’re getting SK2 at 1.0 and no other shapekeys. b=A and c=B, it just makes it easier to write.

SK3 = clamp((i-c)/(C-c))
SK2 = clamp((i-b)/(B-b)) - SK3

Etc.

Okay, just checked, no clamp. Use max(min(n, 1.0), 0.0) to clamp in Python I guess.

So SK3 = max(min((i-c)/(C-c), 1.0),0.0)

Extrapolates to however many shapekeys you want, if you can follow the reasoning.

max(min(({}-{})/({}-{}), 1),0)

------

The build puppet workflow is basically the update shape process in a loop, selected to active. The export process is the reverse, but simpler in some aspects. Here's a basic flow chart for the export process - 

![Untitled Diagram](https://user-images.githubusercontent.com/78473045/208230609-c6bde3e4-fe1b-46de-9b55-10950264533b.jpg)









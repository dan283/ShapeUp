
Work in progress

Introducing ShapeUp - the ultimate shape key management tool for Blender. 

With ShapeUp, you can easily edit, transfer, export, and import shape keys for your FACS-based facial rigs. This powerful addon streamlines the shape key workflow, saving you time and effort while giving you more control over your animation projects. Whether you're a professional animator or a hobbyist, ShapeUp is an essential tool for any Blender user looking to take their facial rigs to the next level.
![shapeUp0202](https://user-images.githubusercontent.com/78473045/213843979-d46a5128-f69c-4b7a-be20-881a0268fa92.gif)

Some terminology:
- hero shapes: simple shape keys with no drivers. Examples: jawOpen, lipCornerPuller, browLowerer, eyesClosed
- combination shapes/correctives/combos: shape keys that are driven by 2 or more hero shapes and are used as a corrective difference in deltas. Examples: jawOpen_lipCornerPuller, browLowerer_eyesClosed
- inbetweens/inbetween shapes: shape keys that are driven by a hero shape and act as an inbetween corrective. Examples: jawOpen_10, eyesClosed_50
- inbetween combos: a combination of inbetweens and combos. Examples: jawOpen_10_lipCornerPuller, eyesClosed_25_browLowerer_50
- negative shapes - hero shapes ending with "N", to be at max at -1 value of the hero shape. eyeClosedN, lipFunnelerN
![2023-01-07 20-21-59 2023-01-07 20_22_59](https://user-images.githubusercontent.com/78473045/211139203-a56c54e6-b7f4-4b89-b072-b4e2fa69a3cc.gif)
- mimic: a mesh, typically a head, with shape keys for the expressions.
- FACS: Facial action coding system

TODO:
- c̶l̶e̶a̶n̶ ̶u̶p̶/̶r̶e̶ ̶w̶r̶i̶t̶e̶ ̶c̶o̶d̶e̶ ̶t̶o̶ ̶b̶e̶ ̶m̶o̶r̶e̶ ̶r̶e̶a̶d̶a̶b̶l̶e̶ ̶a̶n̶d̶ ̶o̶r̶g̶a̶n̶i̶z̶e̶d̶ ̶a̶s̶ ̶i̶t̶'̶s̶ ̶b̶e̶c̶o̶m̶i̶n̶g̶ ̶a̶ ̶b̶i̶t̶ ̶m̶e̶s̶s̶y̶:
  -  ̶r̶e̶-̶w̶r̶i̶t̶e̶ ̶s̶h̶a̶p̶e̶ ̶u̶p̶d̶a̶t̶e̶ ̶w̶i̶t̶h̶ ̶n̶e̶w̶ ̶l̶o̶g̶i̶c̶:̶
    - r̶e̶-̶w̶r̶i̶t̶e̶ ̶h̶e̶r̶o̶ ̶u̶p̶d̶a̶t̶e̶
    - r̶e̶-̶w̶r̶i̶t̶e̶ ̶c̶o̶m̶b̶o̶ ̶u̶p̶d̶a̶t̶e̶:
      - r̶e̶m̶e̶d̶y̶ ̶w̶r̶i̶t̶e̶ ̶3̶+̶ ̶c̶o̶m̶b̶o̶ ̶u̶p̶d̶a̶t̶e̶ ̶(̶s̶e̶t̶_̶c̶o̶m̶b̶o̶_̶k̶e̶y̶s̶ ̶f̶u̶n̶c̶t̶i̶o̶n̶ ̶t̶o̶ ̶a̶c̶c̶o̶m̶o̶d̶a̶t̶e̶ ̶f̶o̶r̶ ̶d̶o̶w̶n̶s̶t̶r̶e̶a̶m̶ ̶c̶o̶m̶n̶b̶o̶s̶)̶
    -  ̶r̶e̶-̶w̶r̶i̶t̶e̶ ̶i̶n̶b̶e̶t̶w̶e̶e̶n̶ ̶u̶p̶d̶a̶t̶e̶
  - r̶e̶-̶w̶r̶i̶t̶e̶ ̶s̶h̶a̶p̶e̶ ̶e̶x̶p̶o̶r̶t̶ ̶w̶i̶t̶h̶ ̶n̶e̶w̶ ̶l̶o̶g̶i̶c̶:̶
  
    - -̶ ̶c̶o̶m̶b̶i̶n̶e̶ ̶d̶e̶l̶t̶a̶ ̶d̶i̶f̶f̶e̶r̶e̶n̶c̶e̶s̶ ̶f̶r̶o̶m̶ ̶a̶r̶b̶i̶t̶r̶a̶r̶y̶ ̶n̶u̶m̶b̶e̶r̶ ̶o̶f̶ ̶m̶e̶s̶h̶e̶s̶
    
    - -̶ ̶e̶x̶p̶o̶r̶t̶ ̶t̶o̶ ̶a̶ ̶s̶p̶e̶c̶i̶f̶i̶c̶ ̶f̶o̶l̶d̶e̶r̶
    - c̶o̶m̶b̶i̶n̶e̶ ̶e̶x̶p̶o̶r̶t̶ ̶m̶e̶t̶h̶o̶d̶s̶
  - d̶e̶l̶e̶t̶e̶ ̶u̶n̶n̶e̶c̶e̶s̶s̶a̶r̶y̶ ̶c̶o̶d̶e̶ ̶a̶n̶d̶ ̶r̶e̶-̶f̶a̶c̶t̶o̶r̶ ̶c̶l̶a̶s̶s̶e̶s̶ ̶c̶a̶r̶r̶i̶e̶d̶ ̶o̶v̶e̶r̶
- f̶i̶l̶t̶e̶r̶ ̶t̶h̶e̶ ̶l̶i̶s̶t̶ ̶o̶n̶ ̶t̶h̶e̶ ̶l̶e̶f̶t̶ ̶t̶o̶ ̶o̶n̶l̶y̶ ̶d̶i̶s̶p̶l̶a̶y̶ ̶h̶e̶r̶o̶ ̶s̶h̶a̶p̶e̶s̶,̶ ̶r̶e̶-̶s̶o̶r̶t̶ ̶a̶l̶p̶h̶a̶b̶e̶t̶i̶c̶a̶l̶l̶y̶.̶ ̶A̶l̶t̶e̶r̶n̶a̶t̶i̶v̶e̶l̶y̶ ̶c̶r̶e̶a̶t̶e̶ ̶a̶ ̶f̶i̶l̶t̶e̶r̶e̶d̶ ̶l̶i̶s̶t̶ ̶w̶i̶t̶h̶o̶u̶t̶ ̶v̶a̶l̶u̶e̶s̶,̶ ̶l̶i̶k̶e̶ ̶t̶h̶e̶ ̶o̶n̶e̶ ̶o̶n̶ ̶t̶h̶e̶ ̶r̶i̶g̶h̶t̶ ̶b̶u̶t̶ ̶o̶n̶l̶y̶ ̶w̶i̶t̶h̶ ̶h̶e̶r̶o̶ ̶s̶h̶a̶p̶e̶s̶,̶ ̶a̶n̶d̶ ̶d̶i̶f̶f̶e̶r̶e̶n̶t̶ ̶m̶e̶n̶u̶ ̶w̶i̶t̶h̶ ̶t̶h̶e̶ ̶c̶o̶m̶p̶l̶e̶t̶e̶ ̶l̶i̶s̶t̶ ̶w̶i̶t̶h̶ ̶v̶a̶l̶u̶e̶s̶.̶

![shapeup01](https://user-images.githubusercontent.com/78473045/210918856-be2fe05d-e831-4429-96a8-45ca8ea02e98.gif)

- c̶h̶a̶n̶g̶e̶ ̶u̶p̶d̶a̶t̶e̶ ̶l̶o̶g̶i̶c̶ ̶s̶o̶ ̶t̶h̶a̶t̶ ̶e̶v̶e̶r̶y̶t̶h̶i̶n̶g̶ ̶i̶s̶ ̶b̶a̶s̶e̶d̶ ̶o̶n̶ ̶c̶o̶r̶r̶e̶c̶t̶i̶v̶e̶ ̶d̶e̶l̶t̶a̶s̶
- a̶d̶d̶ ̶e̶n̶u̶m̶ ̶f̶o̶r̶ ̶e̶x̶p̶r̶e̶s̶s̶i̶o̶n̶ ̶s̶e̶l̶e̶c̶t̶i̶o̶n̶

![shapeup_expressions](https://user-images.githubusercontent.com/78473045/211720255-a03fa9a3-76df-4ed1-a3a5-36a281b6443e.gif)

- e̶x̶p̶l̶o̶r̶e̶ ̶q̶u̶i̶c̶k̶s̶e̶t̶ ̶(̶s̶e̶t̶t̶i̶n̶g̶ ̶t̶h̶e̶ ̶s̶e̶l̶e̶c̶t̶e̶d̶ ̶s̶h̶a̶p̶e̶ ̶t̶o̶ ̶1̶ ̶a̶n̶d̶ ̶e̶v̶e̶r̶y̶t̶h̶i̶n̶g̶ ̶e̶l̶s̶e̶ ̶t̶o̶ ̶0̶)̶
- explore other export options, like alembic
- n̶e̶g̶a̶t̶i̶v̶e̶ ̶s̶h̶a̶p̶e̶ ̶u̶p̶d̶a̶t̶e̶
- create a build function that would build a puppet based on selected shapes and their naming
  - while getting a dedicated button, this willl be covered by the new update logic. 
-  ̶e̶x̶p̶l̶o̶r̶e̶ ̶t̶h̶e̶ ̶p̶o̶s̶s̶i̶b̶i̶l̶i̶t̶y̶ ̶o̶f̶ ̶u̶p̶d̶a̶t̶i̶n̶g̶ ̶m̶u̶l̶t̶i̶p̶l̶e̶ ̶s̶h̶a̶p̶e̶s̶ ̶a̶t̶ ̶o̶n̶c̶e̶ ̶b̶a̶s̶e̶d̶ ̶o̶n̶ ̶n̶a̶m̶i̶n̶g̶
- explore by state updates
- explore freezing shapes:
  - basically define back existing upstream shapes (?)
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

-------
Explore live setups for live blendshape connections and live relax - 

![liveBlendshape](https://user-images.githubusercontent.com/78473045/210152813-fe2ffca1-45b8-44f8-ae6c-9140d43881d0.gif)

Blendshapes for animated meshes or shotsculpting - 

![shapekey_abc](https://user-images.githubusercontent.com/78473045/210639444-21e62837-ab66-46d4-a4b4-8f23a030f51d.gif)

Adjustable sticky lips and semi procedural meniscus setups - 

![lipsticky_08](https://github.com/dan283/ShapeUp/assets/78473045/12815b51-1cb8-45bb-8f4a-c08058d7b51b)

![meniscus08](https://github.com/dan283/ShapeUp/assets/78473045/c8adcd08-142e-415d-be61-b58c2debb95e)














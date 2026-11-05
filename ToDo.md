### To Do:
- readability and header/comment pass
- clean up and refactor
- decide:
  - continue along existing path and add a delete left/right edge option for rows and columns mode, OR
  - rework tiling and make columns one single triangle wide (don't work in pairs)
- add border: fill in the jagged edges caused by the rows/columns mode
- more modes:
  - radial: hexagonal shaped grid. Radius determines the size, iterations controls how many rings there are.
  under the hood it's sort of like a scaled and rotated version of the subdivision mode.
  - fill area: define a 2D plane for the tool to fill with a triangular grid in rows/columns mode.
  v1 of this feature will only use planes aligned to world XYZ and won't have scaling or flipping, later versions may align to a plane defined by two selected transforms
    - could possibly activate this mode with a selection check rather than button. If two transforms are selected, can activate fill area mode and define a plane.
    If 4 are selected, automatically activates skewing/warping mode? What if transforms aren't planar? How would the check for that work?
    - flip direction: swaps the alignment of the rows/columns
    - fit modes: (prevents the grid from being skewed/scaled, ensuring equilateral tris -- except for border if filled):
      - fit height (default): grid is scaled to fit the top/bottom to the plane's bounds. Forces equilateral Tris
      - fit width: grid is scaled to fit the left/right edges to the plane's bounds. Forces equilateral Tris
      - fit both: scales both. Will almost certainly prevent tris from being equilateral
      - skew/warp?: essentially a corner pin operation on the grid to match the four transforms. Would still need to work outside of fit both mode
      Might work better as a sort of post-process deformation?
      - for fit height or fit width: could add settings to get the edges closer to those of the actual desired plane:
        - crop (bool): if faces extend beyond the plane, then remove offending faces. May require a setting for padding or
        only keeping faces fully inside the boundary
        - fill gaps (bool): if there is a gap in the lesser priority direction, extrude the edges to fill it
          - For future me: is this redundant/necessary/should it be a part of the border feature?
          Is there a case that can't be easily solved by extruding/bridging the edges that fall short? How much time would the user save and how much complexity would be added?
          Is it worth folding this into the border? they mey end up being functionally different operations.
          It wouldn't make sense to have a fill without a border, but what about a border without a fill (flat edges for whole perimiter, but gaps on either sides)?

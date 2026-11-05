# TriGrid
A modelling tool in maya that creates a flat grid of equilateral triangles.

<details>
<summary><b>Setup</b></summary>
  
- Download and unzip the script at a location of your choosing
- Open the text file in a text editor (ex. Notepad++) 
- Open Maya's script editor and create a new MEL tab
- Select all of the text in the text editor and copy/paste it into the new MEL tab
- Optional: Add it as a shelf button for reuse (recommended)
  - Follow these instructions from Autodesk: https://download.autodesk.com/global/docs/maya2014/en_us/index.html?url=files/Running_MEL_Make_a_shelf_button_for_a_script.htm,topicNumber=d30e789357

Alternatively, the script can be run by pressing numpad enter. Select all text in the script first to keep it from disappearing from the script editor.
</details>

### How to Use
- run the script
- Choose one of the modes:
  - Subdivision: each edge of a triangle is split with its verts connected, forming 4 more triangles (triforce style). End result is a triangular shaped grid.
  - Rows and columns: Rows of adjacent, connected triangles are laid out in the x axis as their tips point along z axis in alternating directions. Rows are 1 triangle tall.
    Columns will stack these rows in the z axis and their width is measured in pairs of triangles (one up, one down) for tiling. End result approximates a square shape.
- Set the iterations depending on the mode:
  - Subdivision: one iteration = one subdivision
  - Rows and columns:
    - Horizontal iteration = add one pair of triangles on the X axis
    - Vertical iteration = create one row with the above width

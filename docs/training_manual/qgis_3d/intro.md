# Lesson: Introduction to QGIS 3D

We will first discover QGIS and its 3D capabilities.

We will :
- Load buildings, roads and trees (2D)
- Load an orthophoto raster layer
- Configure the 3D symbology of these views
- Open a new 3D view to visualize these layers
 - learn 3D navigation with mouse and keyboard
 - learn the different 3D tools
 - see how to configure a 3D view finely
- Load a DEM file and use it in the 3D view
- Create an animation in QGIS 3D
- Make advanced 3D symbology
 - Set of rules
 - Displaying a 3D model for points
- Show 3D objects (Vertical 3D lines)


## Step 1: Loading data

The data is located in the `~/grenoble/data/` folder, and the projects are located in `~/grenoble/qgis/`.

- Open QGIS
- Start a new QGIS project
- Change the project projection to EPSG:2154
- Find the data directory in the navigation panel and add it to favorites
- Open the OpenStreeMap data geopackage
- Load orthophoto

Corresponding project: `grenoble_1.qgs`


## Step 2: 3D View

- Open a new 3D view: View -> 3D View -> New 3D Map View
- Navigate in the 3D view
 - Left mouse click and drag
 - Mouse wheel
 - Right mouse click and drag
 - Ctrl-mouse and move
 - Mouse-shift and move
 - directional keys
- Discovery of basic 3D tools
 - Camera control
 - Full zoom
 - Toggle on-screen navigation
 - Identify
 - Measuring Line
 - Save as image
 - Export 3D scene
- Options and configuration: Options -> Configure
 - General: Change the extent of the 3D view
 - Camera: change perspective
 - 3D axis and navigation synchronization
 - Ground
 - Flat land: no elevation
 - DEM (raster layer): used later
 - Online (not working)
 - Mesh (not used during the workshop)
 - Light to configure scene lighting
 - Advanced: options mainly useful for debugging a scene: changing resolutions and observing the change
 - Post-processing effects:
 - Shadows
 - Eye-Dome Lighting
 - Ambient occlusion

Load the `mnt.tif` raster and use it as a terrain model in the 3D view:
- open the raster
- Open 3D view configuration
- Choose the terrain type “MNT” and choose the “mnt” layer
- Disable the "DEM" layer so that it no longer appears in the 3D view
- Change the vertical scale and observe the result

Corresponding project: `grenoble_2.qgs`

![](https://pad.oslandia.net/uploads/6122e017-511d-4889-8404-17dcb67c14c2.png)


## Step 3: Basic 3D Symbology

We will configure the rendering mode for buildings, trees and roads.

- Open the properties of the buildings layer
- Select 3D symbology (cube symbol)
- Select “single symbol”
- Set an extrusion to 10
- Check that the altitude restriction is set to "Terrain"
- Start a 3D view
- Change “Diffuse” and “Ambience” colors
- Observe the impact on the appearance of buildings
- Add “Borders”, change color and width
- Change the extrusion using an expression (use the "buildings:levels" attribute)

Also change the symbology of trees and roads. Try to represent trees by combining a cylinder representation for the trunk and a cone representation for the leaves

Corresponding project: `grenoble_3.qgs`

![](https://pad.oslandia.net/uploads/e482a1e2-de69-4472-97a2-b72035000339.png)


## Step 4: Advanced 3D Symbology

We will now use a "Ruleset" symbology for buildings and display the trees using a 3D model.

- For the buildings layer, change the 3D symbology such as:
 - the garages are 4 meters high
 - The flats are extruded in red
 - The houses are extruded in yellow
 - All other buildings are extruded in gray

- Also use a “Set of rules” symbology for trees:
 - Represent “genre_bota” type trees with the 3d object `arbre.obj`
 - Represent the other trees with cylinders

- Imagine advanced symbologies for roads

Corresponding project: `grenoble_4.qgs`

![](https://pad.oslandia.net/uploads/efc81742-bc76-4725-8e34-3620aae4b060.png)


## Step 5: Relative, absolute and terrain altitude restriction

Load the 3D lines file `lignes3D.gpkg`

- Vary the altitude restriction between "Relative", "Absolute" and "Terrain". Observe the difference
- Also vary the height parameter

![](https://pad.oslandia.net/uploads/0132015d-bc24-46ec-af94-2715d2efafac.png)

Corresponding project: `grenoble_5.qgs`


## Step 6: Animation

- Enable "Animations" in 3D view
- Select the 0s keyframe
- Move the 3D view to where you want to start
- Add a keyframe at 5s 
- Move the 3D view to where you want it to stop
- Click on start
- Export
 - choose a low frame rate
 - this generates images which can be merged to make a movie with a tool such as ffmpeg
- Change the interpolation method
- Add other keyframes

Corresponding project: `grenoble_6.qgs`


## What's Next?

Now that we've looked at how databases work in theory, let's create a new
database to implement the theory we've covered.


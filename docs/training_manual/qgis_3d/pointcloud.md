# Lesson: Pointcloud data

We will :
- Load point cloud data
- Study symbology and properties
- Display point clouds in 3D
- Use processing tools to carry out processing on point clouds

## Step 0: Presentation of the different Point Cloud processing

They are based on `PDAL wrench` and available since QGIS 3.32

![](https://pad.oslandia.net/uploads/fc5765dd-42ea-41dc-a393-18a5309a1589.png)


## Step 1: Loading data

- Start a new QGIS project
- Change the project projection to EPSG:2154
- Load the point cloud `pointcloud/merged.copc.laz`
- Look at the different statistics of the point cloud: right click on the layer: properties -> statistics
- Modify the 2D symbology in "Classification" then "Attribute by ramp" "Intensity" or "Z"
- Try to activate the "Shading Renderer" for 2D symbology
- Filter the point cloud to only display buildings: right click on the "Filter..." layer
- Show the point cloud in a 3D view

If the point cloud is too large to load, it is possible to load a smaller point cloud in the `pointcloud` directory

Corresponding project: `pointcloud_1.qgs`

![](https://pad.oslandia.net/uploads/3818c119-60dd-433a-8165-b6f359b83fde.png)

## Step 2: Extract parts of a point cloud

- Filter the point cloud to only display buildings
- Open the “Buildings” layer of `osm.gpkg`
- Select the 3 towers of Grenoble located “Boulevard du Maréchal Leclerc” (it is possible to use the “French Locator Filter” plugin to find the address)
- Create a new layer in memory from the selection
- Start the “Point cloud extraction” processing -> “Limit”
 - Source layer: “merged”
 - cutting polygon: select the selection layer
 - limit “cropping extent” so that processing does not take too long

Other “remarkable” buildings to extract: the Stade des Alpes, the Perret Tower in Paul-Mistral Park.
Along the same lines, it is possible to extract elements of vegetation, soil, etc.

Corresponding project: `pointcloud_2.qgs`

![](https://pad.oslandia.net/uploads/83c27576-ae11-4096-8808-a1d8294f98b0.png)

## Step 3: Extract the average building size

- Load building data from OpenStreetMap
- Extract the Z value from the point cloud with “Export to raster”
- Assign the Z value to OpenStreetMap buildings:
 - Cut out the buildings layer to keep only the buildings inside the “merged” point cloud (Extract/cut by extent)
 - convert raster Z to points (raster pixel to points)
 - add a spatial index to the point layer
 - remove the minimum Z to have the size of the buildings without the altitude (“refactor the fields”)
 - assign the Z value to each building (join the attributes by location and select (one by one))

Corresponding project: `pointcloud_3.qgs`

## Step 4: 3D view combining OSM data and extracted point clouds

- From the existing project, open the datasets used in the first part:
 - orthophoto
 - the mnt
 - OpenStreetMap data
- configure the symbologies. Use the new Z attribute for building extrusion
- Create a new 3d view

Corresponding project: `pointcloud_4.qgs`


![](https://pad.oslandia.net/uploads/d59e19a3-ae60-4f96-b1c5-0b40db59ffc3.png)

## Elevation profiles

## Step 1: Point cloud profile

- Open a new QGIS project
- Load the point cloud `merged.copc.laz`
- Load the MNT `mnt.tif`
- Launch the profile elevation tool: View -> Elevation profiles
- Draw a capture curve that passes through the point cloud
- Change the tolerance setting in the options and observe the difference
- Play with the elevation options in the point cloud properties
- Draw a capture curve that follows the Isère and gradually increase the tolerance to see vegetation and buildings appear

Corresponding project: `profil_elevation_1.qgs`

![](https://pad.oslandia.net/uploads/1bbe5386-04b1-476e-b7aa-e9db27c518cb.png)


## Step 2: Adding 2D data

- Load OpenStreetMap data
- Add buildings to profile elevation: What is happening?
 - To resolve the problem, you must configure the terrain in the global properties of the project
- Edit building elevation properties to add extrustion

    Corresponding project: `profile_elevation_2.qgs`

![](https://pad.oslandia.net/uploads/d8957778-2a12-4f78-a2d9-fdc7f7ad62fe.png)


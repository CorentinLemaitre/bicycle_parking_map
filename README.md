# bicycle_parking_map
Static map to show bicycle parking spot around a specific place

## Context

The goal of this repository is to help produce a map of the bicycle parking to access a specific place. The use case is the [Salle Paul Fort](https://www.openstreetmap.org/node/4484128529) in Nantes. The map is made to be shown in the nearest bicyle parking spot and help people to find one free nearby. 

The map is based on **OpenStreetMap** data and made to be updated easily. Please contribute to OpenStreetMap if bicycle parking are created or modified. [Here you can find the documentation to do it](https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dbicycle_parking).

To use this repository you need the software QGIS.

# Step by step 

## Download bicycle_parking.geojson

The localisation of bicycle parking will be extracted from OpenStreetMap data. The tool Overpass turbo help you to do this. Use a web browser to go to [overpass-turbo](https://overpass-turbo.eu/s/1cRd), then zoom in the place where you want to map bicycle parking. 

Add this overpass querry in the dialog and execute it. 

```
[out:xml] [timeout:25];
(
    node["amenity"="bicycle_parking"](around:1000, {{center}});
    way["amenity"="bicycle_parking"](around:1000, {{center}});
    relation["amenity"="bicycle_parking"](around:1000, {{center}});
);
out center;
```

Save the result as `bicycle_parking.geojson` to replace the old file.


# Calculating areas in QGIS

If you have some shapefiles and you want to calculate the coverage area of them, here are a few steps to get a rough estimate.

One caveat is that your data needs to be in the proper map units for which you want the area value. So if you're looking for meters, you'll need to have your data in a meter-based coordinate system (like [UTM](http://en.wikipedia.org/wiki/Universal_Transverse_Mercator_coordinate_system)), or if you want square feet or miles, you need something in feet (possibly [state plane](http://en.wikipedia.org/wiki/State_plane), or the like).

## Create convex hull

1. Select **Vector > Geoprocessing Tools > Convex hull**.
2. Select the layer you want a convex hull outline generated from, choose "single minimum convex hull", and set the output shapefile.

## Calculate an area column

1. Open the attribute table of your convex hull polygon layer.
2. Go into Edit mode and open the **Field Calculator** (`Cmd-I` or `Ctrl-I`)
3. Select "Create a new field" called "area" with type "whole number" and a width large enough to accommodate your rough area size.
4. Expand the "Geometry" functions and double-click `$area`, then click OK to run the calculations.

You now have a column with your boundary's area in map units. If your data is in meters, divide the square meter area by 1,000,000 to get the area in sq km. If the result is feet and you want square miles, divide the result by 27,878,372 (5280 squared).
# GDAL 

http://www.gdal.org/ogr2ogr.html

## Installation
The easiest way to use GDAL is to use the GDAL that is packaged with QGIS.

## examples

### GKPG -> PostgreSQL

```
"D:\apps\QGIS 2.18\bin\ogr2ogr.exe" -f PostgreSQL "PG:dbname=pdok host=[host] port=[port] user=[username] password=[passwrd] SCHEMAS=policestations" policestations.gpkg
```

### Shape -> GKPG

```
"D:\apps\QGIS 2.18\bin\ogr2ogr.exe" -f GPKG policestations.gpkg policestations.shp
```
The *.gpkg file shouldn't be in the directory were the command is executed. The file will be made through GDAL.

### PostgreSQL -> GPKG

```
"D:\apps\QGIS 2.18\bin\ogr2ogr.exe" -f GPKG policestations.gpkg "PG:dbname=pdok host=[host] port=[port] user=[username] password=[passwrd] SCHEMAS=policestations"
```
The *.gpkg file shouldn't be in the directory were the command is executed. The file will be made through GDAL.

### Shape -> PostgreSQL

```
"D:\apps\QGIS 2.18\bin\ogr2ogr.exe" -f PostgreSQL "PG:dbname=pdok host=[host] port=[port] user=[username] password=[passwrd] SCHEMAS=policestations" -mapFieldType All=String -nlt PROMOTE_TO_MULTI  policestations.shp
```
|parameter| |
|-|-|
|-mapFieldType All=String|write all the data as a STRING to the database|
|-nlt PROMOTE_TO_MULTI|Update every geometry to a MULTI-variant (POINT -> MULITPOINT, LINE -> MULTILINE, enz.)|
```
"D:\apps\QGIS 2.18\bin\ogr2ogr.exe" -f PostgreSQL "PG:dbname=pdok host=[host] port=[port] user=[username] password=[passwrd] SCHEMAS=policestations" -sql "SELECT naam, bordertype from policestations" -a_srs EPSG:28992 -mapFieldType All=String policestations.shp
```
|parameter| |
|-|-|
|-sql "SELECT naam AS name, bordertype from policestations"|makes it possible to rename columns|
|-a_srs EPSG:28992|'forces' the projection of a geometry|

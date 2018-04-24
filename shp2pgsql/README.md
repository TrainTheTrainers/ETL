# How to
How to load data from shape file into postgres database 

```
shp2pgsql -s 4326 -I policiskistanici.shp polickiskistanicishema.policiskistanicitablea > dr_policiskistanici.sql

```
```
psql -f policiskistanici.sql -h [localhost] -d [sampledatabase] -U postgres
```

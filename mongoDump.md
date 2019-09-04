# MongoDB dump and restore

## MongoDB dump
- ```mongodump --db DBName ```
    To take full db dump

- ```mongodump --db dbName --collection collectionName```
    To take a particular collection dump

## MongoDB restore of a full DB
- ```mongorestore --db DBNameInTheStorage /location/of/dbFolder```
    Restore whole db to the specified dbName

- ```mongorestore --db dbName --collection collectionName /location/to/json/file```
    Restore a particular collection only

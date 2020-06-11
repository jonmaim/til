# Loop through all databases

Copy/paste this code into the mongo shell to apply operation on each database.

```javascript
db = db.getSiblingDB("admin");
dbs = db.runCommand({ "listDatabases": 1 }).databases;

dbs.forEach(function(database) {
  d = db.getSiblingDB(database.name);
  /* do something */
  cals = db.calendars.find();
  print(database.name + ' ' + cals.length);
});
```

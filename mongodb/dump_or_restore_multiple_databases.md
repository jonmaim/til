# Dump or restore multiple databases

## Dump

```bash
for i in db1 db2 db3 ;
  do
    echo $i;
    mongodump -v -h localhost -d $i -o dump;
  done
tar cfvz dump.tar.gz dump;
```

## Restore

```bash
tar xvfz dump.tar.gz;
for i in db1 db2 db3 ;
  do
    echo $i;
    mongorestore -h localhost -d $i --drop --objcheck dump/$i/
  done
```

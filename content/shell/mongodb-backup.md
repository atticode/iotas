+++
title = "Mongodb 备份 shell"
date = 2020-12-13T13:47:56+08:00
isCJKLanguage = true
description = ""
tags = ["shell", "mongodb"]
categories = []
weight = 10
+++

## Mongodb 导出 collection

```shell
#!/bin/sh

#datetime=$(date +%Y%m%d_%H%M%S)
datetime=$(date +%Y%m%d)

echo $date

mkdir ~/backup/mongo/backup-$datetime

cd ~/backup/mongo/backup-$datetime

/usr/local/mongodb/bin/mongoexport --username=dev --password=dev --host="localhost:27017" --db=demo --collection=user --out=user.json
/usr/local/mongodb/bin/mongoexport --username=dev --password=dev --host="localhost:27017" --db=demo --collection=test --out=test.json
/usr/local/mongodb/bin/mongoexport --username=dev --password=dev --host="localhost:27017" --db=demo --collection=demo --out=demo.json

cd ..

zip -q -r backup-$datetime.zip backup-$datetime

rm -rf backup-$datetime
```

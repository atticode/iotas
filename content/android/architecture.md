+++
title = "Android Architecture"
date = 2020-12-12T13:47:30+08:00
isCJKLanguage = true
description = ""
tags = ["android"]
categories = []
weight = 10
+++

### 1.MVP Architecture
```txt

./
|-- app
|   |-- src
|   |   |-- androidTest
|   |   |-- main
|   |   |   |-- assets
|   |   |   |   |-- css
|   |   |   |   |-- image
|   |   |   |   |-- js
|   |   |   |-- java
|   |   |   |   |-- com
|   |   |   |   |   |-- demo
|   |   |   |   |   |   |-- example
|   |   |   |   |   |   |   |-- user
|   |   |   |   |   |   |   |   |-- User.java
|   |   |   |   |   |   |   |   |-- UserActivity.java
|   |   |   |   |   |   |   |   |-- UserContract.java
|   |   |   |   |   |   |   |   |-- UserDataSource.java
|   |   |   |   |   |   |   |   |-- UserFragment.java
|   |   |   |   |   |   |   |   |-- UserLocalDataSource.java
|   |   |   |   |   |   |   |   |-- UserPresenter.java
|   |   |   |   |   |   |   |   |-- UserRemoteDataSource.java
|   |   |   |   |   |   |   |   |-- UserRepository.java
|   |   |   |-- res
|   |   |   |-- AndroidManifest.xml
|   |   |-- test
|-- gradle
|   |-- wrapper

```

### 3. Android Application FLow
![android flow](/image/android-application-flow-graph.png)


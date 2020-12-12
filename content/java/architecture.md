+++
title = "Java Architecture"
date = 2020-12-12T13:47:56+08:00
isCJKLanguage = true
description = ""
tags = []
categories = []
weight = 10
+++


## Spring Boot
### 1. Architecture
``` txt
./
|-- src
|   |-- main
|   |   |-- java
|   |   |   |-- com
|   |   |   |   |-- demo
|   |   |   |   |   |-- example
|   |   |   |   |   |   |-- Application.java
|   |   |   |   |   |   |-- user
|   |   |   |   |   |   |   |-- User.java
|   |   |   |   |   |   |   |-- UserController.java
|   |   |   |   |   |   |   |-- UserService.java
|   |   |   |   |   |   |   |-- UserRepository.java
|   |   |-- resources
|   |   |   |-- application.properties
|   |-- test
|-- pom.xml

```


## Maven
### 1. Architecture
``` txt
|-- pom.xml
`-- src
    |-- main
    |   |-- java
    |   |   `-- com
    |   |       `-- mycompany
    |   |           `-- app
    |   |               `-- App.java
    |   `-- resources
    |       `-- META-INF
    |           |-- application.properties
    `-- test
        |-- java
        |   `-- com
        |       `-- mycompany
        |           `-- app
        |               `-- AppTest.java
        `-- resources
            `-- test.properties
```

### 2.Reference
[Maven Get Start](https://maven.apache.org/guides/getting-started/index.html)

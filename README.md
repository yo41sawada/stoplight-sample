# ABOUT THIS REPOSITORY
Stoplight や OpenAPI Generator を確認・検証するためのリポジトリです。

## 完成形の構成例
```
.
├── README.md
├── config.yaml
├── openapi.yaml
└── out
  └── java
    ├── README.md
    ├── pom.xml
    ├── src
    │  ├── main
    │  │  ├── java
    │  │  │  └── org
    │  │  │    └── openapitools
    │  │  │      ├── OpenApiGeneratorApplication.java
    │  │  │      ├── RFC3339DateFormat.java
    │  │  │      ├── api
    │  │  │      │  ├── ApiUtil.java
    │  │  │      │  ├── UsersApi.java
    │  │  │      │  └── UsersApiController.java
    │  │  │      ├── configuration
    │  │  │      │  └── HomeController.java
    │  │  │      └── model
    │  │  │        └── User.java
    │  │  └── resources
    │  │    ├── application.properties
    │  │    └── openapi.yaml
    │  └── test
    │    └── java
    │      └── org
    │        └── openapitools
    │          └── OpenApiGeneratorApplicationTests.java
    └── target
      ├── classes
      │  ├── application.properties
      │  ├── openapi.yaml
      │  └── org
      │    └── openapitools
      │      ├── OpenApiGeneratorApplication.class
      │      ├── RFC3339DateFormat.class
      │      ├── api
      │      │  ├── ApiUtil.class
      │      │  ├── UsersApi.class
      │      │  └── UsersApiController.class
      │      ├── configuration
      │      │  └── HomeController.class
      │      └── model
      │        └── User.class
      ├── generated-sources
      │  └── annotations
      ├── generated-test-sources
      │  └── test-annotations
      ├── maven-archiver
      │  └── pom.properties
      ├── maven-status
      │  └── maven-compiler-plugin
      │    ├── compile
      │    │  └── default-compile
      │    │    ├── createdFiles.lst
      │    │    └── inputFiles.lst
      │    └── testCompile
      │      └── default-testCompile
      │        ├── createdFiles.lst
      │        └── inputFiles.lst
      ├── openapi-spring-1.0.jar
      ├── openapi-spring-1.0.jar.original
      ├── surefire-reports
      │  ├── TEST-org.openapitools.OpenApiGeneratorApplicationTests.xml
      │  └── org.openapitools.OpenApiGeneratorApplicationTests.txt
      └── test-classes
        └── org
          └── openapitools
            └── OpenApiGeneratorApplicationTests.class
```

# 準備
## インストール
- Git
- Docker
- Java
- Maven

## 本リポジトリのクローン
リポジトリをクローンし、OpenAPI 定義ファイルがあることを確認します。
```
git clone https://github.com/yo41sawada/stoplight-sample.git
```

## Docker
Docker イメージを準備します。
```
docker pull openapitools/openapi-generator-cli
```

# 実行
## 自動生成
```
docker run --rm -v "${PWD}:/local" openapitools/openapi-generator-cli generate \
  -i /local/openapi.yaml \
  -g spring \
  -o /local/out/java \
  -c /local/config.yaml
```

## Maven ビルド
```
cd ./out/java
mvn clean package
```

## Spring アプリケーション起動
```
java -jar ./out/java/target/openapi-spring-1.0.jar
```

## アクセス
- [http://localhost:3000/](http://localhost:3000/)
- [http://localhost:3000/users](http://localhost:3000/users)

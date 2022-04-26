# ABOUT THIS REPOSITORY
Stoplight や OpenAPI Generator を確認・検証するためのリポジトリです。

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
  -o /local/out/java
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
- [http://localhost:3000/](http://localhost:3000/){:target="_blank"}
- [http://localhost:3000/users](http://localhost:3000/users){:target="_blank"}

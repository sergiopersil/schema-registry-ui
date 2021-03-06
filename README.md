# schema-registry-ui

[![release](http://github-release-version.herokuapp.com/github/landoop/schema-registry-ui/release.svg?style=flat)](https://github.com/landoop/schema-registry-ui/releases/latest)
[![docker](https://img.shields.io/docker/pulls/landoop/schema-registry-ui.svg?style=flat)](https://hub.docker.com/r/landoop/schema-registry-ui/)
[![Join the chat at https://gitter.im/Landoop/support](https://img.shields.io/gitter/room/nwjs/nw.js.svg?maxAge=2592000)](https://gitter.im/Landoop/support?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This is a web tool for the [confluentinc/schema-registry](https://github.com/confluentinc/schema-registry) in order to create / view / search / evolve / view history & configure **Avro** schemas of your Kafka cluster.

## Live Demo
[schema-registry-ui.landoop.com](http://schema-registry-ui.landoop.com)

## Prerequisites
You will need schema-registry installed with CORS enabled.

In order to enable CORS, add in `/opt/confluent-3.x.x/etc/schema-registry/schema-registry.properties`

```
access.control.allow.methods=GET,POST,OPTIONS
access.control.allow.origin=*
```
And then restart the [schema-registry] service

##### Get the set up locally
We also provide the schema-registry and schema-registry-ui as part of the [fast-data-dev](https://github.com/Landoop/fast-data-dev) docker image for local development setup that also gives all the relevant backends. Just run:
```
docker run -d --name=fast-data-dev -p 8081:8081 landoop/fast-data-dev
```
Checkout more about fast-data-dev docker container [here](https://github.com/Landoop/fast-data-dev)

## Running it

```
    docker pull landoop/schema-registry-ui
    docker run --rm -it -p 8000:8000 \
               -e "SCHEMAREGISTRY_URL=http://confluent-schema-registry-host:port" \
               landoop/schema-registry-ui
```

## Build from source

```
    git clone https://github.com/Landoop/schema-registry-ui.git
    cd schema-registry-ui
    npm install
    http-server .
```
Web UI will be available at `http://localhost:8080`

### Nginx config

If you use `nginx` to serve this ui, let angular manage routing with
```
    location / {
        try_files $uri $uri/ /index.html =404;
        root /folder-with-schema-registry-ui/;
    }
```

### Setup Kafka Rest clusters

Use multiple Kafka Rest clusters in `env.js` :
```
var clusters = [
   {
       NAME:"prod",
       // Schema Registry service URL (i.e. http://localhost:8081)
       SCHEMA_REGISTRY: "http://localhost:8081",
       COLOR: "#141414" // optional
     },
     {
       NAME:"dev",
       SCHEMA_REGISTRY: "http://localhost:8383",
       COLOR: "red" // optional
     }
  ];

```
* Use `COLOR` to set different header colors for each set up cluster.

## Changelog
[Here](https://github.com/Landoop/schema-registry-ui/wiki/Changelog)

## License

The project is licensed under the [BSL](http://www.landoop.com/bsl) license.

## Relevant Projects

* [kafka-topics-ui](https://github.com/Landoop/kafka-topics-ui), UI to browse Kafka data and work with Kafka Topics
* [kafka-connect-ui](https://github.com/Landoop/kafka-connect-ui), Set up and manage connectors for multiple connect clusters
* [fast-data-dev](https://github.com/Landoop/fast-data-dev), Docker for Kafka developers (schema-registry,kafka-rest,zoo,brokers,landoop)
* [Landoop-On-Cloudera](https://github.com/Landoop/Landoop-On-Cloudera), Install and manage your kafka streaming-platform on you Cloudera CDH cluster



<img src="http://www.landoop.com/images/landoop-dark.svg" width="13" /> www.landoop.com

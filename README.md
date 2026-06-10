# docker-clickhouse

🚨🚧 THIS IS A TESTING REPOSITORY TO BE USED LOCALLY ONLY 🚧🚨

Explore how to use the [ClickHouse](https://clickhouse.com/) on a Docker Container

- [[GitHub] ClickHouse/ClickHouse](https://github.com/ClickHouse/ClickHouse)

- [ClickHouse Docs](https://clickhouse.com/docs)
  - [Data modelling overview | ClickHouse Docs](https://clickhouse.com/docs/data-modeling/overview)

  - [Tutorials and example datasets | CLickHouse Docs](https://clickhouse.com:2053/docs/getting-started/example-datasets)

  - [ClickHouse SQL Reference | ClickHouse Docs](https://clickhouse.com/docs/sql-reference)

- [SQL Playground by ClickHouse](https://sql.clickhouse.com/)
  - [[GitHub] ClickHouse/sql.clickhouse.com](https://github.com/ClickHouse/sql.clickhouse.com)

## Commands

### Docker Container

- [clickhouse - Official Image | Docker Hub](https://hub.docker.com/_/clickhouse/)
  - [Install ClickHouse using Docker | ClickHouse Docs](https://clickhouse.com/docs/install/docker)
    - [Configuration](https://clickhouse.com/docs/install/docker#configuration)

1\. Pull the ClickHouse Docker Image

```sh
docker pull clickhouse/clickhouse-server:26.2-alpine
```

2\. Run a ClickHouse Container

```sh
docker run -d \
  --name test-clickhouse-container \
  -e CLICKHOUSE_USER=admin \
  -e CLICKHOUSE_PASSWORD=secret \
  -e CLICKHOUSE_DB=test \
  --ulimit nofile=262144:262144 \
  -p 8123:8123 \
  -p 8443:8443 \
  -p 9000:9000 \
  clickhouse/clickhouse-server:26.2-alpine
```

with Volume

```sh
docker run -d \
  --name test-clickhouse-container \
  -e CLICKHOUSE_USER=admin \
  -e CLICKHOUSE_PASSWORD=secret \
  -e CLICKHOUSE_DB=test \
  --ulimit nofile=262144:262144 \
  -p 8123:8123 \
  -p 8443:8443 \
  -p 9000:9000 \
  -v clickhouse_data:/var/lib/clickhouse/ \
  -v clickhouse_logs:/var/log/clickhouse-server/ \
  clickhouse/clickhouse-server:26.2-alpine
```

check the Docker volumes ( [doc ref](https://docs.docker.com/reference/cli/docker/volume/ls/) )

```sh
docker volume ls
```

check the disk used by Docker ( [doc ref](https://docs.docker.com/reference/cli/docker/system/df/) )

```sh
docker system df
```

3\. Connect to ClickHouse

```sh
docker exec -it test-clickhouse-container clickhouse-client
```

[Web user interface](https://clickhouse.com/docs/interfaces/http#web-ui): `http://localhost:8123/play`

Test query

```sql
SELECT 'Hello, ClickHouse!'

SELECT version()
```

- [ClickHouse OSS quick start | ClickHouse Docs](https://clickhouse.com/docs/getting-started/quick-start/oss)

4\. Stop Container

```sh
docker stop test-clickhouse-container
```

5\. Remove Container

```sh
docker rm -f test-clickhouse-container
```

## Useful references

- [Docker](https://www.docker.com/)
  - [Use Docker Compose | Docker Docs](https://docs.docker.com/get-started/workshop/08_using_compose/)

  - [Docker Compose | GeeksforGeeks](https://www.geeksforgeeks.org/devops/docker-compose/)

  - [Docker Compose Cheatsheet — Most useful commands with examples | by Rost Glukhov - Medium](https://medium.com/@rosgluk/docker-compose-cheatsheet-most-useful-commands-with-examples-4fbc3d2b5deb)

- [JS client | ClickHouse Docs](https://clickhouse.com/docs/integrations/javascript)
  - [[GitHub] ClickHouse/clickhouse-js](https://github.com/ClickHouse/clickhouse-js)

- [ClickHouse Cheat Sheet | CheatDocs](https://cheatdocs.org/clickhouse/)

- [Top 10 best practices tips for ClickHouse | ClickHouse Blog](https://clickhouse.com/blog/10-best-practice-tips)

- [ClickHouse: 5 Practical Examples for Data Analytics | devbyte.space](https://www.devbyte.space/clickhouse-top-5-practical-examples-for-beginers/)

### Materialized views

- [Materialized views | ClickHouse Docs](https://clickhouse.com/docs/materialized-views)

- [What Is a Materialized View and How It Works in ClickHouse | OneUptime Blog](https://oneuptime.com/blog/post/2026-03-31-clickhouse-what-is-a-materialized-view/view)

- [A Guide to Materialized Views in ClickHouse | hypequery](https://hypequery.com/blog/a-guide-to-materialized-views-in-clickhouse)

- [Materialized Views in ClickHouse: Benefits, Limitations, and Alternatives | GlassFlow](https://www.glassflow.dev/blog/clickhouse-materialized-views)

- [Dominate Your Analytics with Materialized Views in ClickHouse | ChistaDATA Inc.](https://chistadata.com/materialized-views-in-clickhouse-2/)

### Tutorial

- [ClickHouse OSS quick start | ClickHouse Docs](https://clickhouse.com/docs/getting-started/quick-start/oss)

- [Advanced tutorial | ClickHouse Docs](https://clickhouse.com/docs/tutorial)

- [ClickHouse Basic Tutorial: An Introduction | Dev.to](https://dev.to/hoptical/clickhouse-basic-tutorial-an-introduction-52il)

- [Beginner’s Guide to ClickHouse: Introduction, Features, and Getting Started | by Suffyan Asad - Medium](https://medium.com/@suffyan.asad1/beginners-guide-to-clickhouse-introduction-features-and-getting-started-55315107399a)

- [2 ClickHouse tutorials: Quick start and large-scale data analysis | Instaclustr](https://www.instaclustr.com/education/clickhouse/2-clickhouse-tutorials-quick-start-and-large-scale-data-analysis/)

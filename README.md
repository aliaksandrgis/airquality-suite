# AirQuality Suite

Air quality data platform built as a set of microservices: producer, streaming, API, and web client.

Demo: https://air.naviodev.com

Data flow: Producer → Kafka (Confluent Cloud) → Spark → Supabase → Geo API → Web client

## Screenshots
![Dashboard 1](imgs/1.png)
![Dashboard 2](imgs/2.png)
![Dashboard 3](imgs/3.png)
![Dashboard 4](imgs/4.png)

## Repositories
- airquality-data-pipeline: https://github.com/aliaksandrgis/airquality-data-pipeline
  Kafka producer that pulls live measurements and station catalogs from DE/NL/PL and publishes raw events.
- airquality-spark-jobs: https://github.com/aliaksandrgis/airquality-spark-jobs
  Spark Structured Streaming job that consumes Kafka, writes bronze parquet, and upserts curated rows to Supabase.
- airquality-airflow-dags: https://github.com/aliaksandrgis/airquality-airflow-dags
  Airflow schedules one-shot ingestion tasks and daily housekeeping (log cleanup, retention, pruning).
- airquality-geo-api: https://github.com/aliaksandrgis/airquality-geo-api
  FastAPI service that exposes measurements and stations from Supabase/Postgres.
- airquality-web-client: https://github.com/aliaksandrgis/airquality-web-client
  Static web UI that renders charts and maps for the public demo.

## Data sources
- Germany: UBA API
- Netherlands: Luchtmeetnet API
- Poland: GIOS API

## Stack
Airflow, Kafka (Confluent Cloud), Spark, Supabase (Postgres), FastAPI, static web UI.

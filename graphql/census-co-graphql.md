# Census GraphQL Schema

## Overview

This conceptual GraphQL schema represents the Census (Fivetran Activations) reverse ETL and data activation platform. Census enables engineering and data teams to synchronize modeled warehouse data into more than 200 SaaS destinations through managed reverse ETL pipelines, audience segmentation, and embedded activation products.

The schema covers the full surface area of the Census Management API and Embedded API, including sync lifecycle management, source and destination provisioning, dataset and model management, field mapping, observability, and credential management.

## Schema Source

- **Provider:** Census (Fivetran Activations)
- **API Reference:** https://fivetran.com/docs/activations/rest-api
- **Developer Documentation:** https://developers.getcensus.com/
- **Base URL:** https://app.getcensus.com/api

## Authentication

Census uses workspace-scoped API keys issued from the Census or Fivetran Activations dashboard. All API key values are passed as Bearer tokens in the Authorization header.

## Core Concepts

### Syncs

A Sync is the primary unit of Census — it defines a pipeline from a source model in the data warehouse to an object in a SaaS destination. Syncs have a trigger schedule, a behavior (upsert, mirror, append), field mappings, and produce SyncRuns each time they execute.

### Sources and Models

A DataSource represents a connected warehouse (Snowflake, BigQuery, Databricks, Redshift, Postgres). Within a source, teams define SourceModels — SQL queries, dbt models, or Looker Looks — that produce the dataset to be synced.

### Destinations

A Destination represents a connected SaaS tool (Salesforce, HubSpot, Marketo, Braze, etc.). Each destination exposes DestinationObjects and DestinationFields that Census can write to.

### Mappings

Mappings define how columns from the source model are projected onto fields in the destination object. Each mapping specifies a MappingType (direct field, constant, formula) and a BehaviorMapping for identifier resolution.

### Segments

The Audience Hub allows visual segment construction over warehouse data, producing Segment objects that can be synced to ad platforms, marketing tools, and CDPs.

### Embedded and Connect

Census Embedded enables SaaS builders to offer reverse ETL to their own customers. Connect Links capture end-user credentials and programmatically provision pipelines.

## Type Summary

| Category | Types |
|---|---|
| Sync | Sync, SyncDetails, SyncStatus, SyncType |
| Sync Runs | SyncRun, SyncRunDetails, SyncRunStatus, SyncRunError |
| Destinations | Destination, DestinationDetails, DestinationType, DestinationObject, DestinationField |
| Sources | DataSource, DataSourceDetails, Warehouse, WarehouseDetails, WarehouseType |
| Models | SourceModel, SourceModelDetails, SourceModelType, SQL, SQLQuery, DBT, DBTModel, LookerLook |
| Mappings | Mapping, MappingDetails, MappingField, MappingType, BehaviorMapping |
| Operations | Operation, OperationType |
| Records | Record, RecordDetails, RecordStatus |
| Segments | Segment, SegmentDetails |
| Connections | Connection, ConnectionDetails, ConnectionTest |
| Schema Discovery | Schema, SchemaDetails, Table, Column, ColumnType |
| Fields | Field, FieldDetails, Object, ObjectDetails |
| Auth | APIKey, Token |
| Webhooks | Webhook, WebhookEvent |
| Queries | Query |
| Mutations | Mutation |

## File

- `census-co-schema.graphql` — Full GraphQL schema definition with 60+ named types.

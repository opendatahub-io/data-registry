# Data Registry concepts and terminology

The Data Registry records metadata about data assets; it does not store their
data. Its API path shows how assets are organized, for example:

```text
/v1/team-a/namespaces/training-data/generic-tables/sales
    project            collection                  asset
```

In this path, `namespaces` is the API term for collections. The OpenShift
project (`team-a`) is the [authorization boundary](auth.md), not the
collection.

| Term                     | Meaning                                                                                                                                               |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Project**              | The RHOAI/OpenShift project, backed by a Kubernetes namespace. It appears as `{project}` in API paths and scopes registry access.                     |
| **Collection**           | A logical group of assets within a project. The API calls it a `namespace`; it is not a Kubernetes namespace or a separate RBAC boundary.             |
| **Data asset**           | A metadata record for structured or unstructured data. Registering it does not copy or verify the physical data.                                      |
| **Table**                | A structured asset with format and optional schema or location metadata. The Iceberg `tables` API covers Iceberg-format assets.                       |
| **Generic table**        | A structured asset registered through the Data Registry extension, including non-Iceberg formats such as Parquet or CSV.                              |
| **Volume**               | An unstructured asset, such as a location containing documents or images. It is not a Kubernetes PersistentVolume.                                    |
| **Format**               | The declared representation of an asset, such as `parquet` or `documents`. Registering a format does not convert or validate the stored data.         |
| **Storage location**     | An optional direct address for physical data. An asset may use a connection reference instead; both references may also be absent.                  |
| **Connection reference** | An optional pointer to a Data Connect Hub connection ID or an RHOAI Connection Secret name. The registry stores the reference, not credential values. |
| **Label**                | A project-level name for grouping and filtering assets. An asset can have multiple labels; older material may call these tags.                        |
| **Owner**                | The authenticated creator recorded on an asset. Ownership metadata does not replace project RBAC or grant access to the physical data.                |
| **Physical data**        | The actual objects, files, or tables in storage or a database. Access to them is authorized separately from registry metadata.                        |

For a worked example, see the [Data Registry customer walkthrough](https://github.com/red-hat-data-services/red-hat-ai-examples/tree/main/examples/data-registry).

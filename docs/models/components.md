# Components

**Comonents**: 

Health status of import service componenets



## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `database`                                                         | [Optional[models.Database]](../models/database.md)                 | :heavy_minus_sign:                                                 | Health status of database component.                               |
| `file_system`                                                      | [Optional[models.FileSystem]](../models/filesystem.md)             | :heavy_minus_sign:                                                 | Health status of file system component.                            |
| `external_services`                                                | [Optional[models.ExternalServices]](../models/externalservices.md) | :heavy_minus_sign:                                                 | Health status of external services components.                     |
| `processing_engine`                                                | [Optional[models.ProcessingEngine]](../models/processingengine.md) | :heavy_minus_sign:                                                 | Health status of processing engine component.                      |
| `storage`                                                          | [Optional[models.Storage]](../models/storage.md)                   | :heavy_minus_sign:                                                 | Health status of storage component.                                |
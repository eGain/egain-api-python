# FolderSummary

This schema contains the topic ID and name of the Folder. This is used by FolderBreadcrumb.


## Fields

| Field                                                    | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `id`                                                     | *Optional[int]*                                          | :heavy_minus_sign:                                       | ID of the folder.                                        |
| `name`                                                   | *Optional[str]*                                          | :heavy_minus_sign:                                       | Name of the folder.                                      |
| `link`                                                   | [Optional[models.SchemasLink]](../models/schemaslink.md) | :heavy_minus_sign:                                       | N/A                                                      |
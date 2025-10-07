# ExportStatusResults

Breakdown of completed job results.


## Fields

| Field                                      | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `successful`                               | *Optional[int]*                            | :heavy_minus_sign:                         | The count of successfully processed items. | 4485                                       |
| `warnings`                                 | *Optional[int]*                            | :heavy_minus_sign:                         | The count of items with warnings.          | 10                                         |
| `errors`                                   | *Optional[int]*                            | :heavy_minus_sign:                         | The count of items with errors.            | 5                                          |
# ImportContentDataSource


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `type`                                                                       | [models.ImportContentType](../models/importcontenttype.md)                   | :heavy_check_mark:                                                           | Type of data source                                                          |
| `path`                                                                       | *str*                                                                        | :heavy_check_mark:                                                           | Path of the data source                                                      |
| `region`                                                                     | *Optional[str]*                                                              | :heavy_minus_sign:                                                           | Region of the data source                                                    |
| `credentials`                                                                | [Optional[models.DataSourceCredentials]](../models/datasourcecredentials.md) | :heavy_minus_sign:                                                           | N/A                                                                          |
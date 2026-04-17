# DataSourceCredentials


## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `access_key_id`                                                          | *Optional[str]*                                                          | :heavy_minus_sign:                                                       | Access key for S3 credentials datasource. Provide along with Secret Key. |
| `secret_access_key`                                                      | *Optional[str]*                                                          | :heavy_minus_sign:                                                       | Secret key for S3 credentials datasource. Provide along with Access Key. |
| `username`                                                               | *Optional[str]*                                                          | :heavy_minus_sign:                                                       | Username for SFTP credentials datasource. Provide along with Password.   |
| `password`                                                               | *Optional[str]*                                                          | :heavy_minus_sign:                                                       | Password for SFTP credentials datasource. Provide along with Username.   |
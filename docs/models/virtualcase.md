# VirtualCase


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `id`                                                   | *Optional[str]*                                        | :heavy_minus_sign:                                     | ID of the case                                         |                                                        |
| `detail_field`                                         | List[[models.DetailField](../models/detailfield.md)]   | :heavy_minus_sign:                                     | detail fields                                          |                                                        |
| `display_field`                                        | List[[models.DisplayField](../models/displayfield.md)] | :heavy_minus_sign:                                     | display fields                                         |                                                        |
| `dynamic_cluster_id`                                   | *Optional[str]*                                        | :heavy_minus_sign:                                     | Cluster id                                             | 1000001035                                             |
| `title`                                                | *Optional[str]*                                        | :heavy_minus_sign:                                     | name of the case                                       |                                                        |
| `virtual_case_id`                                      | *Optional[str]*                                        | :heavy_minus_sign:                                     | virtual case id                                        |                                                        |
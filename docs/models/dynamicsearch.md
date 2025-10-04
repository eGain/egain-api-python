# DynamicSearch


## Fields

| Field                                                      | Type                                                       | Required                                                   | Description                                                | Example                                                    |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `dynamic_cluster`                                          | List[[models.DynamicCluster](../models/dynamiccluster.md)] | :heavy_minus_sign:                                         | clusters in search                                         |                                                            |
| `parent_cluster_id`                                        | *Optional[str]*                                            | :heavy_minus_sign:                                         | Parent cluster                                             | 1000001035                                                 |
| `type`                                                     | *Optional[str]*                                            | :heavy_minus_sign:                                         | type of search                                             |                                                            |
| `virtual_case`                                             | List[[models.VirtualCase](../models/virtualcase.md)]       | :heavy_minus_sign:                                         | cases in search                                            |                                                            |
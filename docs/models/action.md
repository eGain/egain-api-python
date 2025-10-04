# Action


## Fields

| Field                                                    | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `id`                                                     | *Optional[str]*                                          | :heavy_minus_sign:                                       | ID of the action                                         |
| `title`                                                  | *Optional[str]*                                          | :heavy_minus_sign:                                       | Name of the action                                       |
| `type`                                                   | *Optional[str]*                                          | :heavy_minus_sign:                                       | type of the action                                       |
| `short_name`                                             | *Optional[str]*                                          | :heavy_minus_sign:                                       | short name of the action                                 |
| `reject_count`                                           | *Optional[int]*                                          | :heavy_minus_sign:                                       | number of times action was rejected.                     |
| `accept_count`                                           | *Optional[int]*                                          | :heavy_minus_sign:                                       | number of times action was accepted.                     |
| `metadata`                                               | List[[models.Metadata](../models/metadata.md)]           | :heavy_minus_sign:                                       | Metadata of action                                       |
| `article_type`                                           | [Optional[models.ArticleType]](../models/articletype.md) | :heavy_minus_sign:                                       | The type of the Article and its attributes.              |
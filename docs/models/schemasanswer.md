# SchemasAnswer


## Fields

| Field                                        | Type                                         | Required                                     | Description                                  | Example                                      |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `id`                                         | *Optional[str]*                              | :heavy_minus_sign:                           | ID of the answer                             | 1000001035                                   |
| `depth`                                      | *Optional[int]*                              | :heavy_minus_sign:                           | depth of the answer                          |                                              |
| `is_invisible`                               | *Optional[bool]*                             | :heavy_minus_sign:                           | Flag indicating if answer is visible         |                                              |
| `text`                                       | *Optional[str]*                              | :heavy_minus_sign:                           | Text of the answer                           |                                              |
| `image`                                      | [Optional[models.Image]](../models/image.md) | :heavy_minus_sign:                           | N/A                                          |                                              |
| `concept_name`                               | *Optional[str]*                              | :heavy_minus_sign:                           | name of the answer                           |                                              |
| `concept_id`                                 | *Optional[str]*                              | :heavy_minus_sign:                           | Id of the answer                             |                                              |
| `lower_value`                                | *Optional[int]*                              | :heavy_minus_sign:                           | lower value of the answer                    |                                              |
| `upper_value`                                | *Optional[int]*                              | :heavy_minus_sign:                           | upper value of the answer                    |                                              |
| `enum_lower_value`                           | *Optional[str]*                              | :heavy_minus_sign:                           | lower value of enum answer                   |                                              |
| `enum_upper_value`                           | *Optional[str]*                              | :heavy_minus_sign:                           | upper value of enum answer                   |                                              |
| `lower_inclusive`                            | *Optional[bool]*                             | :heavy_minus_sign:                           | Value indicating if lower value is inclusive |                                              |
| `upper_inclusive`                            | *Optional[bool]*                             | :heavy_minus_sign:                           | Value indicating if upper value is inclusive |                                              |
| `partial_min`                                | *Optional[int]*                              | :heavy_minus_sign:                           | Partial minimum                              |                                              |
| `partial_max`                                | *Optional[int]*                              | :heavy_minus_sign:                           | Partial maximim                              |                                              |
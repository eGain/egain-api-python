# ContactPerson

ContactPerson


## Fields

| Field                                    | Type                                     | Required                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `first_name`                             | *str*                                    | :heavy_check_mark:                       | First name of the customer               |
| `middle_name`                            | *Optional[str]*                          | :heavy_minus_sign:                       | Middle name of the customer              |
| `last_name`                              | *Optional[str]*                          | :heavy_minus_sign:                       | Last name of the customer                |
| `email`                                  | List[[models.Email](../models/email.md)] | :heavy_check_mark:                       | Email details                            |
| `phone`                                  | List[[models.Phone](../models/phone.md)] | :heavy_minus_sign:                       | Phone details                            |
# UserDetails

Success


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `id`                                   | *Optional[str]*                        | :heavy_minus_sign:                     | The numerical ID of the User           |                                        |
| `roles`                                | List[[models.Role](../models/role.md)] | :heavy_minus_sign:                     | Roles of the User                      |                                        |
| `first_name`                           | *Optional[str]*                        | :heavy_minus_sign:                     | First Name of the User                 | John                                   |
| `last_name`                            | *Optional[str]*                        | :heavy_minus_sign:                     | Last Name of the User                  | Doe                                    |
| `has_email_configured`                 | *Optional[bool]*                       | :heavy_minus_sign:                     | Indicates if user has email            |                                        |
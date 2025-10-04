# Attachments

This schema contains the definition of Attachments.


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `count`                                                            | *Optional[int]*                                                    | :heavy_minus_sign:                                                 | The number of Attachments in the list.                             |
| `link`                                                             | [Optional[models.Link]](../models/link.md)                         | :heavy_minus_sign:                                                 | Defines the relationship between this resource and another object. |
| `attachments`                                                      | List[[models.AttachmentSummary](../models/attachmentsummary.md)]   | :heavy_minus_sign:                                                 | The list of Attachments.                                           |
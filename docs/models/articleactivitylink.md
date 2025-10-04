# ArticleActivityLink


## Fields

| Field                                                                          | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `version_id`                                                                   | *str*                                                                          | :heavy_check_mark:                                                             | An Article version's ID.                                                       |
| `edition_id`                                                                   | *Optional[str]*                                                                | :heavy_minus_sign:                                                             | An Article edition's ID.                                                       |
| `language`                                                                     | [models.ArticleActivityLinkLanguage](../models/articleactivitylinklanguage.md) | :heavy_check_mark:                                                             | The knowledge base language in which the version is created.                   |
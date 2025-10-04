# TopicAISearchResult

This schema contains general information about the topic.


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `name`                                                               | *str*                                                                | :heavy_check_mark:                                                   | Name of Topic.                                                       |
| `article_count_in_topic`                                             | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | Number of articles within the topic.                                 |
| `article_count_in_topic_tree`                                        | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | Number of articles in this topic and all sub-topics.                 |
| `created_by`                                                         | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | The ID of the user that created this resource.                       |
| `created_date`                                                       | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `department_id`                                                      | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `last_modified_by`                                                   | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | The ID of the user that modified this resource.                      |
| `last_modified_date`                                                 | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `id`                                                                 | *str*                                                                | :heavy_check_mark:                                                   | N/A                                                                  |
| `child_count`                                                        | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
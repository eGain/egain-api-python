# TopicBreadcrumbsList

This schema contains an array of topic breadcrumbs, allowing clients to distinguish between multiple distinct hierarchical topic paths.


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `topic_breadcrumb`                                                   | List[[models.TopicBreadcrumb](../models/topicbreadcrumb.md)]         | :heavy_minus_sign:                                                   | An array of TopicBreadcrumb instances representing individual paths. |
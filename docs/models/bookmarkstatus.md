# BookmarkStatus

Article Bookmark Status


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `is_bookmarked`                                                    | *bool*                                                             | :heavy_check_mark:                                                 | Indicates whether the Article is bookmarked                        |
| `bookmark_id`                                                      | *Optional[int]*                                                    | :heavy_minus_sign:                                                 | The ID of the Bookmark, if Article is bookmarked.                  |
| `folder_breadcrumb`                                                | [Optional[models.FolderBreadcrumb]](../models/folderbreadcrumb.md) | :heavy_minus_sign:                                                 | This schema contains one or more FolderSummary instances.          |
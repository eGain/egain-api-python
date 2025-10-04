# GHSearchResult

Success


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `casebase`                                                     | [Optional[models.Casebase]](../models/casebase.md)             | :heavy_minus_sign:                                             | N/A                                                            |
| `action_search`                                                | List[[models.ActionSearch](../models/actionsearch.md)]         | :heavy_minus_sign:                                             | actions in the search                                          |
| `answered_question`                                            | List[[models.AnsweredQuestion](../models/answeredquestion.md)] | :heavy_minus_sign:                                             | questions answered in the search                               |
| `case_search`                                                  | List[[models.CaseSearch](../models/casesearch.md)]             | :heavy_minus_sign:                                             | cases in the search                                            |
| `dynamic_search`                                               | List[[models.DynamicSearch](../models/dynamicsearch.md)]       | :heavy_minus_sign:                                             | dynamic cases in the search                                    |
| `unanswered_question`                                          | List[[models.Question](../models/question.md)]                 | :heavy_minus_sign:                                             | unanswered questions in the search                             |
| `startup_question`                                             | List[[models.Question](../models/question.md)]                 | :heavy_minus_sign:                                             | startup questions in the search                                |
| `target_clusters`                                              | List[[models.ClusterID](../models/clusterid.md)]               | :heavy_minus_sign:                                             | active clusters in the search                                  |
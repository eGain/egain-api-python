# CaseQuestionDetail


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `question`                                         | [models.CaseQuestion](../models/casequestion.md)   | :heavy_check_mark:                                 | N/A                                                |
| `answer`                                           | List[[models.CaseAnswer](../models/caseanswer.md)] | :heavy_check_mark:                                 | Answer of the question                             |
| `scoring_value`                                    | *Optional[float]*                                  | :heavy_minus_sign:                                 | Weightage of the question                          |
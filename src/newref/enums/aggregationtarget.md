# AggregationTarget

```ts
import { AggregationTarget } from '@singular/core';
```

An enum for defining the target of an [AggregationRule](../models/aggregationrule) object:
  - AggregationTarget.**Headers**: Applies the aggregation rules on the request headers.
  - AggregationTarget.**Queries**: Applies the aggregation rules on the request query parameters.
  - AggregationTarget.**Body**: Applies the aggregation rules on the request body.
  - AggregationTarget.**Params**: Applies the aggregation rules on the request path parameters.
  - AggregationTarget.**Custom**: Applies the aggregation rules on the [request object](.).

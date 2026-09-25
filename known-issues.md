# Known Issues

This document describes known issues that affect the Mule 4 Batch Job examples in this repository.

## Batch Aggregator Size Cannot Be Configured Using an Application Property

With Mule runtime 4.12.0, the `size` attribute of a Batch Aggregator cannot be configured using an application property.

Externalizing the Batch Aggregator size is useful when evaluating and tuning Batch Job performance because the value can be changed without modifying the Mule configuration. This repository previously used this approach:

```xml
<batch:aggregator size="${batch.aggregator.main.size}">
```

During Maven processing, Mule 4.12.0 fails AST validation when the property is resolved:

```text
java.lang.ClassCastException: class java.lang.String cannot be cast to class java.lang.Integer
```

The failure occurs in the Mule runtime `BatchStepAggregatorStreamingOrSize` AST validator, which expects the Batch Aggregator `size` value to be an `Integer` but receives the application property as a `String`.

Using a DataWeave expression to explicitly coerce the property to a number is not an alternative because expressions are not supported for the Batch Aggregator `size` field.

As a workaround, the Batch Aggregator size must currently be defined as a literal value in the Mule configuration:

```xml
<batch:aggregator size="1000">
```

Consequently, changing the Batch Aggregator size for performance testing requires modifying the Mule configuration.

---

Copyright © 2026 Alan Belisle. Licensed under the [Apache License 2.0](LICENSE).

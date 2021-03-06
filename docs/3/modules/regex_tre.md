---
title: "Module Details: regex_tre (v3)"
---

## The "regex_tre" Module

!!! note ""
    This module depends on a third-party library ([TRE](https://laurikari.net/tre/)) and must be manually enabled at compile time.

    Once you have installed the dependency you can enable this module using the following command:

    <pre><code>./configure --enable-extras regex_tre</code></pre>

### Description

This module provides a regular expression engine which uses the [TRE](https://laurikari.net/tre/) library.

### Configuration

To load this module use the following `<module>` tag:

```xml
<module name="regex_tre">
```

This module requires no other configuration.

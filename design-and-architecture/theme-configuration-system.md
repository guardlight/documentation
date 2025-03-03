# Theme Configuration System

For each theme the user can build a configuration that Guardlight will use to analyze the content with.

The Configuration will be built up by various sources. The analyzers will define their set of inputs required that the user complete.

The user will also have a a threshold setting per analyzer and overall.&#x20;

If the analysis matches any of the thresholds, it will be shown to the user at main page level, as well.

For example.

```
Theme Configuration Screen (per theme)
- Analyzer Section
  - Analyzer specified inputs
  - Threshold settings
    - Green: 0 < [input]
    - Yellow: {Green} < [input] > Red
    - Red: {Yellow} < 100
- Main threshold
  - ...
```


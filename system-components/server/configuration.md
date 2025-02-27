# Configuration

{% hint style="info" %}
All config properties can be overridden by environment variables. Please see [Environment Variables](https://van-niekerk.gitbook.io/guardlight/system-components/server/configuration#environment-variables)
{% endhint %}

## General Configuration

### Data Content Size

Data that needs analysis can be very large. The data/text is divided into a specific chunks/sections sizes so that the analysis can be efficient and precise and allows the analyzers to run on less powerful machines.

Some users may have much more powerful machines, and can use a bigger content size. The following config property allows that content size to be changed.

```yaml
data:
    content:
        size: 2000
```

## Parser config

Guardlight allows for extra parsers to be added to extend it's parsing functionality.

{% hint style="info" %}
For a more detailed guided on how extending Guardlight works. Please see [Extending Parsers](https://van-niekerk.gitbook.io/guardlight/getting-started/extending-guardlight#adding-parsers-example).
{% endhint %}

Adding more parsers can be done via the `parsers` config section with the following config.

When adding parsers via the config, the parsers will also become available for selecting in the UI.

#### Config Explanation

<table><thead><tr><th width="161">Property</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>The type and also the topic name for this parser.</td></tr><tr><td>name</td><td>Name for the parser show in the UI.</td></tr><tr><td>description</td><td>Description show in the UI.</td></tr></tbody></table>

#### Configuration

{% code fullWidth="false" %}
```yaml
parsers:
    - type: epub
      name: EPUB Parses
      description: Parses epub files to utf-8 standard text
```
{% endcode %}

{% hint style="warning" %}
The `text` and `result` parser topic names are reserved and cannot be used or overridden.&#x20;
{% endhint %}

## Analyzer config

Guardlight allows for extra parsers to be added to extend it's parsing functionality.

{% hint style="info" %}
For a more detailed guided on how extending Guardlight works. Please see [Extending Analyzers](https://van-niekerk.gitbook.io/guardlight/getting-started/extending-guardlight#adding-analyzers-example).
{% endhint %}

Adding more analyzers can be done via the `analyzers` config section with the following config.

When adding analyzers via the config, the analyzers will also become available for selecting in the UI.

#### Config Explanation

<table><thead><tr><th width="164">Property</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>The type and also the topic name for this analyzer.</td></tr><tr><td>name</td><td>Name for the analyzer show in the UI.</td></tr><tr><td>description</td><td>Description show in the UI.</td></tr></tbody></table>

#### Configuration

```yaml
analyzers:
    - type: static
      name: Static Analyzer
      description: Uses a basic word list to scan content for.
```

{% hint style="warning" %}
The `result` analyzer topic name are reserved and cannot be used or overridden.
{% endhint %}

## Environment Variables

All config properties can be overridden by environment variables

Each property can be overridden by using the prefix `GUARDLIGHT_` and the property with each indentation as a `.` .

For example: Changing the Data Content Size: `GUARDLIGHT_DATA_CONTENT_SIZE=200`




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

<table><thead><tr><th width="164">Property</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>The type and also the topic name for this analyzer.</td></tr><tr><td>name</td><td>Name for the analyzer show in the UI.</td></tr><tr><td>description</td><td>Description show in the UI.</td></tr><tr><td>inputs</td><td>List of objects for defining the input the analyzer requires from the User. This is an extension of the base analyzer input contract.</td></tr><tr><td>output</td><td>An object that the analyzer will give back to the server. This is an extension of the base analyzer result contract.</td></tr></tbody></table>

#### Input Config Explanation

<table><thead><tr><th width="166.5">Property</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>Name of the input which will be the heading in the UI.</td></tr><tr><td>description</td><td>A useful description show under the heading in the UI</td></tr><tr><td>type</td><td>The input required from the user. Can be textarea, textfield.</td></tr></tbody></table>

#### Output Config Explanation

<table><thead><tr><th width="178">Property</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>Defines how the results will be published. Can be list&#x3C;string>, ...</td></tr><tr><td>description</td><td>A helpful description shown to the UI when viewing the report.</td></tr></tbody></table>

#### Configuration

Below is an example of the default analyzer config

```yaml
analyzers:
    - type: word_search
      name: Word Search Analyzer
      description: Uses a basic word list to scan content for.
      inputs:
        - name: Strict Words
          description: Words in this list will immediatly flag the content.
          type: textarea
      output:
        type: list<string> # Actual content
        description: The following words where detected.
    - type: sentiment_analysis
      name: Sentiment Analyzer
      description: Uses the predefined word or phrase list to determine the sentiment of each word/phrase
      inputs:
        - name: Contextual Words
          description: These words/phrases will be used to scan the text and a score (between -1 and 1) will be determined for each. 
          type: textarea
      output:
        type: list<string>
        description: The phrases matches.
```

{% hint style="warning" %}
The `result` analyzer topic name are reserved and cannot be used or overridden.
{% endhint %}

## Environment Variables

All config properties can be overridden by environment variables

Each property can be overridden by using the prefix `GUARDLIGHT_` and the property with each indentation as a `.` .

For example: Changing the Data Content Size: `GUARDLIGHT_DATA_CONTENT_SIZE=200`




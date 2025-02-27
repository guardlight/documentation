# Extending Guardlight

Guardlight allows to be extended with more parsers and analyzers that communicate through the **NATS Jetstream**, following a common interface for parsing and analyzing. These configurations are added to the server configuration file.

## Via NATS Jetstream

{% hint style="info" %}
For an detailed explanation of how Guardlight uses NATS. Please see [Guardlight NATS usage](https://van-niekerk.gitbook.io/guardlight/system-components/server/nats-jetstream#guardlight-nats-usage).
{% endhint %}

When adding functionality via NATS, the added components communicate through 2 main topics. The `"request"` topic and `result` topic.

For each type of added functionality, there is a subtopic and a topic for the specific component.&#x20;

When the specific component is used, a message is placed on the said topic and there it waits until the component takes the message from the topic and consumes it.

When the data is processed, it gets returned via another topic. The "request" and result topic adheres to a specific interface contract.

### Adding Parsers Example

Lets say there is a need to upload and parse a specific file type that Guardlight does not natively support, such as a Word Document (.docx).&#x20;

You can add a new parser to the parsers group, such as `parsers.docx` .

The parser will then consume the .docx data (binary data) and converts it into a utf-8 text format and place it back onto the `parsers.result` topic.

{% hint style="info" %}
For a detailed explanation on the contract between a parser and Guardlight. Please see [Parser Contract](https://van-niekerk.gitbook.io/guardlight/system-components/parsers#parser-contract).
{% endhint %}

{% hint style="info" %}
For a detailed explanation on adding a new parser to the config. Please see [Parser Config](https://van-niekerk.gitbook.io/guardlight/system-components/server/configuration#parser-config).
{% endhint %}

### Adding Analyzers Example

lets say there is a need to analyze the text using a specific approach or algorithm that Guardlight does not natively supports, such a advanced AI analysis.

You can add a new analyzer to the analyzers group, such as `analyzers.super-ai` .

The analyzer will then consume the data section and analyze it and then place the results back onto the `analyzers.result` topic.

{% hint style="info" %}
For a detailed explanation on the contract between an analyzer and Guardlight. Please see [Analyzer Contract](https://van-niekerk.gitbook.io/guardlight/system-components/analyzers#analyzer-contract).
{% endhint %}

{% hint style="info" %}
For a detailed explanation on adding a new analyzer to the config. Please see [Analyzer Config](https://van-niekerk.gitbook.io/guardlight/system-components/server/configuration#analyzer-config).
{% endhint %}


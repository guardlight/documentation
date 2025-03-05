# Job Queuing

## Overview

Guardlight uses job queuing to schedule different jobs such as parsing, analysis, etc.



### Queue Model

<table><thead><tr><th width="152">Property</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>Job id.</td></tr><tr><td>data</td><td>A json field with data for the destination app.</td></tr><tr><td>topic</td><td>Destination app topic name.</td></tr><tr><td>status</td><td>The status of the job.</td></tr><tr><td>retryCount</td><td>The amount the job was retried.</td></tr></tbody></table>

#### Topic names

A topic name decribes the name where an external app is communicating on via NATS. This can be something like parser.epub or analyzer.result.&#x20;

#### Job status

Can be one of the following: queued, inprogress, done, error.

#### Data

Different json data structure for each app.&#x20;

{% hint style="info" %}
See [Analyzer Input Contract](https://refactored.gitbook.io/guardlight/system-components/analyzers#input-contract) for more info.
{% endhint %}

{% hint style="info" %}
See [Parser Input Contract](https://refactored.gitbook.io/guardlight/system-components/parsers#parser-contract) for more info.
{% endhint %}

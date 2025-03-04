# Analyzers

## Analyzer Contract

The contract is the data structure that will be common between Guardlight and an Analyzer.

### Terminology

**Score —** The score is a value between -1 and 1 and describes how well the analysis fit the theme that is being analyzed for. -1 means it does not match the theme, and 1 means it matches the theme perfect. The more perfect a theme match is, the more bad the content is for consumption.&#x20;

### Input Contract

<table><thead><tr><th width="155">Property</th><th>Description</th></tr></thead><tbody><tr><td>data</td><td>The content that needs to be analyzed.</td></tr><tr><td>inputs</td><td>Key|Value list of defined inputs</td></tr><tr><td></td><td></td></tr></tbody></table>

### Output Contract

<table><thead><tr><th width="158">Property</th><th>Description</th></tr></thead><tbody><tr><td>score</td><td>The total score for the analysis.</td></tr><tr><td>type</td><td>How the analysis results will be structured. [detailed]</td></tr><tr><td>content</td><td>The results of the analysis. Adhering to [Type]</td></tr><tr><td>description</td><td>A description of the analysis. Can be static or a summary.</td></tr></tbody></table>

#### Output Type

* **detailed —** A detailed list of strings. Each list item have detailed analysis results. The details can be shown in the UI.&#x20;

### Detailed

<table><thead><tr><th width="162">Property</th><th>Description</th></tr></thead><tbody><tr><td>score</td><td>The score per list item</td></tr><tr><td>content</td><td>The analysis result content per item</td></tr></tbody></table>

## Environment Variables provided by Guardlight

<table><thead><tr><th width="161">Variable</th><th>Description</th></tr></thead><tbody><tr><td>GL_NATS_URL</td><td>The URL to the NATS server</td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr></tbody></table>


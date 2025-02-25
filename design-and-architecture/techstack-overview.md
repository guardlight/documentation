# Techstack overview

Guardlight’s base setup consists of three main components: the UI, the server, and basic parsers and analyzers.

### UI

The UI is built with **React** and provides an intuitive interface for users to upload ebooks or add free text. It allows users to select themes, topics, and word lists for content analysis. Additionally, users can add, edit, or remove these themes/topics and word lists according to their needs.

### **Server**

The server is written in **Golang** and serves as the core of the system. It interacts with a **PostgreSQL** database for storage and uses **Docker** for infrastructure orchestration. For messaging between external adapters and internal services, it leverages **NATS Jetstream**. The server is responsible for managing the user interface, data storage, and message routing.

### **Parsers and Analyzers**

Currently, the system includes basic parsers written in **Python** for mature context analysis.&#x20;

The parsers includes:

* **EPUB parser**: Parses ebook content in EPUB format.
* **Free text parser**: Analyzes user-inputted free text.

The analyzers includes:

* **Word search:** Searches the content for specific words.

However, the system is designed to be extended. More parsers and analyzers can be added through **NATS Jetstream**, following a common interface for parsing and analyzing. These configurations are added to the server configuration file.

# Job Scheduling and Orchestration

Jobs are scheduled via an internal job scheduler and handled by an **orchestrator**. The orchestrator is responsible for spinning up the necessary containers for each task (such as parsing or analysis).

* **Job Distribution**: The orchestrator distributes the jobs via **NATS Jetstream**, where the job data remains until it is picked up by the appropriate parser or analyzer.
* **Result Handling**: Once the analysis is complete, the result is sent back to **NATS Jetstream** on the result topic. A report is then generated from this data.
* **UI Updates**: The UI is updated via **Server-Sent Events (SSE)**, allowing users to view the latest results in real-time.

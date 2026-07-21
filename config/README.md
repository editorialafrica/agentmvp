| File                     | Purpose                                             | Contract               |
| ------------------------ | --------------------------------------------------- | ---------------------- |
| `pipeline.json`          | Defines execution stages and orchestration          | Pipeline Contract      |
| `dependencies.json`      | Defines stage dependencies (DAG)                    | Pipeline Contract      |
| `prompts.json`           | Registers executable AI agents                      | AI Agent Contract      |
| `artifacts.json`         | Registers generated artifacts                       | Artifact Contract      |
| `drive.json`             | Configures storage backend and artifact persistence | Platform Specification |
| `outputs.json`           | Configures output generation and destinations       | Pipeline Contract      |
| `validation.json`        | Defines validation rules and severity               | Platform Specification |
| `branding.json`          | Defines branding and visual identity                | Platform Specification |
| `filenames.json`         | Defines naming conventions                          | Artifact Contract      |
| `context-ownership.json` | Defines context ownership                           | Context Contract       |
| `production.json`        | Defines production runtime settings                 | Platform Specification |
| `retries.json`           | Defines retry behavior                              | Pipeline Contract      |

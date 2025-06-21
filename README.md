
# context.json

## An open standard for defining AI context and collaboration across platforms

### What is context.json?

As AI models, agents, and humans increasingly collaborate across tools, platforms, and workflows, it becomes critical to **define context, actors, data boundaries, and instructions in a way that is both machine- and human-readable**. Disconnected systems and hidden rules often cause confusion, privacy risk, and inefficiency.

`context.json` solves this by providing a **single, unified, and portable configuration file** that precisely defines all relevant context, instructions, roles, and history for any AI-powered session, workflow, or collaboration. It makes context and collaboration explicit, composable, and auditable, enabling secure, robust, and transparent operations in any environment.


## Key Features

* **Open Standard:** Freely available, community-driven, and vendor-neutral.
* **Cross-Platform:** Works with any AI/ML model, agent, human, or service, across any stack or workflow.
* **Portable:** Move, archive, or share entire sessions, instructions, and history as a single file.
* **Explicit Context:** All instructions, sources, actors, privacy settings, and constraints are clear and inspectable.
* **Auditable Collaboration:** Complete record of who did what, when, and why—critical for compliance, enterprise, and regulated use.
* **Extensible:** Supports custom fields for domain- or use-case-specific configuration.


## context.json Specification (v1)

The `context.json` standard defines a structured way to specify **context, instructions, actors, sources, boundaries, and collaboration history** for any AI-driven workflow. The goal: maximum clarity, security, and interoperability.

### Core Fields

#### `context_id` (Required)

A unique identifier for the context (UUID or deterministic hash).

```json
"context_id": "e3b0c442-98fc-1fc3-9fb3-3259aec0e27a"
```

#### `version` (Required)

The version of the context.json standard.

```json
"version": "1.0.0"
```

#### `purpose` (Required)

Short, clear statement describing what this context is for.

```json
"purpose": "Real-time document co-editing with human and AI agents."
```

#### `actors` (Required)

List of all human users, AI models, or services participating in this context.

```json
"actors": [
  {
    "actor_id": "alice@example.com",
    "role": "user",
    "type": "human"
  },
  {
    "actor_id": "gpt-4",
    "role": "assistant",
    "type": "AI",
    "details": {
      "provider": "OpenAI",
      "capabilities": ["summarization", "chat"]
    }
  }
]
```

#### `sources` (Required)

External documents, APIs, or data used within the session.

```json
"sources": [
  {
    "type": "document",
    "uri": "https://example.com/project-spec.pdf",
    "description": "Project requirements"
  }
]
```

#### `instructions` (Required)

Explicit step-by-step instructions or rules for the workflow. Each is a clear, single string.

```json
"instructions": [
  "Summarize key requirements before generating code.",
  "Do not access external APIs without user approval.",
  "All output must be in markdown format."
]
```

#### `boundaries` (Required)

Defines privacy, scope, output, and data usage constraints.

```json
"boundaries": {
  "context_window": 8192,
  "privacy": "confidential",
  "output_format": "markdown",
  "other_constraints": [
    "No personally identifiable information may be shared.",
    "Session expires after 60 minutes of inactivity."
  ]
}
```

#### `history` (Required)

Chronological log of all significant events, messages, and actions.

```json
"history": [
  {
    "timestamp": "2025-06-21T12:00:00Z",
    "actor_id": "alice@example.com",
    "event_type": "message",
    "content": "Started session."
  },
  {
    "timestamp": "2025-06-21T12:02:00Z",
    "actor_id": "gpt-4",
    "event_type": "completion",
    "content": "Provided summary of project requirements."
  }
]
```

#### `timestamp` (Required)

Creation or last update time for this context.

```json
"timestamp": "2025-06-21T12:30:00Z"
```

#### `extensions` (Optional)

Open-ended space for any additional configuration, protocol links, or metadata.

```json
"extensions": {
  "related_protocols": [
    "https://github.com/modelyaml/modelyaml",
    "https://llmstxt.org/"
  ],
  "custom_field": "example_value"
}
```


## Complete Example

```json
{
  "context_id": "d9f6c1b3-43e6-47c9-8eb8-ec0c7b6d900f",
  "version": "1.0.0",
  "purpose": "Cross-platform, human-AI collaborative code review.",
  "actors": [
    {
      "actor_id": "dev1@acme.com",
      "role": "reviewer",
      "type": "human"
    },
    {
      "actor_id": "gpt-4",
      "role": "assistant",
      "type": "AI",
      "details": {
        "provider": "OpenAI",
        "capabilities": ["suggestion", "linting"]
      }
    }
  ],
  "sources": [
    {
      "type": "document",
      "uri": "https://acme.com/repos/project/main.py",
      "description": "Python source file"
    }
  ],
  "instructions": [
    "Review all code for security and efficiency.",
    "Suggest improvements as inline comments.",
    "Log every major suggestion to history."
  ],
  "boundaries": {
    "context_window": 4096,
    "privacy": "private",
    "output_format": "plaintext",
    "other_constraints": [
      "No code changes allowed without user approval."
    ]
  },
  "history": [
    {
      "timestamp": "2025-06-21T10:00:00Z",
      "actor_id": "dev1@acme.com",
      "event_type": "upload",
      "content": "Uploaded main.py"
    },
    {
      "timestamp": "2025-06-21T10:01:00Z",
      "actor_id": "gpt-4",
      "event_type": "message",
      "content": "Suggested optimization for function process_data()."
    }
  ],
  "timestamp": "2025-06-21T10:05:00Z",
  "extensions": {
    "custom_label": "code_review_sprint42"
  }
}
```


## Why Use context.json?

### Clarity

Eliminates hidden context. Everyone—human or AI—sees the same instructions, sources, and constraints.

### Security & Privacy

Explicit boundaries and roles help ensure correct use of data, auditability, and regulatory compliance.

### Portability

Move sessions and workflows between teams, tools, and AI agents with full fidelity.

### Auditable Collaboration

A clear, inspectable record of all actions, sources, and events—enabling trusted, accountable AI.

### Extensible

Support for custom domains, fields, and future protocol links—built for growth and ecosystem integration.


## Contributing

context.json is an open standard, actively seeking community input and implementation feedback.
See [GitHub](https://github.com/davidkimai/context.json) for drafts, specification, and examples.
Discussion and improvements welcome.


context.json is an open standard ・ v1 ・ [Contribute on GitHub](https://github.com/davidkimai/context.json/pulls)

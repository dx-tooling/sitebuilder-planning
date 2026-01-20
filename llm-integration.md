### LLM Integration and Execution Model

The SiteBuilder provides a bi-directional chat UI. User messages are sent to a SOTA LLM provider (e.g. OpenAI) via their API using the user's BYOK key, and the LLM agent runs inside the same workspace container that contains the content project.

Execution flow:

- User clicks "new content project" or "edit content project".
- The application launches a fresh workspace container for this session.
- The container pulls the latest version of the project's git repository into its workspace.
- The editor UI opens and the user chats with the LLM.
- The LLM agent uses tools to read/write files in the workspace and execute commands (e.g. `npm build`) inside the container.
- Each interaction can create a new version/commit for history and rollback.

Guardrails and limits:

- Containers are ephemeral per session and run with strict filesystem boundaries (no host mounts).
- Command execution is limited to a defined allowlist, with timeouts and resource quotas.
- All file changes and command executions are logged for auditing and rollback.
- Network access is scoped to required services only.

BYOK handling:

- API keys are stored encrypted in the application database and injected into the runtime only when needed.
- Keys are never written to the container filesystem or logs.
- Access to keys is scoped to the owning organization and session.

Preview and build pipeline:

- The container provides build and preview commands that output artifacts to a known location.
- The web UI reads preview output from the container and streams it into the embedded preview area.
- Export generates a ZIP from the latest build output inside the container.

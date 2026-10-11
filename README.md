# Assignment 4 — Multi-Agent System (MAS) with n8n

A multi-agent workflow built in **n8n**. A chat message enters the workflow, is processed by two connected AI Agent nodes, and can use web search to support answers with current information.

## Project Overview

This assignment demonstrates agent orchestration in n8n: the output from the first AI Agent is passed to a second AI Agent as part of a sequential workflow. The visible workflow also includes a Groq Chat Model, Simple Memory, and a Tavily web-search tool.

## Workflow Components

| Component | Role in the visible workflow |
|---|---|
| When chat message received | Starts the workflow when a user submits a chat message |
| AI Agent | Processes the incoming request using its configured instructions and connected model/tools |
| AI Agent1 | Receives the preceding agent's output and performs the next configured agent step |
| Groq Chat Model | Supplies the language model used by the agent nodes |
| Simple Memory | Provides conversational memory to the connected agent(s) |
| Search the web in Tavily | Gives the connected agent a web-search tool for finding relevant online information |

**Note:** The exact responsibilities of AI Agent and AI Agent1 depend on their system prompts in the n8n workflow. Update this section with the specific role you assigned to each agent before submission.

## How the Workflow Runs

1. A user enters a question in the n8n chat.
2. The chat trigger starts the workflow and passes the message to the first AI Agent.
3. The first agent processes the question using its configured prompt, Groq Chat Model, memory, and available tools.
4. The first agent's output is passed to the second AI Agent.
5. The second agent processes that output according to its own configured instructions.
6. The workflow returns the resulting response in the chat.

The screenshot shows a test query about Lionel Messi and a response containing biographical and football-related information. Since the workflow has a Tavily search tool, verify in the execution trace whether it was actually called for a particular response before claiming that every answer is web-verified.

## Technologies Used

- **n8n** — visual workflow automation and agent orchestration
- **Groq Chat Model** — language-model inference
- **Simple Memory** — conversational context
- **Tavily Search** — web-search tool connected to an agent

## Example Test

**User query:** `Who is Leo Messi?`

The workflow returns a natural-language answer about Lionel Messi. The included screenshot records an example execution.

## Repository Structure

```text
Assignment-4-n8n-MAS/
├── README.md
├── .gitignore
├── workflow/
│   └── (add the exported n8n workflow JSON here)
└── screenshots/
    ├── workflow-overview.png
    └── sample-execution.png
```

## Setup and Usage

1. Export the completed workflow from n8n as a JSON file.
2. Place the reviewed JSON export in the `workflow/` directory.
3. Import the workflow into your own n8n instance.
4. Configure your own Groq and Tavily credentials, as required.
5. Verify the memory configuration and both agents' prompts.
6. Run a test query in the n8n chat and inspect the execution trace.

Credential names or references in an export do not provide access to the original credentials. Set up credentials securely in your own n8n instance.

## Screenshots

- `screenshots/workflow-overview.png` — overview of the two-agent workflow and its connected model, memory, and search tool.
- `screenshots/sample-execution.png` — example chat query and execution output.

## Security

Do not commit API keys, tokens, credential exports, or private information. Keep credentials configured inside n8n.

## Limitations

This repository's documentation is based on the screenshots. The exported workflow JSON has not yet been added, so the workflow is not fully reproducible from this repository until you add it.

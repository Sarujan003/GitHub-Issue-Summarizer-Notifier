# GitHub Issue Summarizer & Notifier

This project is an automated workflow built using **n8n** that streamlines the triage process for GitHub issues. It automatically analyzes new issues with an AI model, extracts key information, and sends a professionally formatted email notification to relevant stakeholders.

This system acts as an intelligent assistant, saving project managers and development teams significant time by providing instant summaries and categorizations of incoming issues.

---

## Key Features

-   **Automatic Triggering**: The workflow can run automatically the moment a new issue is created in the repository.
-   **AI-Powered Analysis**: Leverages a powerful AI chat model (like Google Gemini or OpenAI's GPT) to understand the content of an issue.
-   **Intelligent Summarization**: The AI generates a concise, one-sentence summary of the problem or request.
-   **Automatic Categorization**: Issues are automatically classified into categories like "Bug," "Feature Request," or "Question."
-   **Structured Data Handling**: The AI's response is returned as a clean JSON object, which is then parsed for robust data handling.
-   **Customizable Email Notifications**: Sends a detailed HTML email containing the issue title, AI summary, category, original reporter, and a direct link to the issue on GitHub.

---

## How It Works

The n8n workflow follows these logical steps:

1.  **Fetch Issue**: A trigger node waits for a new issue to be created in the specified GitHub repository.
2.  **Format Data**: A code node cleans up the initial data from the trigger, preparing it for the AI.
3.  **Analyze with AI**: The issue's title and description are sent to an AI Agent with a specific prompt, asking for a summary and a category in a JSON format.
4.  **Parse JSON**: An "Edit Fields" node parses the AI's raw text response to extract the `summary` and `category` into clean, usable fields.
5.  **Send Notification**: A "Send email" node uses the data from all previous steps to construct and send a detailed HTML email.

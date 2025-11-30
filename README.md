# Intelligent Email Automation Agent 🤖✉️

A production-ready **Intelligent Email Automation Agent** built using **LangGraph** to replace linear workflows with a dynamic, graph-based system for email sorting and response generation.

## 📌 Project Overview
This agent models complex decision-making processes to handle high volumes of incoming emails. It autonomously classifies emails (e.g., spam, urgent, general) and executes specialized workflows, such as drafting personalized responses for high-priority senders or filtering spam.

**Key Objectives:**
- Implement robust **State Management** to track email status and conversation history.
- Design **Conditional Edges** for dynamic routing based on LLM classification.
- Automate secure email drafting and sending via an integrated API.

## 🏗️ Architecture & Features
The agent utilizes a cyclic graph with the following key nodes and logic:

-   **EmailState:** The central data structure holding the current email content, classification label, draft response, and sender details.
-   **Nodes:** Separate functions defined for: `read_email`, `classify_email`, `draft_response`, and `send_email`.
-   **Conditional Routing:** After the `classify_email` node, the graph uses conditional logic to route the state to:
    -   `draft_response` (if urgent/important).
    -   `send_email` (if a draft is ready).
    -   End the graph (if spam or processed).
-   **LLM Integration:** Used for zero-shot email classification and context-aware response drafting.

## 🛠️ Tech Stack
-   **Framework:** LangGraph
-   **Language:** Python
-   **Libraries:** LangChain (LLMs), Langfuse (for optional observability), SMTP/Gmail API
-   **Concepts:** Finite State Machines, Conditional Logic, State Persistence

## 🚀 Usage Example
The agent processes a batch of emails and decides the next action for each:

1. **Input:** New email arrives.
2. **Node 1 (`classify_email`):** LLM determines the email is 'Urgent Support Request'.
3. **Edge Logic:** Graph routes the state to the `draft_response` node (Conditional Edge triggered).
4. **Node 2 (`draft_response`):** LLM generates a personalized response acknowledging the urgency.
5. **Edge Logic:** Graph routes the state to the `send_email` node.
6. **Output:** Personalized email response is automatically sent.

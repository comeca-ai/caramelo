# Caramelo - The Brazilian Boardy

Caramelo is a Brazilian version of [Boardy](https://www.boardy.ai/), designed to act as a "super connector" AI agent. It interacts with users via WhatsApp, understands their business context, and helps them with networking, strategy, and introductions.

## Features

- **WhatsApp Integration**: Communicates directly with users through WhatsApp.
- **Contextual Memory**: Stores user details (name, company, priority, conversation stage) in Redis.
- **Intelligent Routing**: Uses Anthropic's Claude 3.5 Sonnet to route conversations to specialized agents:
  - **Profiler**: Collects user information and business context.
  - **Qualifier**: Deep dives into user priorities (Customers, Hiring, Fundraising).
  - **Synthesizer**: Summarizes the user's problem.
  - **NextSteps**: Proposes practical actions and connections.
  - **Collector**: Gathers contact details (LinkedIn, Email).
- **"Caramelo" Persona**: Friendly, direct, "stray dog of the BR tech ecosystem" persona (using the 🐕 emoji).

## Architecture

The project is implemented as an **n8n workflow** (`caramelo-workflow-n8n.json`).

### Key Components

1.  **Webhook**: Receives messages from WhatsApp.
2.  **Redis**: Persists conversation state and user memory.
3.  **Anthropic (Claude 3.5 Sonnet)**: Powers the logic for routing and generating responses.
4.  **WhatsApp API**: Sends responses back to the user.

## Prerequisites

To run this workflow, you need:

1.  **n8n**: An instance of n8n (self-hosted or cloud).
2.  **Redis**: A Redis instance for memory storage.
3.  **Anthropic API Key**: For Claude 3.5 Sonnet.
4.  **WhatsApp Business API**: Credentials (Phone Number ID, Access Token) configured in n8n.

## How to Use

1.  Import the `caramelo-workflow-n8n.json` file into your n8n instance.
2.  Configure the credentials for:
    - Redis
    - Anthropic
    - WhatsApp
3.  Set up the WhatsApp Webhook URL to point to your n8n webhook node.
4.  Start the workflow.

## Project Goal

The objective is to create a Brazilian-adapted version of Boardy, acting as a helpful and well-connected assistant for the Brazilian tech ecosystem.

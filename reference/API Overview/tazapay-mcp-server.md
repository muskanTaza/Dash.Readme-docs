---
title: Tazapay MCP Server
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Overview

The TazaPay MCP Server is a Go-based server that integrates with the Anthropic‘s MCP (Model Context Protocol) server to provide payment processing tools via AI agents and LLM. It exposes several tools that allow AI assistants to interact with Tazapay's payment infrastructure, including currency exchange rates, payment link generation, and account balance retrieval. 

Many more such tools are planned to be added in our Open-source Repo. Check it out here: <https://github.com/tazapay/tazapay-mcp-server>

# Use Cases

**Automated Payment Link Generator**

Build agents that generate and send payment links on demand—for example, after order confirmation or customer request—without manual dashboard usage.

**Real-Time Balance Monitoring Tools**

Create agents that fetch and track account balances across Tazapay accounts to trigger alerts, pause payouts, or notify finance teams.

**Beneficiary Onboarding Workflows**

Streamline beneficiary creation by integrating with your CRM or HR systems to auto-register vendors, partners, or employees in Tazapay.

**Intelligent Payout Systems**

Set up autonomous agents that initiate payouts based on predefined rules—like payroll cycles, vendor invoices, or refund requests—minimizing manual errors.

### **Other Agentic Integration Scenarios**

- **Sales Tools→** Auto-send Payment Link after quote approval
- **Ops Tool →** Monitor low balance and auto-notify teams via Slack
- **HR System →** Auto-create Tazapay beneficiary during employee onboarding
- **Refund Assistant →** Detect failed orders and trigger payouts to customer account

And the list of use cases goes on as we add more and more tools to automate and have better access to our Tazapay API’s.

# Available Tools

### 1. FX Tool (`tazapay_fetch_fx_tool`)

**Purpose**: Retrieves foreign exchange rates between two currencies.

**Parameters**:

- `from`: Source currency (3-letter code, e.g., USD)
- `to`: Target currency (3-letter code, e.g., INR)
- `amount`: Amount to convert (numeric value)

**Response**: Returns the exchange rate and converted amount.

### 2. Payment Link Tool (`generate_payment_link_tool`)

**Purpose**: Generates a payment link for customers.

**Parameters**:

- `invoice_currency`: Currency for the invoice
- `payment_amount`: Amount to be paid
- `customer_name`: Full name of the customer
- `customer_email`: Email address of the customer
- `customer_country`: Country of the customer
- `transaction_description`: Description of the transaction

**Response**: Returns a payment URL that can be shared with customers.

### 3. Balance Tool (`tazapay_fetch_balance_tool`)

**Purpose**: Retrieves account balances.

**Parameters**:

- `currency`: Optional currency filter (3-letter code, e.g., USD)

**Response**: Returns all balances or the balance for the specified currency.

# Setting Up

Choose one of the setup method to proceed. You can use Docker image (recommended) or build Go app from source.

## **Prerequisites**

Ensure the following tools are installed before setup:

- Go 1.24+ / Docker Desktop App
- An IDE or tool that supports MCP (e.g., Claude Desktop, GitHub Copilot, Cursor IDE)
- Tazapay API Key and secret Key

## For Docker Build

- Ensure Docker is installed on your desktop
- Pull the Following Docker Image from dockerhub into your local machine
  ```bash
  docker pull tazapay/tazapay-mcp-server:latest
  ```
- Add the following to your `claude_desktop_config.json`:
  ```json
  {
    "mcpServers": {
      "Tazapay-Docker-Server": {
        "command": "docker",
        "description": "MCP server to integrate Tazapay API's and payments solutions.",
        "args": [
          "run","--rm","-i",
          "-e","TAZAPAY_API_KEY",
          "-e","TAZAPAY_API_SECRET",
          "tazapay/tazapay-mcp-server:latest"
        ],
        "env": {
          "TAZAPAY_API_KEY": "your_tazapay_api_key",
          "TAZAPAY_API_SECRET": "your_tazapay_api_secret"
        }
      }
    }
  }
  ```
- Now you are ready to interact with LLM to take care of operations with your Tazapay account.

## For Local Build

- Identify your Home directory
  ```bash
  echo $HOME
  ```
- Add a `.tazapay-mcp-server.yaml` config file in your home directory with the following content:
  ```yaml
  TAZAPAY_API_KEY:
  						"your_api_key"
  TAZAPAY_API_SECRET:
              "your_api_secret"
  ```
- Verify that the file '.tazapay-mcp-server.yaml' is added to your home directory.
  ```bash
  [ -f "$HOME/.tazapay-mcp-server.yaml" ] && echo "Config file found." || echo "Config file missing at $HOME/.tazapay-mcp-server.yaml"
  ```
- Clone Repo and Build Locally
  ```bash
  git clone https://github.com/tazapay/tazapay-mcp-server.git
  cd tazapay-mcp-server
  go build -o tazapay-mcp-server ./cmd/server
  ```
    The binary `tazapay-mcp-server` will be available post build.
- Now in Claude Desktop,
  - Go to `Settings > Developer > Edit Config`
  - Add the following to your `claude_desktop_config.json`:
  ```json
  {
    "mcpServers": {
      "Tazapay-mcp-server": {
        "command": "/absolute/path/to/repo/tazapay-mcp-server",
        "description": "MCP server to integrate Tazapay API's and payments solutions."
      }
    }
  }
  ```
- Now you are ready to interact with LLM to take care of operations with your Tazapay account.

# **Integration With other popular IDE**

## **GitHub Copilot Chat in VS code**

- Navigate to: **Settings > Features > Chat > Enable MCP**
- Now add the given json file in **`settings.json`**
  ```json
  {
    "mcp": {
      "inputs": [
      {
        "type": "promptString",
        "id": "tazapay_api_key",
        "description": "Tazapay API Key ",
        "password": false
      },
      {
        "type": "promptString",
        "id": "tazapay_api_secret",
        "description": "Tazapay API Secret",
        "password": true
      }
      ],
      "servers": {
        "Tazapay-mcp-Server": {
        "command": "docker",
        "description": "MCP server to integrate Tazapay API's and payments solutions.",
        "args": [
          "run","--rm","-i",
          "-e","TAZAPAY_API_KEY",
          "-e","TAZAPAY_API_SECRET",
          "tazapay/tazapay-mcp-server:latest"
        ]
       }
      }
    }
  }
  ```
- Configure MCP tools via the **gear icon** in the Chat tab.

## **Cursor IDE**

- Go to: **Settings > MCP > Add New Global MCP Server**
- Paste the JSON configuration from above and all tools are ready to use within the chat.

# Example Prompts

Some of the Examples usage prompts you can give to AI agents to use MCP server.

- This prompt will fetch the balance for all the currencies. Internally triggering the `fetch_balance_prompt`.
  ```
  What's the balance status of my account.
  ```
- Retrieve Real time FX rates and have a certain workflow attach to it.
  ```
  Fetch the current USD to INR exchange rate. If the rate is above 83.50, 
  generate a sharable Tazapay payment link for ₹10,000 and to be send to the Suyash at suyash@email.com. 
  ```
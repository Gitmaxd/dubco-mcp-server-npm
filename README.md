# Unofficial dubco-mcp-server

[![npm version](https://img.shields.io/npm/v/dubco-mcp-server.svg)](https://www.npmjs.com/package/dubco-mcp-server)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Node.js Version](https://img.shields.io/node/v/dubco-mcp-server)](https://nodejs.org/)

A Model Context Protocol (MCP) server for creating and managing [Dub.co](https://dub.co) short links (unofficial). This server enables AI assistants to create, update, and delete short links through the Dub.co API.

## 🚀 Features

- Create custom short links with your Dub.co domains
- Update existing short links
- Delete short links
- Seamless integration with AI assistants through the Model Context Protocol

## 📋 Prerequisites

- Node.js 16.0.0 or higher
- A Dub.co account with API access
- An API key from the [Dub.co dashboard](https://app.dub.co/settings/api)

## 💻 Installation

### Global Installation

```bash
npm install -g dubco-mcp-server
```

### Local Installation

```bash
npm install dubco-mcp-server
```

### Direct Usage with npx

```bash
npx dubco-mcp-server
```

## ⚙️ Configuration

This MCP server requires a Dub.co API key to function. You can get your API key from the [Dub.co dashboard](https://app.dub.co/settings/api).

Set the API key as an environment variable:

```bash
export DUBCO_API_KEY=your_api_key_here
```

For persistent configuration, add this to your shell profile (e.g., `.bashrc`, `.zshrc`):

```bash
echo 'export DUBCO_API_KEY=your_api_key_here' >> ~/.zshrc
```

## 🖥️ Cursor IDE Setup

Cursor IDE provides native support for MCP servers. Follow these steps to set up the dubco-mcp-server in Cursor:

### Step 1: Install Cursor IDE

If you haven't already, download and install [Cursor IDE](https://cursor.sh/) (version 0.4.5.9 or later).

### Step 2: Open Cursor Settings

1. Open Cursor IDE
2. Click on the gear icon in the bottom left corner, or use the keyboard shortcut `Cmd+,` (Mac) or `Ctrl+,` (Windows/Linux)
3. Navigate to the Features section
4. Scroll down to find the "MCP Servers" section

### Step 3: Add the MCP Server

1. Click on "+ Add new MCP server"
2. In the dialog that appears:
   - **Name**: Enter "Dub.co MCP Server" (or any name you prefer)
   - **Type**: Select "command" from the dropdown
   - **Command**: Enter `env DUBCO_API_KEY=your_api_key_here npx -y dubco-mcp-server`
     (Replace `your_api_key_here` with your actual Dub.co API key)
3. Click "Save" to add the server

### Step 4: Verify the Connection

After adding the MCP server, you should see a green status indicator next to the server name. If it shows a red or yellow status, try:

1. Checking that your API key is correct
2. Restarting Cursor IDE
3. Verifying that Node.js (16.0.0+) is properly installed

### Step 5: Using the Server

The dubco-mcp-server provides tools that can be used with Cursor's AI features:

1. Open Cursor's Composer or Agent mode (MCP only works in these modes)
2. Explicitly instruct the AI to use the Dub.co tools (create_link, update_link, delete_link)
3. Accept the tool usage prompts when they appear

## 🔧 Usage with MCP

This server provides tools that can be used by AI assistants through the Model Context Protocol. To use it with an MCP-compatible AI assistant, add it to your MCP configuration.

### MCP Configuration Example

```json
{
  "mcpServers": {
    "dubco": {
      "command": "npx",
      "args": ["-y", "dubco-mcp-server"],
      "env": {
        "DUBCO_API_KEY": "your_api_key_here"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### Available Tools

#### create_link

Create a new short link on Dub.co.

**Parameters:**

```json
{
  "url": "https://example.com",
  "key": "optional-custom-slug",
  "externalId": "optional-external-id",
  "domain": "optional-domain-slug"
}
```

**Example:**

```json
{
  "url": "https://github.com/gitmaxd/dubco-mcp-server-npm",
  "key": "dubco-mcp"
}
```

#### update_link

Update an existing short link on Dub.co.

**Parameters:**

```json
{
  "linkId": "link-id-to-update",
  "url": "https://new-destination.com",
  "domain": "new-domain-slug",
  "key": "new-custom-slug"
}
```

**Example:**

```json
{
  "linkId": "clwxyz123456",
  "url": "https://github.com/gitmaxd/dubco-mcp-server-npm/releases"
}
```

#### delete_link

Delete a short link on Dub.co.

**Parameters:**

```json
{
  "linkId": "link-id-to-delete"
}
```

**Example:**

```json
{
  "linkId": "clwxyz123456"
}
```

## 🔍 How It Works

The server connects to the Dub.co API using your API key and provides a standardized interface for AI assistants to interact with Dub.co through the Model Context Protocol. When a tool is called:

1. The server validates the input parameters
2. It sends the appropriate request to the Dub.co API
3. It processes the response and returns it in a format that the AI assistant can understand

## 🛠️ Development

### Building from Source

```bash
git clone https://github.com/gitmaxd/dubco-mcp-server-npm.git
cd dubco-mcp-server-npm
npm install
npm run build
```

### Running in Development Mode

```bash
npm run dev
```

## 📝 License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- [Dub.co](https://dub.co) - The URL shortener service
- [Dub.co API Documentation](https://dub.co/docs/api-reference/introduction)
- [Model Context Protocol](https://github.com/anthropics/model-context-protocol) - Learn more about MCP

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 👨‍💻 Created By

This unofficial Dub.co MCP Server was created by [GitMaxd](https://github.com/gitmaxd) ([@gitmaxd](https://twitter.com/gitmaxd) on X).

This project was developed as a learning exercise to understand the Model Context Protocol and how to build MCP servers. I chose Dub.co as the integration target because of its straightforward API and practical utility, making it an ideal candidate for a learning project.

While I have no official affiliation with Dub.co, I highly recommend their service for both manual and automated short link creation. Their API is well-documented and easy to work with, making it perfect for this kind of integration.

If you find this project helpful or have suggestions for improvements, feel free to reach out or contribute to the repository. Happy link shortening!

# dubco-mcp-server

[![npm version](https://img.shields.io/npm/v/dubco-mcp-server.svg)](https://www.npmjs.com/package/dubco-mcp-server)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Node.js Version](https://img.shields.io/node/v/dubco-mcp-server)](https://nodejs.org/)

A Model Context Protocol (MCP) server for creating and managing [Dub.co](https://dub.co) short links. This server enables AI assistants to create, update, and delete short links through the Dub.co API.

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

## 🔧 Usage with MCP

This server provides tools that can be used by AI assistants through the Model Context Protocol. To use it with an MCP-compatible AI assistant, add it to your MCP configuration.

### MCP Configuration Example

```json
{
  "mcpServers": {
    "dubco": {
      "command": "npx",
      "args": ["dubco-mcp-server"],
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

# dubco-mcp-server

A Model Context Protocol (MCP) server for creating and managing [Dub.co](https://dub.co) short links.

## Installation

```bash
npm install -g dubco-mcp-server
```

Or use it directly with npx:

```bash
npx dubco-mcp-server
```

## Configuration

This MCP server requires a Dub.co API key to function. You can get your API key from the [Dub.co dashboard](https://app.dub.co/settings/api).

Set the API key as an environment variable:

```bash
export DUBCO_API_KEY=your_api_key_here
```

## Usage with MCP

This server provides the following tools:

### create_link

Create a new short link on dub.co.

```json
{
  "url": "https://example.com",
  "key": "optional-custom-slug",
  "externalId": "optional-external-id",
  "domain": "optional-domain-slug"
}
```

### update_link

Update an existing short link on dub.co.

```json
{
  "linkId": "link-id-to-update",
  "url": "https://new-destination.com",
  "domain": "new-domain-slug",
  "key": "new-custom-slug"
}
```

### upsert_link

Create or update a short link on dub.co.

```json
{
  "url": "https://example.com",
  "key": "optional-custom-slug",
  "externalId": "optional-external-id",
  "domain": "optional-domain-slug"
}
```

### delete_link

Delete a short link on dub.co.

```json
{
  "linkId": "link-id-to-delete"
}
```

## License

ISC

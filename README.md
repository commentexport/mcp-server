# Combly MCP

Find, search and export YouTube, TikTok and Instagram comments, and draw fair giveaway winners.

get_account reads your plan and usage. load_comments and search_comments read a post's comments and find them by keyword, author, date, questions or links; export_comments returns CSV. draw_giveaway picks random winners under your rules and publishes a winner page; list_giveaways and get_giveaway read past draws. Loads and draws use your plan's monthly limits.

## Remote MCP

Use **https://commentexport.app/mcp** in a client that supports remote MCP with OAuth. Sign in to Combly (email code or Google) and approve the connection. Clients without OAuth can send a Combly API key instead: `Authorization: Bearer cmb_live_…` (create one in the Combly dashboard).

## Claude Desktop and other stdio clients

Requires Node.js 22 or newer. Add this configuration:

```json
{
  "mcpServers": {
    "combly": {
      "command": "npx",
      "args": ["-y", "combly-mcp"]
    }
  }
}
```

Or install the `.mcpb` file from [Releases](https://github.com/commentexport/mcp-server/releases) in your desktop client's Extensions settings. The connector opens your browser for sign-in.

## Privacy and permissions

The consent screen lists what the connection can do. Your Combly sign-in and any platform passwords are never requested by this package. The pinned [mcp-remote](https://www.npmjs.com/package/mcp-remote) bridge handles OAuth, PKCE and local token storage and connects only to the fixed endpoint above. OAuth tokens are stored locally by mcp-remote and should be treated as credentials. Privacy policy: https://commentexport.app/privacy

## Development and publishing

Run `npm ci` and `npm test`. GitHub Actions publishes a new package version using the organization's `NPM_TOKEN` secret, then builds and releases the desktop bundle. Keep package.json, manifest.json, server/config.json and server.json versions aligned.

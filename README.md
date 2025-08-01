# SessionBase MCP Server

An MCP (Model Context Protocol) server that provides access to SessionBase CLI functionality through AI assistants.

## Features

This MCP server wraps the SessionBase CLI and provides the following tools:

- **`list_sessions`** - List local chat sessions from Claude Code, Gemini CLI, and Amazon Q Chat
- **`upload_session`** - Upload chat sessions to SessionBase
- **`login`** - Authenticate with SessionBase 
- **`whoami`** - Show current authentication status
- **`logout`** - Log out from SessionBase

## Prerequisites

- Node.js >= 18
- SessionBase CLI installed and available in PATH
- An MCP-compatible client (like Claude Desktop)

## Installation

### 1. Install SessionBase CLI

First, make sure you have the SessionBase CLI installed. Check the [SessionBase documentation](https://github.com/sessionbase/sessionbase) for installation instructions.

### 2. Install this MCP Server

```bash
# Clone the repository
git clone https://github.com/sessionbase/mcp.git
cd mcp

# Install dependencies
npm install

# Build the project
npm run build
```

### 3. Configure your MCP client

For Claude Desktop, add this to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "sessionbase": {
      "command": "node",
      "args": ["/path/to/sessionbase-mcp/dist/index.js"]
    }
  }
}
```

## Usage

Once configured, you can use these tools through your MCP client:

### List Sessions
```
Please list my local chat sessions
```

### Upload a Session
```
Upload my most recent Claude Code session to SessionBase
```

### Check Authentication
```
Check if I'm logged into SessionBase
```

## Tool Reference

### `list_sessions`
Lists local chat sessions from supported platforms.

**Parameters:**
- `claude` (optional): Filter for Claude Code sessions only
- `gemini` (optional): Filter for Gemini CLI sessions only  
- `qchat` (optional): Filter for Amazon Q Chat sessions only
- `path` (optional): Filter sessions by specific directory path
- `global` (optional): Include sessions from all projects

### `upload_session`
Uploads a chat session to SessionBase.

**Parameters:**
- `filePath` (optional): Path to session file (.json or .jsonl)
- `claude` (optional): Upload most recent Claude Code session
- `gemini` (optional): Upload most recent Gemini CLI session
- `qchat` (optional): Upload most recent Amazon Q Chat session
- `private` (optional): Make the session private
- `title` (optional): Session title
- `tags` (optional): Comma-separated tags
- `summary` (optional): Session summary

### `login`
Authenticate with SessionBase.

**Parameters:**
- `token` (optional): Provide token directly (bypasses browser login)

### `whoami`
Show current authentication status and user information.

### `logout`
Log out from SessionBase.

## Development

```bash
# Run in development mode with hot reload
npm run dev

# Build for production
npm run build

# Start the built server
npm start
```

## Troubleshooting

1. **"sessionbase command not found"**: Make sure the SessionBase CLI is installed and in your PATH
2. **"Permission denied"**: Ensure the built files have execute permissions (`chmod +x dist/*.js`)
3. **Authentication issues**: Run `sessionbase login` directly in your terminal first

## License

MIT

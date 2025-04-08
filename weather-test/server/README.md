## Set up your environment

First, let’s install uv and set up our Python project and environment:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Make sure to restart your terminal afterwards to ensure that the uv command gets picked up.

Now, let’s create and set up our project:

```bash
# Create a new directory for our project
uv init weather
cd weather

# Create virtual environment and activate it
uv venv
source .venv/bin/activate

# Install dependencies
uv add "mcp[cli]" httpx

# Create our server file
touch weather.py
```

Now let’s dive into building your server.

## Connect to client

## Setup Claude Dekstop

First, make sure you have Claude for Desktop installed. You can install the latest version here. If you already have Claude for Desktop, make sure it’s updated to the latest version.

We’ll need to configure Claude for Desktop for whichever MCP servers you want to use. To do this, open your Claude for Desktop App configuration at ~/Library/Application Support/Claude/claude_desktop_config.json in a text editor. Make sure to create the file if it doesn’t exist.

For example, if you have VS Code installed:

```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

You’ll then add your servers in the mcpServers key. The MCP UI elements will only show up in Claude for Desktop if at least one server is properly configured.

In this case, we’ll add our single weather server like so:

```bash
{
    "mcpServers": {
        "weather": {
            "command": "uv",
            "args": [
                "--directory",
                "/ABSOLUTE/PATH/TO/PARENT/FOLDER/weather",
                "run",
                "weather.py"
            ]
        }
    }
}
```

```json
{
    "mcpServers": {
        "weather": {
            "command": "uv",
            "args": [
                "--directory",
                "/ABSOLUTE/PATH/TO/PARENT/FOLDER/weather",
                "run",
                "weather.py"
            ]
        }
    }
}
```
You may need to put the full path to the uv executable in the command field. You can get this by running which uv on MacOS/Linux or where uv on Windows.

Make sure you pass in the absolute path to your server.

This tells Claude for Desktop:

There’s an MCP server named “weather”
To launch it by running uv --directory /ABSOLUTE/PATH/TO/PARENT/FOLDER/weather run weather.py
Save the file, and restart Claude for Desktop.

### Using VSCode Chat Agent Mode

1. Open the command palette (Ctrl+Shift+P or Cmd+Shift+P on Mac).
2. Type "Chat" and select "Chat: Open Chat".
3. Choose Agent mode on dropdown.
4. Select the MCP server: "weather", then choose the "weather" from claude dekstop.
5. The agent will connect to the server and you can start interacting with it.
6. Type "Get weather for New York" and hit enter.
7. The agent will respond with the current weather for New York.

more visit <https://code.visualstudio.com/blogs/2025/04/07/agentMode>

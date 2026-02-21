Client config

{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\src\\AI\\MCP_Servers\\weather",
        "run",
        "weather.py"
      ]
    }
  },
  "preferences": {
    "sidebarMode": "chat",
    "coworkScheduledTasksEnabled": false
  }
}


Your config contains something like:

- command: uv.exe

- args: run weather.py

When Claude starts a session and the connector is enabled, it:

1. Spawns a new process

2. Runs uv --directory ... run weather.py

3. Connects to it over stdio

4. Performs MCP handshake

5. Keeps it alive while needed

So Claude is the one running your server process.
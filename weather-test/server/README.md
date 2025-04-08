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
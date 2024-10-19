# Cartesia CalHacks Workshop

This repository contains the code for a voice agent that can be used to interact with the [Cartesia](https://cartesia.ai) API. The agent is built using [pipecat-ai](https://github.com/pipecat-ai/pipecat-ai), a framework for building voice agents. (Once you've got the hang of this project, check out the Pipecat examples for ways to build an even more sophisticated voice agent!)

## Run the AI voice agent

### Prerequisites

#### Get API keys

1. Go to [Daily](https://daily.co) and create a room and an API key. (When you press “Sign Up”, click “Daily Video” instead of “Daily Bots”.)
2. Go to [the OpenAI platform](http://platform.openai.com) and create an API key.
3. Go to [the Cartesia playground](http://play.cartesia.ai) and create an API key.
4. Paste the API keys into a new `.env` file created by copying `.env.example` to `.env`.

#### Install Python dependencies

> [!TIP]
> Before you run this command, make sure you have Python installed. You can download it from [python.org](https://www.python.org/downloads/).

Run this command in your terminal to install the dependencies:

```bash
pip install cartesia pipecat-ai[cartesia,openai,silero,daily] ffmpeg-python python-dotenv
```

Alternatively, you can also install the dependencies using `uv`, which may be faster. First, install `uv` with `pip install uv`. Then, run this command in your terminal:

```bash
uv sync
```

#### Run the agent

Run this command in your terminal to start the agent. Make sure you're in the root of the project:

```bash
python3 main.py
```

Finally, open up the room URL in your browser, and you should be able to talk to the agent!

Try modifying the system prompt (which starts with `"You are a helpful LLM in a WebRTC call..."`) in `main.py` to see how the agent's behavior changes!

Some fun prompts you could try:

- `You are a pirate in a WebRTC call. Respond to everything the user says like a pirate.`
- `You are a overzealous salesman selling used Honda Civics in a WebRTC call. Whatever the user says, guide them towards buying a used Honda Civic.`

## Project Structure

### `cartesia-quickstart.py`

> [!TIP]
> This file is not used in the voice agent, it's just a quick example of how to use the Cartesia API to generate some speech and save it to an audio file you can play on your computer.

If you want to use the Cartesia API directly to generate speech, you can use this file as a starting point. It's sourced from the [Cartesia Python Quickstart Guide](https://docs.cartesia.ai/get-started/make-an-api-request).

### `.env.example` (you should copy this file to `.env`)

> [!TIP]
> Copy this file to `.env` and fill in the values to get started.

This file stores all the keys we got from Daily, OpenAI, and Cartesia, and sets the Cartesia voice ID to use. (You can get your own voice ID from the Voice Library in the Cartesia playground!)

### `main.py`

This file contains the main logic of the agent. It connects to the Daily room we created earlier and waits for someone to join so it can talk to them.

### `runner.py`

This file contains some code to help configure the agent with the API keys in `.env` so it can connect to the Daily room we created earlier. You probably don't need to change anything here.

### `pyproject.toml`, `.python-version`, `uv.lock`

These files are used to manage the dependencies of the project. You probably don't need to change anything here.

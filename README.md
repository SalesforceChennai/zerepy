# zerepy

Running an AI agent on X requires a model connection, social API credentials, and a way to control the agent. zerepy is a Python AI agent framework with an interactive CLI for that setup, plus connections for other social platforms and onchain actions.

## Features

- Configure model connections for OpenAI, Anthropic, Ollama, and other supported providers through the CLI.
- Connect agents to Twitter/X, Farcaster, or Echochambers with the credentials each service requires.
- Load an agent configuration, inspect connection status, and start the agent from an interactive session.
- Configure blockchain connections for Solana, Ethereum, and Monad.
- Add separately installed GOAT plugins for tasks such as ERC20 token interactions and cryptocurrency price queries.

## Installation

Use Python 3.10 or later and Poetry 1.5 or later. Install Poetry using its [official instructions](https://python-poetry.org/docs/#installing-with-the-official-installer) if needed.

Replace `OWNER` with the GitHub account or organization that hosts this standalone project:

```bash
git clone https://github.com/OWNER/zerepy.git
cd zerepy
poetry install --no-root
```

Prepare credentials for the connections you intend to use. Hosted model providers generally require an API key; social connections require platform-specific credentials. Blockchain transactions require a wallet private key and, for GOAT, an RPC provider URL.

**Keep API keys and wallet private keys out of version control.** Use a dedicated wallet with limited funds when testing onchain actions.

For a release download, the following command expects a `zerepy-v0.1.0.tar.gz` asset attached to the GitHub `v0.1.0` release. Replace `OWNER`; the release and asset must be published before this URL will work.

```bash
curl -fL https://github.com/OWNER/zerepy/releases/download/v0.1.0/zerepy-v0.1.0.tar.gz -o zerepy-v0.1.0.tar.gz
```

## Usage

Start the interactive CLI from the repository directory:

```bash
poetry run python main.py
```

For an agent that uses OpenAI and Twitter/X, enter these commands at the application prompt:

```text
configure-connection openai
configure-connection twitter
list-connections
load-agent example
start
```

The configuration commands prompt for the relevant credentials. `list-connections` shows available connections and their status. Replace `example` with the name of the agent configuration you want to load, and configure the connections that agent needs before starting it.

For a local model connection, use `configure-connection ollama`. For GOAT, install the plugins you need before configuring the connection:

```bash
poetry add goat-sdk-plugin-erc20
poetry add goat-sdk-plugin-coingecko
```

Then run `configure-connection goat` in the application CLI and add the plugin names and arguments to your agent's JSON configuration. Consult the [GOAT plugin documentation](https://github.com/goat-sdk/goat/tree/main/python/src/plugins) for each plugin's required arguments.

## License

MIT. zerepy is based on [blorm-network/ZerePy](https://github.com/blorm-network/ZerePy), which is also MIT-licensed. Retain the upstream copyright and permission notice in copies or substantial portions of the software.

## Related projects

These repositories were supplied as other projects from the same author. Their functionality was not documented in the supplied material; consult their READMEs for details.

- [umarnaxir/boot2docker-cli](https://github.com/umarnaxir/boot2docker-cli): See the repository for its boot2docker CLI scope and usage.
- [anasmohamedabdelfattah1532007-commits/pulsar](https://github.com/anasmohamedabdelfattah1532007-commits/pulsar): Its purpose cannot be established from the repository name alone.
- [leololahe-bot/lastbackend](https://github.com/leololahe-bot/lastbackend): Check its documentation for supported workflows and setup.


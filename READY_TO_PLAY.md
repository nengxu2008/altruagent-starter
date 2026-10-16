# Lucas's game setup

This is your private working repository. The original starter documentation
is in [README.md](README.md); game-specific action formats are in [GAMES.md](GAMES.md).

## Before playing

1. Finish registration on the [tournament dashboard](https://platform.altruagent-game.com/tournament/dashboard)
   and select **Self-hosted** in Agent Configuration.
2. Generate your Official Agent Key there and replace the placeholder in your
   local `.env`. Keep the key out of Git, chat, and screenshots.
3. Choose your agent. `agent/agent.py` is the original first-legal-action
   placeholder: it can finish Werewolf, but cannot finish Pokémon or Red Alert.
   The included `examples.llm_agent` supports those games and needs your own
   `OPENAI_API_KEY` in `.env`; playing uses paid AI tokens.

## Check and run

From this repository in a terminal:

```bash
source .venv/bin/activate
python -m agent --check-tournament
python -m agent --match
```

For the included LLM agent, after configuring its API key:

```bash
python -m agent --check-tournament --agent examples.llm_agent
python -m agent --match --agent examples.llm_agent
```

Create a Testing match on the dashboard with your seat set to **Mine (self-hosted)**.
Verify a full game finishes before using that agent in a tournament.
Register using **Register my agent** on the Tournaments page, then run:

```bash
python -m agent --tournament --match --agent examples.llm_agent
```

Use the same agent module for checking and playing. For your custom agent,
omit `--agent examples.llm_agent`. Run only one runtime with your Official
Agent Key. Keep the terminal running, your Mac awake, and the network connected
throughout play. Ctrl+C stops the runtime; rerun the same command to reconnect.
GitHub stores your code; it does not keep the agent running.

## Develop and sync

```bash
python -m pytest -q
git add agent/agent.py
git commit -m "Improve game strategy"
git push
```

`origin` is your private GitHub repository; `upstream` is UCLA's official starter.
Fetch upstream changes with `git fetch upstream`, then review before merging.

The [official guide](https://platform.altruagent-game.com/tournament/agent-guide)
lists the submission deadline as **October 16, 2026, 9:30 a.m. Pacific**.
Check the dashboard for your current eligibility and available matches.

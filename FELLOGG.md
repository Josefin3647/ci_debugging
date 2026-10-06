# Fellogg

En rad per fel. Skriv medan du minns hur du gjorde.

| Nr | Vad stod i loggen? | Lokalt eller på GitHub? | Hur tog du reda på orsaken? | Hur löste du det? |
|----|--------------------|-------------------------|-----------------------------|-------------------|
| 1  | Invalid workflow file: yaml syntax on line 11 | GitHub | Loggen pekade på rad 11, men jag såg att indenteringen låg fel på rad 14. Jag kollade med en LLM som bekräftade felet. | Tog bort mellanslaget i indenteringen på rad 14. |
| 2  | `uv sync --frozen`: Unable to find lockfile at `uv.lock`, but `--frozen` was provided | GitHub | Läste felmeddelandet som pekade ut att `uv.lock` inte fanns. Dubbelkollade sedan med en LLM som bekräftade. | La till `uv.lock` lokalt med `uv sync` och tog bort `uv.lock` från `.gitignore`. |
| 3  | F401 `os` imported but unused (`src/miniforecast/baseline.py:3:8`) | GitHub | Läste felmeddelandet i check som pekade ut `import os` som oanvänd i `baseline.py`. Dubbelkollade med en LLM som bekräftade. | Tog bort `import os` med det föreslagna `--fix`-kommandot `uv run ruff check src tests --fix`.|

Fortsätt tabellen med fler rader vid behov.

# Fellogg

En rad per fel. Skriv medan du minns hur du gjorde.

| Nr | Vad stod i loggen? | Lokalt eller på GitHub? | Hur tog du reda på orsaken? | Hur löste du det? |
|----|--------------------|-------------------------|-----------------------------|-------------------|
| 1  | Invalid workflow file: yaml syntax on line 11 | GitHub | Loggen pekade på rad 11, men jag såg att indenteringen låg fel på rad 14. Jag kollade med en LLM som bekräftade felet. | Tog bort mellanslaget i indenteringen på rad 14. |
| 2  | `uv sync --frozen`: Unable to find lockfile at `uv.lock`, but `--frozen` was provided | GitHub | Läste felmeddelandet som pekade ut att `uv.lock` inte fanns. Dubbelkollade sedan med en LLM som bekräftade. | La till `uv.lock` lokalt med `uv sync` och tog bort `uv.lock` från `.gitignore`. |
| 3  | F401 `os` imported but unused (`src/miniforecast/baseline.py:3:8`) | GitHub | Läste felmeddelandet i check som pekade ut `import os` som oanvänd i `baseline.py`. Dubbelkollade med en LLM som bekräftade. | Tog bort `import os` med det föreslagna `--fix`-kommandot `uv run ruff check src tests --fix`.|
| 4 | ruff format --check src tests: Would reformat: `src/miniforecast/baseline.py:4:1`, `tests/test_baseline.py:7:28` | GitHub | Läste felmeddelandet som pekade ut att  `baseline.py`och `test_baseline.py` inte följde ruffs formatering. Jag dubbelkollade med en LLM som bekräftade det. | Körde `uv run ruff format src tests` på `baseline.py`och `test_baseline.py`. |
| 5 | `uv run pytest` gav `ModuleNotFoundError: No module named numpy` i `src/miniforecast/features.py` | GitHub | Läste felmeddelandet som pekade ut `import numpy` i `features.py`. Kontrollerade beroenden i `pyproject.toml` och såg att `numpy` saknades. Bekräftade med hjälp av en LLM. | La till `numpy` med `uv add numpy`. |
| 6 | `uv run pytest` gav `AssertionError` på `tests/test_features.py::test_moving_average_window_two`: `assert [1.0, 1.67, 2.33] == [1.5, 2.5, 3.5]` | GitHub | Felmeddelandet visade att funktionen `moving_average([1, 2, 3, 4], 2)` gav för låga värden. Kunde inte själv tolka orsaken och tog hjälp av en LLM. Kontrollerade med en LLM att det var funktionen och inte själva testet av funktionen som var fel. | Ändrade `window + 1` till `window` i beräkningen av `kernel` i `moving_average` (`src/miniforecast/features.py`)för att summan skulle delas med antalet värden i fönstret (2 i testet). |

Fortsätt tabellen med fler rader vid behov.

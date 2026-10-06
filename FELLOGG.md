# Fellogg

En rad per fel. Skriv medan du minns hur du gjorde.

| Nr | Vad stod i loggen? | Lokalt eller på GitHub? | Hur tog du reda på orsaken? | Hur löste du det? |
|----|--------------------|-------------------------|-----------------------------|-------------------|
| 1  | Invalid workflow file: yaml syntax on line 11 | Github | Jag såg att indenteringen låg fel på rad 14 men osäker på om det var felet. Frågade en LLM som bekräftade. | Tog bort mellanslaget i indenteringen på rad 14 |
| 2  | uv sync --frozen: Unable to find lockfile at uv.lock, but -- frozen was provided | GitHub | Läste felmeddelandet och dubbelkollade med en LLM | La till uv.lock lokalt med uv sync och tog bort uv.lock från .gitignore |
| 3  |                    |                         |                             |                   |

Fortsätt tabellen med fler rader vid behov.

# Project Guidelines

## Architecture

- The backend is a FastAPI application in [src/app.py](src/app.py). It exposes the activities API, redirects `/` to the static UI, and stores activity data in memory.
- The browser client lives in [src/static/index.html](src/static/index.html), [src/static/app.js](src/static/app.js), and [src/static/styles.css](src/static/styles.css). Keep API changes and client changes aligned.
- Data resets whenever the server restarts. Do not introduce persistence unless the task explicitly requires it.

## Build and Test

- Install dependencies with `pip install -r requirements.txt`.
- Run the development server with `uvicorn src.app:app --reload --reload-include 'src/static/*'`.
- Run the test suite with `pytest`. Add backend tests under `tests/` when a change affects API behavior.
- The VS Code debug configuration in [.vscode/launch.json](.vscode/launch.json) uses the same Uvicorn entry point. Treat it as the source of truth over the older run command in [src/README.md](src/README.md).

## Conventions

- Preserve the existing activity-name and participant-email identifiers in API routes and responses unless the task requires a contract change.
- For frontend API calls, follow the existing `fetch`-based pattern and URL-encode dynamic path and query values.
- Use the exercise workflow in [.github/steps/](.github/steps/) for context on intended feature changes, especially frontend participant management and backend testing.
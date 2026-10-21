# Michelle Studio

A private "studio manager" for a freelance illustrator and brand designer. It tells Michelle what to do next instead of just storing information.

## Design principle ("Michelle's Law")

Every feature must answer: **does this reduce Michelle's thinking, or does it only store more information?** If it only stores, redesign it until it helps her decide or act.

- Every screen answers one question. Today: *What should I do right now?* Target Clients: *Who can I work with?* Portfolio: *What work should I show?*
- One source of truth. Status, last contact and next follow-up are **derived** from the interaction history and are never typed in.
- Mistakes must be cheap: every logged action has an undo toast, and interaction history is editable.
- Every input path (button, command bar, and later natural language) must end up calling the same action functions (`logOutreach`, `saveProjects`, etc.).

## What exists today

- **Today:** command bar, ranked suggested next actions, undo.
- **Target Clients:** directory of 30 dream clients, with a weighted 5-factor fit score (Alignment 35%, Budget 20%, Likelihood 15%, Excitement 15%, Strategic value 15%).
- **Portfolio Intelligence:** projects with services, industries, skills, confidence and commercial value, content status per channel, and a "Portfolio Sent" outreach action that links projects to clients.

## Running it

It's a single file with no build step. Open `index.html` in a browser.

**Storage:** inside Claude the app uses Claude's `window.storage`. Anywhere else, a small fallback at the top of `index.html` stores data in the browser's `localStorage` (keys prefixed `michelle-studio:`). Data is per-browser and per-device.

## Roadmap

1. Validate Portfolio with real projects
2. Process Library
3. Content Planner
4. Finance (decision support, e.g. "am I on pace for my goal?")
5. Weekly Review (pre-filled from existing data; asks only what needs reflection)
6. Later: real backend (e.g. Supabase) with login, then mobile and integrations

## Known items

- `[MS DIAGNOSTIC]` and `TEMP DIAGNOSTIC` console logging in `saveProjectForm` is temporary. Remove it once the project-save fix is confirmed in Michelle's live session.
- `saveClients()` now reports failure, but most callers don't check its return value yet (`saveProjectForm` does).
- Each company has one "Decision maker" field; the outreach method uses about three contacts per company.

## Contributing

- Create a branch, make your change, open a pull request. Don't commit to `main` directly.
- Keep workflows intact. Check a proposed feature against the design principle above before building it.
- The app is one large file for now. Splitting CSS and JS into separate files is a reasonable first refactor.
- This repository is private. It contains a real client list and business strategy.

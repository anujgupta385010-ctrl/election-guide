# Election Process Guide

An interactive, AI-powered web app that helps users understand the democratic election process — including phases, timelines, key terms, and a live Q&A assistant.

## Live Demo

Open `index.html` in any modern browser, or deploy to Firebase Hosting (see below).

## Features

- **Overview** — Six core election phases with step-by-step breakdowns (Candidate Filing → Primary → Campaign → Registration → Election Day → Counting)
- **Timeline** — Chronological milestone view with status indicators (completed / in progress / upcoming)
- **Glossary** — 18 searchable election terms, expandable on click
- **Ask the Guide** — AI-powered chat assistant (Claude API) that answers any election question in a clear, neutral, and accessible way

## Google Services Used

| Service | Purpose |
|---|---|
| **Firebase Hosting** | Global CDN deployment with security headers |
| **Firebase Analytics** | User behaviour tracking (tab views, phase selections, questions asked) |
| **Google Fonts API** | DM Sans + DM Serif Display typography |

### Analytics Events Tracked

| Event | Trigger | Parameters |
|---|---|---|
| `page_view` | App load | `page_title` |
| `tab_view` | User switches tab | `tab_name` |
| `phase_selected` | User clicks a phase card | `phase_title`, `phase_index` |
| `question_asked` | User sends a chat message | `question_text` (first 100 chars) |

> **Note:** For production, proxy API calls through a Firebase Cloud Function to keep your key secure.

## Testing

Manual test scenarios to verify core and edge case paths:

| Scenario | Expected result |
|---|---|
| Click each tab | Tab panel switches, `tab_view` event fires |
| Click all 6 phase cards | Detail panel updates, `phase_selected` event fires |
| Search glossary with valid term | Matching terms shown |
| Search glossary with no match | "No matching terms found" message shown |
| Submit empty chat input | Nothing happens, no API call |
| Submit chat with API offline | Fallback error message shown |
| Type 500+ characters in chat | Input capped at 500 characters |
| Click a timeline item | Description expands/collapses |

## Tech Stack

- Vanilla HTML, CSS, JavaScript — zero build dependencies
- Firebase Hosting + Firebase Analytics (Google Cloud)
- Google Fonts API (DM Serif Display + DM Sans)

## License

MIT


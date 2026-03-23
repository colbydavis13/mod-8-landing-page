# mod-8-landing-page

A minimal static "Hello World" landing page.

## Tech Stack

- **Frontend**: Plain HTML5 (single `index.html`)
- **Server (dev)**: Python 3 built-in HTTP server (`python3 -m http.server 5000`)
- **No build system, no package manager, no dependencies**

## Project Structure

```
/
├── index.html        # Main landing page
├── README.md
└── .github/
    └── workflows/    # Azure Static Web Apps CI/CD (not used in Replit)
```

## Running Locally (Replit)

The "Start application" workflow runs:
```
python3 -m http.server 5000 --bind 0.0.0.0
```
This serves the static files on port 5000.

## Deployment

Configured as a **static** deployment with `publicDir: "."`.

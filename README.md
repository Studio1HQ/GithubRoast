<div align="center">

<img src="https://raw.githubusercontent.com/Studio1HQ/Studio1HQ/main/assets/banners/GithubRoast.webp" alt="GitHub Commit Roast App with Nebius: A Flask app that roasts your commit history using Nebius AI" width="100%" />

<br />
<br />

# GitHub Commit Roast App with Nebius

### A Flask app that roasts your commit history using Nebius AI

A Flask app that fetches a repository's commits from the GitHub API and asks a Nebius AI Studio model for a humorous roast and advice on better commit practices.

<br />

[![Built by Studio1](https://img.shields.io/badge/Built_by_Studio1-f97316?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNjAgMTYwIiBmaWxsPSJub25lIj48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTAgMzVDMCAxNi42ODA3IDE0LjA3NDQgMS42NDg0NCAzMiAwLjEyNjk1M1YxNDFINTEuMDUyM0M1Mi40MzA4IDEzNy4zNDQgNTQuNzQ0NiAxMzMuNjg5IDU3Ljk5MzggMTMwLjAzM0M2MS4xNDQ2IDEyNi41MDggNjQuNjg5MiAxMjMuNDQgNjguNjI3NyAxMjAuODI5QzcyLjU2NjIgMTE4LjM0OSA3Ni4zNTY5IDExNi43ODIgODAgMTE2LjEyOVY4Ni43NTQ0Qzc1LjQ3MDggODcuOTI5MiA3MS4zODQ2IDg5LjY5MTkgNjcuNzQxNSA5Mi4wNDE1QzY0IDk0LjUyMjUgNjAuNzUwOCA5Ny40NiA1Ny45OTM4IDEwMC44NTRDNTYuNTM0NSAxMDIuNzIgNTUuMjU0NSAxMDQuNjU5IDU0LjE1MzkgMTA2LjY3MVYwSDEyNUMxNDQuMzMgMCAxNjAgMTUuNjY5OSAxNjAgMzVWMTI1QzE2MCAxNDQuMzMgMTQ0LjMzIDE2MCAxMjUgMTYwSDEyNFYxOEgxMDQuOTQ4QzEwMy41NjkgMjEuNjgxNiAxMDEuMjU1IDI1LjM2MjggOTguMDA2MiAyOS4wNDQ0Qzk0Ljg1NTQgMzIuNTk0MiA5MS4zMTA4IDM1LjY4NDEgODcuMzcyMyAzOC4zMTRDODMuNDMzOCA0MC44MTIgNzkuNjQzMSA0Mi4zODk2IDc2IDQzLjA0NzRWNzIuNjMwNEM4MC41MjkyIDcxLjQ0NzMgODQuNjE1NCA2OS42NzI0IDg4LjI1ODUgNjcuMzA1N0M5MiA2NC44MDc2IDk1LjI0OTIgNjEuODQ5MSA5OC4wMDYyIDU4LjQzMDdDOTkuNDY1NSA1Ni41NTEzIDEwMC43NDUgNTQuNTk4NiAxMDEuODQ2IDUyLjU3MjNWMTYwSDM1QzE1LjY3IDE2MCAwIDE0NC4zMyAwIDEyNVYzNVoiIGZpbGw9IiNmZmZmZmYiLz48L3N2Zz4K)](https://studio1hq.com)
[![Built with Nebius](https://img.shields.io/badge/Built_with_Nebius-141414?style=for-the-badge)](https://nebius.com)

[Nebius docs](https://docs.tokenfactory.nebius.com) &nbsp;·&nbsp; [Nebius](https://nebius.com) &nbsp;·&nbsp; [More examples](https://github.com/Studio1HQ) &nbsp;·&nbsp; [studio1hq.com](https://studio1hq.com)

</div>

<br />

## Overview

AI GitHub Roast is a Flask app that reads the commit history of a public GitHub repository and sends it to a model on [Nebius AI Studio](https://docs.nebius.com/studio/inference/). The model replies with two paragraphs: a witty, technically accurate roast of the commit practices, then constructive advice on how to improve them.

It also shows the programming languages used in the repository. Developers can use it as a light-hearted way to review their own commit messages.

## Features

- **Commit analysis**: fetches commits for a GitHub username and repository through the GitHub API.
- **Roast and advice**: the model returns a humorous critique followed by concrete suggestions for better commit messages.
- **Language breakdown**: reads the repository's language stats from the GitHub API and shows them with the result.
- **Markdown rendering**: the model's reply is converted to HTML before it is shown.
- **Nebius-hosted model**: uses `google/gemma-2-27b-it` through the OpenAI SDK pointed at Nebius.

## Tech stack

| Layer | Tool |
| --- | --- |
| Framework | [Flask](https://flask.palletsprojects.com/en/latest/) |
| LLM | [Nebius AI Studio](https://docs.nebius.com/studio/inference/), `google/gemma-2-27b-it` |
| Client | [OpenAI Python SDK](https://github.com/openai/openai-python) with a custom base URL |
| Data source | [GitHub REST API](https://docs.github.com/en/rest) |
| Language | Python 3.6 or later |

## Getting started

### Prerequisites

- Python 3.6 or later
- A Nebius AI Studio API key
- A GitHub personal access token

### Installation

```bash
git clone https://github.com/Studio1HQ/GithubRoast.git
cd GithubRoast
python3 -m venv venv
source venv/bin/activate   # macOS and Linux
venv\Scripts\activate      # Windows
pip install -r requirements.txt
```

`app.py` also imports `flask`, `python-dotenv`, `openai` and `markdown`. If they are not already installed, add them:

```bash
pip install flask python-dotenv openai markdown
```

### Environment variables

Create a `.env` file in the project root:

| Variable | Description |
| --- | --- |
| `NEBIUS_API_KEY` | Nebius AI Studio API key from the [Nebius Studio inference docs](https://docs.nebius.com/studio/inference/). |
| `GITHUB_TOKEN` | GitHub personal access token used to call the commits API. |

### Run

```bash
flask run
```

Open <http://127.0.0.1:5000>, then enter a GitHub username and repository name.

## How it works

```text
app.py                  Flask routes, GitHub calls, Nebius call
templates/index.html    input form
templates/result.html   roast and language list
static/style.css
```

On a POST to `/`, the app requests `https://api.github.com/repos/<user>/<repo>/languages` and `/commits`. It collects each commit's message, author, date and URL, puts them in a roast prompt, and calls `chat.completions.create` on `https://api.studio.nebius.ai/v1/` with `max_tokens` 512 and `top_p` 0.9. The reply is rendered with `markdown` and passed to `result.html`.

## Resources

- [Nebius AI Studio inference docs](https://docs.nebius.com/studio/inference/): API keys and models.
- [Nebius Token Factory docs](https://docs.tokenfactory.nebius.com): current docs for Nebius inference.
- [Nebius](https://nebius.com): the platform site.
- [GitHub REST API docs](https://docs.github.com/en/rest): commits and languages endpoints.

## License

Released under the [MIT License](LICENSE).

<br />

---

<div align="center">

<a href="https://studio1hq.com">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-dark.svg" />
    <img src="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-light.svg" alt="Studio1" width="160" />
  </picture>
</a>

Built by **[Studio1](https://studio1hq.com)**, the technical content and DevRel partner for devtool teams. Made with [Nebius](https://nebius.com).<br />
Browse more open-source examples at [github.com/Studio1HQ](https://github.com/Studio1HQ).

[![Website](https://img.shields.io/badge/studio1hq.com-0b0807?style=for-the-badge&logo=googlechrome&logoColor=white)](https://studio1hq.com)
[![Book a call](https://img.shields.io/badge/Book_a_strategy_call-f97316?style=for-the-badge&logo=googlecalendar&logoColor=white)](https://cal.com/studio1/collab)
[![X](https://img.shields.io/badge/%40Studio1HQ-141414?style=for-the-badge&logo=x&logoColor=white)](https://x.com/Studio1HQ)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/studio1hq/)

<sub><a href="https://studio1hq.com">studio1hq.com</a> · Technical content, docs, video and DevRel for devtools</sub>

</div>

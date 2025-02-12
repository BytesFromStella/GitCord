# GitCord - GitHub Issue Manager with Discord Integration

## Overview
GitCord is a collaborative tool that helps teams manage GitHub issues from multiple repositories in a single interface. The core feature is real-time **Discord notifications**, ensuring developers and project managers stay updated on issue changes.

## Features
- **Multi-Repo Issue Fetching**: Fetch issues from multiple GitHub repositories.
- **Filtering & Sorting**: Filter by labels, assignees, status (open/closed), priority, and repository.
- **Assignment Management**: Assign, unassign, and reassign issues easily.
- **Real-time Discord Notifications**: Sends messages to Discord channels for new, updated, and closed issues.
- **Customizable Web Dashboard**: A simple UI to browse and manage issues.
- **CLI Support (Stretch Goal)**: Manage issues via a command-line interface.

## Tech Stack
- **Backend**: Rust (Axum/Tokio) or Bun.js (for speed and JavaScript familiarity)
- **Frontend**: React + Tailwind (Optional, for a web dashboard)
- **Database**: PostgreSQL or SQLite (for storing issue metadata, user preferences)
- **API**: GitHub REST API v3 + Webhooks
- **Messaging**: Discord Webhooks & Bot API

## Setup Instructions

### Prerequisites
- A GitHub account with access to repositories.
- A Discord server where the bot can send notifications.
- Node.js (for Bun.js) or Rust (for Axum-based backend).

### 1. Clone the Repository
```sh
git clone https://github.com/yourusername/gitcord.git
cd gitcord
```

### 2. Configure GitHub API
- Create a [GitHub Personal Access Token](https://github.com/settings/tokens) with `repo` and `notifications` permissions.
- Store the token in `.env`:
  ```sh
  GITHUB_TOKEN=your_github_token_here
  ```

### 3. Configure Discord Webhooks
- Go to your Discord server settings.
- Navigate to **Integrations > Webhooks** and create a webhook.
- Copy the webhook URL and add it to `.env`:
  ```sh
  DISCORD_WEBHOOK_URL=https://discord.com/api/webhooks/your_webhook_id/your_webhook_token
  ```

### 4. Run the Application
#### Bun.js (JavaScript Backend)
```sh
bun install
bun run server.js
```
#### Rust (Axum Backend)
```sh
cargo build --release
./target/release/gitcord
```

### 5. Web Dashboard (Optional)
```sh
cd frontend
npm install
npm run dev
```

## Usage
### Fetch Issues
- Automatically syncs issues every X minutes.
- Run manually with:
  ```sh
  curl -X POST http://localhost:3000/fetch
  ```

### Assign an Issue
```sh
curl -X POST http://localhost:3000/assign -d '{ "issue": 123, "assignee": "@username" }'
```

### Example Discord Notification
```
🔔 **New Issue Created**
📌 Repository: my-repo
🛠️ Title: Fix login bug
👤 Assigned: @developer
🔗 [View Issue](https://github.com/my-org/my-repo/issues/42)
```

## Future Enhancements
- **Role-based permissions** for issue management.
- **Slack integration** alongside Discord.
- **Email notifications** for non-Discord users.
- **AI-powered issue tagging & prioritization.**

## Contributing
We welcome contributions! Feel free to submit issues, PRs, and feature requests.

## License
MIT License © 2025 Your Name


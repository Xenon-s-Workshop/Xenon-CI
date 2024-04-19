# Xenon-CI Workflow

This repository contains the Xenon-CI workflow, a GitHub Actions workflow designed to automate the process of cloning a repository, setting up a Python environment, installing dependencies, and notifying the status through Telegram upon completion.

## Overview

The `xenonci.yml` workflow is triggered on pushes to the `main` branch or manually via the GitHub Actions workflow_dispatch event. It consists of several jobs that clone a repository, install necessary dependencies, execute a userbot, and send a notification to a specified Telegram chat with the workflow's status, including the branch name, commit SHA, execution date, and operating system specifications.

## Setup

To use this workflow in your repository, follow these steps:

1. **Fork or Clone This Repository**: Start by forking or cloning this repository to your GitHub account.

2. **Configure Secrets**: Go to your repository's Settings > Secrets and add the following secrets:
   - `GITHUBMAIL`: Your GitHub email address.
   - `GITHUBNAME`: Your GitHub username.
   - `GH_TOKEN`: Your GitHub personal access token with the necessary permissions.
   - `REPOSLUG`: The slug (username/reponame) of the repository you want to clone.
   - `WORKER`: The entry point for your Python application (e.g., `app.main`).
   - `BOT_TOKEN`: Your Telegram bot token.
   - `CHAT_ID`: The chat ID where notifications should be sent.

3. **Modify the Workflow (Optional)**: If needed, modify the workflow file (`xenonci.yml`) to fit your project's requirements. This may include changing the Python version, adding or removing dependencies, or adjusting the notification message.

4. **Trigger the Workflow**: You can trigger the workflow by pushing changes to the `main` branch or manually via the GitHub Actions tab in your repository.

## Workflow Jobs

- **userbot**: Clones the specified repository and sets up the Python environment with all necessary dependencies.
- **looper**: Ensures the userbot runs in a loop, handling any required Git configurations.
- **notify_telegram**: Sends a notification to the specified Telegram chat upon successful completion of the workflow, including detailed information about the execution.

---

For more information on GitHub Actions and how to customize workflows, visit the [GitHub Actions documentation](https://docs.github.com/en/actions).

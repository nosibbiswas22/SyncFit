# Contributing to SyncFit

Thank you for helping build SyncFit. The repository is public so anyone can
view the project, but contributions are limited to **approved GitHub
collaborators** with write access. Do not share database credentials or
collaborator access outside the team.

## Before you start

Make sure you have:

- Been added as a collaborator to the GitHub repository.
- Java JDK 17 or later installed.
- Apache Maven and Git installed.
- Received the current development configuration from the team lead.
- Access to the appropriate Neon PostgreSQL environment, if your task needs
  database access.

Never commit passwords, API keys, Neon connection strings, or other secrets.
Use local environment variables or an ignored configuration file instead.

## Step-by-step workflow

### 1. Clone the repository

```bash
git clone https://github.com/NOSIBBiswas22/SyncFit.git
cd SyncFit
```

### 2. Create a branch

Start from the latest default branch and use a focused branch name:

```bash
git checkout main
git pull origin main
git checkout -b feature/short-description
```

Use the following branch naming convention:

```text
<type>/<short-kebab-case-description>
```

Supported branch types:

| Type | Use for | Example |
| --- | --- | --- |
| `feature` | New functionality | `feature/timetable-matching` |
| `fix` | Bug fixes | `fix/invalid-job-hours` |
| `docs` | Documentation changes | `docs/update-contributing-guide` |
| `refactor` | Internal code improvements without behavior changes | `refactor/repository-layer` |
| `test` | Adding or updating tests | `test/matching-service` |
| `chore` | Maintenance and tooling | `chore/update-maven-config` |

Keep names short and specific. Do not work directly on `main`, use spaces or
uppercase letters in branch names, or combine unrelated tasks in one branch.

### 3. Understand the task

Review the relevant issue or task before coding. Confirm the expected behavior
with the team if the requirement is unclear. Keep each branch focused on one
change.

### 4. Implement the change

Follow the existing Java, Swing, Maven, PostgreSQL, and project naming
conventions. Keep database queries parameterized, validate user input, and
avoid committing generated files or local IDE settings.

### 5. Verify your work

Before committing:

- Build the project with Maven when the Maven structure is available.
- Run the relevant tests.
- Open the Swing screens affected by the change and check the main user flow.
- Verify that database changes work against the approved development database.
- Review the changed files with `git diff`.

Do not use production data for testing.

### 6. Commit clearly

SyncFit follows a Conventional Commits-style format:

```text
<type>(<optional-scope>): <short imperative description>
```

Use one of these commit types:

| Type | Use for | Example |
| --- | --- | --- |
| `feat` | A new feature | `feat(matching): add timetable conflict detection` |
| `fix` | A bug fix | `fix(profile): validate weekly availability` |
| `docs` | Documentation only | `docs: update collaborator workflow` |
| `refactor` | Code restructuring without behavior changes | `refactor(data): separate repository interfaces` |
| `test` | Tests | `test(matching): cover overlapping work hours` |
| `chore` | Maintenance or configuration | `chore: configure Maven compiler` |
| `build` | Build system or dependency changes | `build: add PostgreSQL driver` |
| `ci` | Continuous integration changes | `ci: add Maven verification workflow` |

Commit standards:

- Use the imperative mood: `Add`, `Fix`, or `Update`, not `Added`, `Fixed`,
  or `Updating`.
- Keep the subject concise, specific, and under 72 characters when possible.
- Keep each commit focused on one logical change.
- Do not end the subject with a period.
- Add a body when context or a breaking change needs explanation.

Write a short, imperative commit message:

```bash
git add .
git commit -m "feat(matching): add timetable conflict validation"
```

Do not include secrets, unrelated formatting changes, or generated build
output in a commit.

### 7. Push your branch

```bash
git push -u origin feature/short-description
```

### 8. Open a pull request

Open a pull request from your branch into `main`. The pull request should
include:

- A brief summary of the change.
- The related issue or task.
- Testing performed and its result.
- Screenshots for visible Swing UI changes.
- Any database schema or migration considerations.

Request review from at least one teammate. Do not merge your own pull request
unless the team lead has approved that workflow.

### 9. Respond to review

Address review comments on the same branch, rerun the relevant checks, and
push the updates. Keep the pull request description current.

### 10. Clean up after merge

Once the pull request is merged, remove the local branch:

```bash
git checkout main
git pull origin main
git branch -d feature/short-description
```

## Database and secret handling

- Use a separate development database or Neon branch for local work.
- Never commit `.env` files, credentials, private keys, or connection strings.
- Share database access only through the team's approved private channel.
- Use migrations or documented SQL changes for schema updates.
- Avoid changing shared database data unless the task requires it.

## Questions and support

For access problems, task clarification, database setup, or merge conflicts,
contact the team lead through the project's private collaborator channel.

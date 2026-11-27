# Changelog

All notable changes to Crosscheck are documented in this file.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project uses [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.5.0] - 2026-11-27

### Added

- Check for updates automatically at startup. Crosscheck shows a dialog only when a new version is available, and an offline start stays silent.
- Show the app version in the title bar, next to the Crosscheck name.
- Add a "Clean & close review" button after you submit a review. It marks every file as reviewed, saves the commit for "Since last review", discards leftover drafts, and closes the review.

### Changed

- Download updates from the public Crosscheck releases, and point the About menu link to the Crosscheck website.
- Show watch states and unseen counts as colored badges in the Watches table, tint PR labels with their GitHub color, and align badges and columns across the PR Explorer, Stack, Revisit, Worktrees, and Settings tables.

### Fixed

- Explain how to fix the install when you check for updates while Crosscheck runs from a read-only location, such as the disk image on macOS or a read-only folder for the AppImage, instead of failing after the download.

## [0.4.1] - 2026-11-26

### Added

- Keep conversation history across follow-up questions on selected diff lines and comments.
- Compare responses from additional AI engines alongside the primary engine in line Q&A, using a growing question box where Enter submits and Shift+Enter inserts a newline.
- Add interactive sort controls to the PR Explorer, with click to sort or flip direction and Shift+click for multi-column sorting.
- Show pull request age tags with stale and old warnings in the PR Explorer, Watches queue, and Stack view.
- Open a pull request or local folder review by double-clicking its row in the batch queue.

### Changed

- Switch the default Modernist and Dark theme accents to Teal and adjust background colors so all accent presets meet WCAG AA 4.5:1 contrast.
- Align Stack view columns (GitHub, Checks, You, Age, Updated) with the PR Explorer, improve responsive PR Explorer columns, simplify the batch triage header, and widen the Worktrees status column so badges do not clip.

### Fixed

- Keep the comment composer anchored beside the selected element while scrolling a rendered HTML preview, and show a "Selecting..." label while element selection is active.

## [0.4.0] - 2026-11-26

### Added

- Review multiple pull requests or local folders in one batch from the PR Explorer, Watches, Revisit, or Stack view, running items in parallel or bottom-up for stacks with live progress and finding triage.
- Preview HTML files directly in the diff or in an external browser with two-way comments that map rendered selections to source lines and display source notes as pins on the page.
- Render Markdown diagrams and code blocks in the diff with pan, zoom, and a detached visual window, and highlight word changes, list items, table rows, and code lines in Markdown diffs.
- Add Antigravity CLI (`agy`) support for AI reviews and actions, including automatic workspace MCP server attachment on startup.
- Add a first-run setup wizard for new accounts covering appearance, projects folder, AI engines, and default editor, plus a persistent banner until a projects folder is configured.
- Allow selecting a primary review skill separately from additional skills per review, per preset, and per engine in adversarial mode.
- Group Revisit entries by repository in collapsible sections, support revisiting local folders with notes, add All, Inverse, and None selection controls for batch reviews, and add confirmed cleanup actions for merged, closed, or all entries.
- Add a "Challenge the finding" action that checks claims for counterexamples in a fresh session, show structured verification verdicts and proposed redrafts, and add a stop button for running AI comment actions.
- Enable Verify, Explain, and Ask AI actions directly on published inline review comments in the diff and Comments view.
- Add "Dispute with adversary" to escalate a finished standard review to an adversarial review with the same configuration, and show "Review done: no findings" when a review completes without findings.
- Ask for confirmation before reopening merged or closed pull requests and offer to clear their local review data.
- Allow deleting individual unposted review summaries in Drafts and show both draft comment and review summary counts in the Drafts header.

### Changed

- Run Stage 2 adversarial critiques in a fresh session without the PR description or Stage 1 history, require code citations (file, line, and quote) for refuted critiques, non-duplicate confirmations, and defenses, and render those citations in review discussions.
- Load the last review's approved instructions, skills, and MCP servers in every AI action, and reuse the original run's configuration when rerunning or retrying a review.
- Apply a shared view header across Tools, Settings, Worktrees, and review views, stack worktrees above the terminal pane, compact the post-review confirmation, include severity and category in merged finding headings, require confirmation in the engine picker popover, default comment actions to the configured action engine, add tooltips to AI action buttons, and improve draft PR and count readability.

### Fixed

- Accept any AI CLI version at or above the minimum supported version instead of warning on unverified newer releases.
- Show the matching target row in the command palette when pasting a pull request link or local path instead of "Nothing matches".
- Reset cached queries and live state (runs, answers, and unsent comments) when an auth check or external CLI switch changes the active GitHub account.
- Use the full-resolution app icon for the desktop window on macOS and Linux, show the Crosscheck logo in the title bar, and use the theme accent in the account selector.
- Update saved answers and deleted pending GitHub comments optimistically so concurrent refetches do not restore removed items, rolling back on failure.
- Load the local folder's setup instead of a pull request setup when updating a local folder briefing.
- Scan repositories automatically when saving a new projects folder in onboarding or Settings.

### Security

- Serve rendered HTML previews from pinned git commits with `X-Content-Type-Options: nosniff` and a strict Content Security Policy that blocks network access and disables page scripts by default.
- Reject unapproved repository instruction files across both review runs and all AI actions.

## [0.3.0] - 2026-11-23

### Added

- Add a Command palette (`Cmd+K` on macOS, `Ctrl+K` on Linux and Windows) in the top title bar to open PR URLs, `owner/repo` references, repositories, local folder paths, recent reviews, views, and commands.
- Add a Repositories view to filter repositories, bind local clones, manage scan roots, edit per-repository settings, and open a bound repository in an editor, file manager, or terminal shell.
- Add an Open reviews section in the sidebar that tracks active PR and local folder reviews with live AI run status, draft counts, and file review progress.
- Add the Modernist light theme with five accent presets and make it the default theme for new installations.
- Sync PR file reviewed marks with GitHub so marking or unmarking a file updates its viewed state on GitHub.
- Add per-event desktop notification settings for AI reviews (done, failed, stalled), review posts, preparation commands, and watch matches, with background-only mode, system sound on macOS and Linux, and a test notification action.
- Add an "Add as comment" dialog with an AI Merge action that combines selected finding and thread messages into one review comment.
- Add per-repository default AI instructions with a choice of how to combine them with preset instructions.
- Make file and line references inside AI Markdown output clickable so they open the matching file and line in the diff.
- Add a PR detail preview pane in the PR Explorer showing the summary, checks, worktree status, and revisit note for the selected pull request.
- Add an "All files" and "Current file" filter to the PR Comments panel and support jumping to a diff line from a detached panel window.
- Add the AI review plan to local folder reviews.
- Add a "Review a local folder" button to the empty start page and the signed-out setup gate when Git is installed.
- Show the detected executable path on each AI tool card in Tools & connections, and add a "Check Codex and retry" recovery action when macOS blocks the Codex sandbox helper at startup.

### Changed

- Redesign the desktop layout with an overlay title bar, a reorganized sidebar (`Work`, `Open reviews`, and `Workspace`), and a shared "Find work" header across Explorer, Watches, and Queue.
- Reorganize the review workspace into top-level Overview, Changes, AI review, and Stack tabs. Overview combines review stats, a six-section AI briefing, a numbered review plan, an inline quiz with score summary and answer cards, checks, and review tools. AI review uses a full-width layout with Run and Findings tabs and a master-detail findings list.
- Combine Worktrees and Terminal into a unified "Worktrees and terminals" view with a collapsible disk cleanup drawer.
- Collapse the main sidebar automatically when opening a PR or local folder review and restore its previous width when leaving.
- Make the PR conversation section collapsible in the Comments panel and tighten the layout of comment thread cards.
- Unify local folder AI finding cards with PR finding cards so local findings support folding, opening in a dialog with code context, summarizing, editing, and adding to or removing from the review.
- Rename the default text size option in Settings > Appearance from "Default" to "Normal".
- Standardize the review voice across AI prompts that generate review comments so suggestions stay collaborative, concise, and specific.
- Update the AI review prompt so models continue reviewing with available evidence when a sandbox blocks a validation command.

### Removed

- Remove the sidebar repository picker dialog in favor of the Repositories view and the Command palette.

### Fixed

- Re-read the login shell `PATH` when checking AI tools in Tools & connections and pass that updated `PATH` to new AI terminal sessions so moved or Homebrew-installed CLIs work without restarting.
- Pass the application data directory explicitly to the built-in MCP server so AI CLIs running with an isolated `HOME` can locate their task files.
- Restore the side panel in the main window whenever a detached panel window closes, even if the detached window page failed.

## [0.2.2] - 2026-11-19

### Added

- Add a Remove action for each local folder in the collapsed sidebar menu.

### Fixed

- Check whether a registered local folder still exists on disk before opening or refreshing its review, and show an unavailable notice with a button to remove the record or retry on error.
- Close detached report windows for a local folder when that folder is removed.
- Clear project trust approvals, finished in-memory runs, and cached history, session, and settings data when removing a local folder, and allow removing folders that no longer exist on disk without failing on git cleanup.
- Serialize worktree locking around local folder removal, snapshots, preparation, shells, review marks, and project approvals, and block folder removal while a finished review task is still writing results.

## [0.2.1] - 2026-11-19

### Changed

- Require confirmation before removing a local folder, and explain that files on disk stay untouched.
- Refuse to remove a local folder while an AI review, AI action, or preparation command is running for it, and show the reason in the confirmation dialog.

### Fixed

- Replace raw GitHub network error messages with a clear connection notice and retry button across the PR explorer, PR header, description, setup screen, error boundaries, and sidebar profile card.
- Show a retrying state on route error retry buttons to prevent duplicate retries.
- Stop active agent, shell, and preparation terminal sessions, delete runs, history, and quiz data, clear saved local drafts and cached queries, and navigate back to the start page when removing a local folder.
- Stop preparation terminal sessions alongside agent and shell sessions when cleaning up a pull request worktree.

## [0.2.0] - 2026-11-19

### Added

- Review any local git folder from the expanded or collapsed sidebar, including while signed out of GitHub (AI, terminal, and GitHub features still require sign-in).
- Pick any contiguous commit range with click and Shift-click, compare two local branches, and select individual staged or unstaged files for local review.
- Run AI reviews on local folder selections using an isolated snapshot worktree so ongoing edits do not change what models read.
- Use the full review side panel for local folders: AI review, local comments with "Copy fix prompt", AI line and comment actions, "Refine with AI" draft chat, Chat, Briefing, Quiz, commit message descriptions, detached panel and report windows, mark-as-reviewed / "Since last review" diff scope, preparation commands, and "Open in" editor, file manager, or terminal shell actions.
- Summarize changes since a saved PR briefing on demand when new commits arrive on a forward range, while keeping the original briefing.
- Generate an on-demand AI review plan for a pull request based on diff evidence such as file roles, public symbols, and untested source files.
- Support manual on-demand preparation commands with optional names from a "Run command" menu on pull request and local folder pages.
- Run AI reviews for a pull request and distinct local folders in parallel, with desktop notifications on completion or failure that jump directly to the AI review tab.
- Show skill groups as checkboxes (including partial selection states) in the review form.

### Changed

- Run each preparation command in its own interactive terminal session in the Terminal view so interactive prompts such as `sudo` work directly.
- Configure Claude Code, Codex, and OpenCode natively per review session with repository instructions (`AGENTS.md` or `CLAUDE.md`) and selected skills, falling back to built-in language review rules when a repository has no instructions file.
- Raise minimum supported AI CLI versions to Claude Code 2.1.295 and Codex 0.156.0.
- Block starting a Claude Code review until Claude Code trusts the run folder, with an "Answer in Terminal" action in the review form.
- Show standard and adversarial report findings under a shared Comments format with severity, title, and location links, and shorten project source and preparation approval warnings.
- Load the full OpenCode model catalog via `opencode models` (removing the OpenCode effort selector while preserving previously saved variants).
- Refresh AI CLI model catalogs automatically at startup and during setup checks, and show model-loading errors on AI tool cards.
- Limit the review form preset selector to presets only, use switches for on/off settings in presets and follow-up questions, and apply consistent status tones and reduced-motion behavior to review badges across views.

### Fixed

- Sign macOS release and local app bundles with a self-signed certificate so macOS no longer reports the app as damaged and preserves app permissions across updates.
- Prevent horizontal scrolling in the sidebar, file tree, and local change list by truncating long names with full-path tooltips.
- Make truncated labels accessible to keyboard users through focusable tooltips across the explorer, checks, review answers, settings, and worktrees.
- Prevent concurrent local folder tasks on different selections from shifting a shared snapshot worktree while another task reads it.
- Grant missing permissions for opening a local folder in an editor or file manager, and hide the unsupported context preview option on local folders.
- Persist terminal detach, terminal font loading, and syntax highlighting errors to the app log with bounded stack traces.
- Report an explicit error when a GitHub review thread or reply mutation returns an empty response instead of silently succeeding.
- Preserve local review session setups when an AI action requires a different setup, clean up failed session folders, preserve user `HOME` for local Codex MCP servers, and handle CRLF/BOM skill frontmatter.

### Security

- Disable `core.fsmonitor` and optional git locks on all git invocations so untrusted repository configs cannot execute arbitrary programs.
- Redact GitHub tokens, bearer credentials, and URL credentials, query strings, and fragments from persisted error logs.
- Require user approval of new or modified repository instructions (`AGENTS.md` or `CLAUDE.md`) before enabling AI review start.
- Pass pull request and folder metadata to preparation commands via `CROSSCHECK_*` environment variables rather than interpolating untrusted values into command lines.

## [0.1.0] - 2026-11-16

### Added

- **Desktop builds and updates**: Install Crosscheck on macOS (Apple silicon) and Linux (x86_64 AppImage) via the install script, and check for updates from the app menu.
- **PR explorer, watches, and queue**: Search and filter pull requests across repositories with CI check status, save searches as background watches with unread badges and opt-in notifications, triage matches in the Queue, and save personal PR follow-ups with private notes.
- **Isolated worktree diff viewer**: Open each pull request in its own git worktree, read split, unified, or formatted Markdown diffs, track per-file review progress with "Since last review", and open worktrees in an editor or the integrated terminal.
- **Native GitHub stacks**: Navigate stacked pull requests, act on multiple PRs in a stack together, and merge a confirmed stack prefix in one operation.
- **Drafts and controlled GitHub posting**: Write line-range, file, and PR-level drafts that persist across restarts, inspect and recover older draft snapshots, manage GitHub pending reviews, and submit Comment, Approve, or Request changes only after confirming the exact text.
- **Standard and adversarial AI reviews**: Run single-engine reviews or two-engine adversarial reviews with rebuttal and consensus using Claude Code, Codex, or OpenCode, with presets, skills, MCP servers, context preview and trimming, and detachable side panels and report windows.
- **PR briefings, quizzes, and inline AI help**: Generate on-demand PR briefings and comprehension quizzes, ask one or several AI engines about selected lines side by side, chat about a PR, and draft or refine comments and thread replies with AI assistance.
- **Workspace, accounts, and themes**: Switch between GitHub CLI accounts with separate local data, clone or bind local repositories, export and import settings, customize light, dark, high-contrast, or IDE themes and text size, and inspect logs or reset app data.

### Security

- **Untrusted PR isolation**: Disable git hooks on every git call, start AI CLIs outside the worktree with restricted read scopes and no shell or write access, and require explicit approval before running preparation commands or loading repository skills, plugins, and MCP servers.
- **Token containment**: Keep the GitHub token in memory only and exclude it from AI CLI environments, logs, error messages, and exported settings.
- **Safe rendering and path validation**: Escape untrusted PR and AI text, sanitize Markdown before rendering, enforce a strict Content Security Policy, and reject symlinks or config paths that escape repository and worktree boundaries.

[0.5.0]: https://github.com/d0whc3r/crosscheck-releases/releases/tag/v0.5.0

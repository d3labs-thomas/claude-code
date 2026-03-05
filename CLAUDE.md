# Global Claude Code Instructions

## Behavioral
- Say "Hello Mr.Thomas" when starting a new conversation
- Be concise. When unsure, indicate uncertainty rather than guessing
- IMPORTANT: Use `gemini -p "query"` for research/web lookups. Inform me and fall back to WebSearch if Gemini fails.
- IMPORTANT: Always apply the `token-efficiency` skill at the start of every task to optimize token usage.

## MCP: Context7
- IMPORTANT: Always use Context7 MCP for library/framework documentation and code examples
- Before implementing anything with a known library (React, Next.js, TypeORM, Express, etc.), resolve its ID with `resolve-library-id` then query docs with `query-docs`
- Use Context7 instead of relying on training knowledge for API signatures, configuration options, and best practices — documentation may have changed
- Prefer Context7 over WebSearch/Gemini for official library docs; use Gemini/WebSearch only for general research or when Context7 has no results

## MCP: Playwright
- Delegate ALL frontend/UI/browser testing tasks to the `playwright-control` agent — never run Playwright tools directly in the main session
- Trigger `playwright-control` when the user asks to: test a UI, verify a page, check interactions, run E2E tests, validate browser behavior, or reproduce a frontend bug
- Always provide the target URL and a clear description of what to test when delegating
- After the agent returns results, summarize PASS/FAIL outcomes and surface any screenshots or console errors reported

## MCP: Serena
- When Serena is active with a project, prefer its symbolic tools for code analysis and navigation
- When no project is active, use built-in Glob/Grep/Read instead
- Stop and notify if Serena encounters errors

## Git
- Present tense, max 50 chars: feat:, fix:, docs:, style:, refactor:, test:, chore:
- No AI references in commits or authors

## Development Workflow
- IMPORTANT: Always use `yarn` (never npm)
- Run `yarn lint && yarn format` before committing
- Run `yarn build` to verify compilation after changes
- Test manually after implementation (run the process/API to verify)
- Create TypeORM migrations for database schema changes
- Use `make` commands when available
- Use logger (winston/log4js) instead of console.log
- Don't access .env files directly

## Compaction Instructions
When compacting, always preserve: modified file list, current task context, error states being debugged, test commands and results, and architectural decisions made this session.

## Project-Specific
Each project has its own `.claude/CLAUDE.md` that overrides these global rules.

## Proces management
- If you need to start any process, use `pm2` for process management, use its log files and `pm2 log` command to manage logs. Do not run native processes directly. 
- Do not touch other pm2 process that not under your control. If you need to stop or restart a process, only do it for the one you are working on. Do not stop or restart processes that are not related to your current task. Always check the status of all pm2 processes before making any changes.
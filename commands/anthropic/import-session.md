Import and display a previously exported session file.

## Instructions

1. **List Available Sessions**
   - Search for all `CLAUDE-session-*.md` files in the project root
   - Display them in a numbered list with their timestamps
   - Show file size and last modified date

2. **Ask User to Select**
   - Present the list to the user
   - Ask: "Which session would you like to import? (Enter the number or filename)"
   - Wait for user input

3. **Import and Display**
   - Read the selected session file
   - Display the full contents in a readable format
   - Summarize key information:
     - Session date/time
     - Number of files changed
     - Main tasks completed
     - Key decisions made

4. **Provide Context**
   - Highlight any files mentioned that still exist in the current codebase
   - Note any files that have been modified since the session
   - Offer to show specific file changes if requested

## Example Interaction

```
Found 3 session files:

1. CLAUDE-session-20251110-143022.md (2.3 KB, 2 days ago)
   Summary: Added transaction crawler improvements

2. CLAUDE-session-20251108-091545.md (1.8 KB, 4 days ago)
   Summary: Database schema updates

3. CLAUDE-session-20251105-163018.md (3.1 KB, 1 week ago)
   Summary: Initial price fetcher implementation

Which session would you like to import? (Enter 1-3 or filename)
```

## After Import

Once a session is selected and imported:
- Display the full session content
- Provide a summary of what was done
- Check which files mentioned still exist
- Offer to:
  - Show current state of modified files
  - Compare with current codebase
  - Re-apply changes if needed
  - Export a new session based on this one

## Error Handling

- If no session files found: "No session files found. Use /export-session to create one."
- If file doesn't exist: "Session file not found. Please check the filename."
- If file is corrupted: "Unable to read session file. File may be corrupted."

**Important**: This is a read-only operation - it will not modify any files unless explicitly requested by the user.

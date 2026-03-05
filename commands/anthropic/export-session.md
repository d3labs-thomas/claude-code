Export the current session to a markdown file named `CLAUDE-session-${datetime}.md` where ${datetime} is the current timestamp in format YYYYMMDD-HHmmss.

The exported file should include:

## Session Export Structure

1. **Session Metadata**
   - Date and time of export
   - Duration of session (if available)
   - Brief summary of the session

2. **File Changes**
   - List all files that were created, modified, or deleted during this session
   - For each file, include:
     - File path
     - Type of change (created/modified/deleted)
     - Brief description of what changed

3. **Content Brief**
   - Summary of tasks completed
   - Key decisions made
   - Any important context or notes
   - Commands executed (if relevant)
   - Problems solved or issues encountered

4. **Code Snippets** (optional)
   - Include relevant code snippets for significant changes
   - Use proper syntax highlighting with language tags

## Format Example

```markdown
# Session Export - [Date Time]

**Session Duration**: [start] - [end]
**Summary**: [Brief one-line summary]

---

## File Changes

### Created
- `path/to/file1.ts` - [Brief description]
- `path/to/file2.md` - [Brief description]

### Modified
- `path/to/file3.ts` - [What changed]
- `path/to/file4.json` - [What changed]

### Deleted
- `path/to/file5.old` - [Why deleted]

---

## Session Content

### Tasks Completed
1. [Task 1 description]
2. [Task 2 description]

### Key Decisions
- [Decision 1 with rationale]
- [Decision 2 with rationale]

### Commands Executed
```bash
[command 1]
[command 2]
```

### Issues & Solutions
- **Issue**: [Description]
  **Solution**: [How it was resolved]

---

## Code Highlights

### [File/Feature Name]
```typescript
// Relevant code snippet
```

---

*Generated with Claude Code*
```

**Important**:
- Save the file in the project root directory
- Use the actual current date/time for the filename
- Include git status information if available
- Be concise but comprehensive
- Focus on actionable information

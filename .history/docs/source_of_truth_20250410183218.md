# Source of Truth for AgenticMesh

## Introduction

This document defines the "Source of Truth" principles for AgenticMesh. It establishes which components and repositories serve as the authoritative source for different types of data, ensuring consistency and reliability across the system.

## Core Principle

**GitHub repositories serve as the single source of truth for all AgenticMesh data.**

This means that in any conflict or discrepancy between data in GitHub and data in an AI platform, the GitHub version is considered authoritative.

## Source of Truth Hierarchy

1. **GitHub Repository**: The primary source of truth for all data
2. **Local File System**: A temporary cache of the GitHub repository
3. **AI Platforms**: Consumers and producers of data, but not authoritative sources

## Data Types and Their Sources of Truth

### Custom Instructions

- **Source of Truth**: GitHub repository
- **Path**: `users/{user_email}/custom_instructions.md` for user-level instructions
- **Path**: `users/{user_email}/projects/{project_name}/custom_instructions.md` for project-level instructions
- **Format**: Markdown

### Knowledge Base Files

- **Source of Truth**: GitHub repository
- **Path**: `users/{user_email}/projects/{project_name}/knowledge_base/{file_name}`
- **Format**: Original format (PDF, TXT, CSV, JSON, etc.)

### Project Structure

- **Source of Truth**: GitHub repository
- **Path**: `users/{user_email}/projects/`
- **Format**: Directory structure

### Organization Structure

- **Source of Truth**: GitHub repository
- **Path**: `organization/{organization_name}/`
- **Format**: Directory structure

### Sync Configuration

- **Source of Truth**: GitHub repository
- **Path**: `config/sync_config.json`
- **Format**: JSON

## Conflict Resolution

When conflicts occur between GitHub and an AI platform, the following rules apply:

1. **GitHub Wins**: If the same resource has been modified in both GitHub and an AI platform, the GitHub version takes precedence.
2. **Timestamp-Based**: If timestamps are available, the most recent change wins.
3. **Manual Resolution**: For complex conflicts, manual resolution may be required.

## Maintaining the Source of Truth

To ensure the GitHub repository remains the source of truth:

1. **Regular Sync**: Regularly sync data between GitHub and AI platforms.
2. **Validation**: Validate data before committing to GitHub.
3. **Backup**: Regularly backup the GitHub repository.
4. **Version Control**: Use Git's version control features to track changes.

## Best Practices

1. **Make Changes in GitHub**: Whenever possible, make changes in GitHub first, then sync to AI platforms.
2. **Use the CLI Tool**: Use the AgenticMesh CLI tool to manage the sync process.
3. **Review Changes**: Review changes before committing to GitHub.
4. **Document Changes**: Document significant changes in commit messages.

## Example Workflow

1. **Make Changes**: Make changes to custom instructions in GitHub.
2. **Commit Changes**: Commit the changes to the GitHub repository.
3. **Sync Changes**: Use the AgenticMesh CLI tool to sync the changes to AI platforms.
4. **Verify Changes**: Verify that the changes have been applied correctly in the AI platforms.

## Conclusion

By establishing GitHub repositories as the single source of truth, AgenticMesh ensures consistency and reliability across all AI platforms. This approach simplifies the management of AI agent configurations and provides a clear path for resolving conflicts and discrepancies.
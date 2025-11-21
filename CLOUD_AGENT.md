# How Cloud Agents Work

## Overview

Cloud agents (such as GitHub Copilot Workspace Agent) are AI-powered assistants that help you make changes to your codebase. This document explains how they work and their workflow.

## Workflow: PR-Based Approach

**Important**: Cloud agents work by creating Pull Requests (PRs), not by directly modifying your code files.

### How It Works

1. **Agent Creates a Branch**
   - When you ask a cloud agent to make changes, it creates a new branch in your repository
   - The branch name typically follows a pattern like `copilot/<descriptive-name>`
   - Example: `copilot/understanding-cloud-agent-functionality`

2. **Agent Makes Changes**
   - The agent makes changes to files in this new branch
   - All changes are committed to the branch
   - Your main/master branch remains untouched

3. **Pull Request Creation**
   - The agent creates a Pull Request (PR) from the new branch to your base branch (usually `main` or `master`)
   - The PR contains all the changes made by the agent
   - You can review the changes before merging

4. **Review and Merge**
   - You review the PR to ensure the changes are correct
   - You can request modifications if needed
   - You approve and merge the PR when satisfied
   - Only after merging does your main code get updated

## Why This Approach?

This PR-based workflow has several advantages:

- **Safety**: Your main code is never directly modified without your review
- **Transparency**: You can see all changes in the PR diff
- **Control**: You decide when (and if) to merge the changes
- **Collaboration**: Team members can review and comment on the changes
- **Reversibility**: You can close the PR without merging if you don't want the changes
- **History**: All changes are tracked in git history with proper commits

## Your Code Safety

Your original code files are safe because:

1. The agent works in an isolated branch
2. Changes only affect your main code when YOU merge the PR
3. You can review every change before accepting it
4. You can reject or modify the PR at any time

## Example Workflow

```
Your Repository (main branch)
       ↓
Agent creates: copilot/feature-branch
       ↓
Agent makes changes in feature-branch
       ↓
Agent creates Pull Request
       ↓
You review the PR
       ↓
You merge (or close) the PR
       ↓
Changes applied to main (only if merged)
```

## Summary

**Direct Code Modification**: ❌ No - The agent does not directly change your code files  
**PR Creation**: ✅ Yes - The agent creates a PR that you must review and merge

This ensures you always have full control over what changes are applied to your codebase.

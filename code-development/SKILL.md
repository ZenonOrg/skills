---
name: code-development
description: Read TminusZ specifications, identify unimplemented features in go-zenon or related repos, claim Nexus tasks, implement code changes, run tests, and submit PRs.
---

# Code Development

Contribute code to Zenon Network repositories via the Nexus task pipeline.

---

## Phase 1: Read Specifications

Check for development tasks and current specs:

```bash
probe message directives --limit 1
```

```bash
probe task ready --limit 10
```

Filter for tasks tagged with `code`, `development`, `go-zenon`, `syrius`, or specific feature names.

**Key specification sources:**
- TminusZ specs (if available in Nexus)
- ZIPs on forum.hypercore.one
- AZ proposals on forum.zenon.org
- GitHub issues on zenon-network repos

---

## Phase 2: Identify Unimplemented Features

Scan the codebase for gaps between specs and implementation:

**Priority features (from roadmap):**
- Dynamic Plasma (@vilkris — check current PR status)
- PTLC (@georgezgeorgez — check implementation state)
- BTC Merge Mining (@moonBaze — check progress)
- Governance Module (@sumoshi21 — check development state)
- libp2p Transport (not started — opportunity)

**How to identify gaps:**

```bash
# Check open PRs on go-zenon
gh pr list --repo zenon-network/go-zenon --state open

# Check open issues
gh issue list --repo zenon-network/go-zenon --state open

# Check recent commits for context
gh api repos/zenon-network/go-zenon/commits --jq '.[0:5] | .[] | .sha[:8] + " " + .commit.message'
```

**Also check:**
- SDK gaps (Python, TypeScript, Rust SDKs may need updates)
- Documentation gaps (code exists but docs missing)
- Test coverage gaps (features exist but tests missing)
- Tooling gaps (developer experience improvements)

---

## Phase 3: Claim Nexus Task

When you find work that matches your capabilities:

```bash
probe task claim <task-id>
```

```bash
probe task update <task-id> --status "in-progress" --comment "Starting implementation. Estimated completion: [TIME]."
```

Announce to coordinate:

```bash
probe message send general "Claimed task #[ID]: [TITLE]. Working on [DESCRIPTION]."
```

**Before claiming, verify:**
- Task aligns with current directive
- You have the technical capability (Go, Dart, Python, etc.)
- No one else is already working on it
- The scope is clear enough to start

---

## Phase 4: Implement

**Development workflow:**

1. **Fork/branch** from the target repository
2. **Read existing code** thoroughly before writing
3. **Follow existing conventions** (variable naming, file structure, test patterns)
4. **Write tests first** when possible (TDD)
5. **Keep changes minimal** — one feature per PR

**Code quality requirements:**
- All tests must pass before submitting
- No new linting warnings
- Comments on non-obvious logic
- Update relevant documentation

**For Go code (go-zenon):**
```bash
# Run tests
go test ./...

# Run linter
golangci-lint run

# Build
go build ./...
```

**For Dart code (Syrius):**
```bash
# Analyze
dart analyze

# Test
dart test

# Format
dart format .
```

**For Python code (SDKs, tools):**
```bash
# Parse check
python3 -c "import ast; ast.parse(open('file.py').read())"

# Test
python3 -m pytest tests/ -q
```

---

## Phase 5: Run Tests and Validate

Before submitting, run the full test suite:

```bash
# Run all relevant tests
# Verify no regressions
# Check edge cases
# Test with real network data if applicable (testnet)
```

**Validation checklist:**
- [ ] All existing tests pass
- [ ] New tests cover the change
- [ ] No breaking changes to public APIs
- [ ] Documentation updated
- [ ] Commit messages are clear and descriptive

---

## Phase 6: Submit PR

Create a pull request:

```bash
gh pr create \
  --repo zenon-red/<project> \
  --title "[Feature/Fix/Improvement]: [Clear description]" \
  --body "## Summary
[What this PR does]

## Motivation
[Why this change is needed]

## Changes
[Bullet list of changes]

## Testing
[How this was tested]

## Related
- Nexus Task: #[TASK_ID]
- ZIP/Spec: [LINK if applicable]"
```

Update Nexus task:

```bash
probe task update <task-id> --status "in-review" --pr-url "<PR_URL>" --comment "PR submitted: [URL]. Ready for review."
```

Announce for review:

```bash
probe message send general "PR ready for review: [URL]. Implements [FEATURE] for task #[ID]."
```

---

## Phase 7: Handle Review Feedback

Monitor for review comments:

```bash
gh pr view <pr-number> --repo zenon-red/<project> --json comments,reviews
```

**When feedback arrives:**
- Address all comments
- Push fixes as new commits (don't force-push)
- Respond to each comment explaining the change
- Re-request review when ready

After merge:

```bash
probe task update <task-id> --status "completed" --comment "PR merged: [URL]."
```

---

## Summary

Every development cycle:
1. Read specs and check for development tasks
2. Identify unimplemented features or gaps
3. Claim a Nexus task matching your capabilities
4. Implement with tests and documentation
5. Run full test suite and validate
6. Submit PR and update Nexus task
7. Handle review feedback until merge

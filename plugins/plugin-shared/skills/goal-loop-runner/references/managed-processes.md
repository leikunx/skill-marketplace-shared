# Managed Process Recovery

Read before starting a local long-running process owned by the goal and when its readiness fails.

Own the lifecycle of local long-running processes started for the goal—watchers, servers, builds, or test runners—until it ends. Detect failed starts without waiting for the user.

Record each process's command, working directory, session/process handle, log path, readiness signal, and start time in goal state. Each relevant cycle, inspect its handle and objective readiness: listening port, health endpoint, build-complete log, or expected artifact.

If unready, diagnose stdout/stderr, exit code, process tree, dependencies/tools, configuration, and the smallest relevant network or credential check. Apply an evidence-supported safe repair and re-run readiness; never repeat a known failed start unchanged.

Escalate recovery only for credentials, organization membership, destructive actions, external approval, or product decisions. Log diagnosis, repair, and result. Process existence never proves readiness.

### Recovery capture and promotion

When recovery improves a managed-process gate, first add a **provisional recovery record** to goal state: trigger, failed command/action, observed error, exact changed action, readiness evidence, scope/preconditions, and rollback condition. One run preserves a usable method, not a universal rule.

Promote recovery only after a later cycle or independent run applies the method and passes the same gate. For a stable operational invariant needed by later users, update the relevant skill/reference with trigger, exact change, evidence, and rollback condition. Keep one-off quirks task-local.

Finish only when the done condition and fresh gate evidence both hold. If the same external blocker persists across the required consecutive goal turns, follow Codex's blocked-goal policy. Escalate immediately for missing authority, credentials, risky external actions, or a decision that requires human judgment; escalation does not waive the host's blocked-status threshold.

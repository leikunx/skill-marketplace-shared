# Company Work IQ messages

Read only for company/workplace tasks that involve Teams messaging through Work IQ.
Skip this reference for personal development and unrelated tasks, even when Work IQ
is connected. This guidance grants no permission to send a message.

## Style and routing

Write naturally, briefly and warmly like a colleague. Avoid canned reminders such as
“密码和密钥不用发在群里。” or “无需发送密码或密钥。” in ordinary questions and updates.
Handle security silently unless a concrete issue requires mentioning it.

For simple authorized Teams sends, use the connected Work IQ MCP and the machine's
account/recipient cache at `$CODEX_HOME/local-memory/workiq.md`, defaulting to
`~/.codex/local-memory/workiq.md` when `CODEX_HOME` is unset. Resolve that path on the
current machine. Keep account names, chat IDs and company data in local/project
memory; do not copy them into this shared skill. If no cache is available, resolve
only the identities and destination required by the task through the connected tools.

## Proportional send workflow

- Use a short update, one batched preflight for missing live facts, one send per
  requested destination, one read-back and a short result.
- For multi-line Teams messages, use `contentType: html` with explicit paragraphs,
  line breaks and code formatting. Plain-text newlines did not display correctly in
  the user's client. Keep instructions easy to scan; edit the original message when
  correcting formatting.
- Reuse verified identities, exact chat IDs, known resource paths and same-session
  authentication evidence. The cache is a routing hint: verify the connected account
  once per new session and exact membership before the first send to a cached chat.
- Discover only missing tools/paths. Inspect the send schema once per session as
  required by the tool; avoid repeated discovery. Batch independent reads and bound
  output to needed fields.
- Skip setup/version/documentation research, browser validation, installations,
  broad chat searches and repeated skill/reference reads for an ordinary send. Use
  those only when the requested content or a real failure requires them. Verify
  normal sends by MCP read-back; browser E2E is for explicit E2E requests or unresolved
  ambiguity.
- Reuse explicit send authorization without asking again to approve ordinary wording.
  This preference never authorizes a new message. Preserve requested recipients,
  conversation type and message count.
- Do not add goal machinery or a long contract to routine sends unless explicitly
  requested or required by higher-priority instructions. If `goal-loop-runner` is
  explicitly invoked, keep its required contract/state minimal and use this workflow.
- On an ambiguous send result, read the destination before retrying. On policy denial
  or missing sign-in, report the prerequisite without bypassing it.

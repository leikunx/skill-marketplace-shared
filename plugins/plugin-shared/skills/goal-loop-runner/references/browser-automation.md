# Browser Automation and Account Selection

Read before the initial browser action or selection of an authenticated browser instance.

For browser automation, first check Playwright Extension MCP availability. When available, use it for the initial browser action and collect evidence. Use another mechanism only at the user's explicit request, when the extension is unavailable or disconnected, or for an unsupported capability; first record the reason in goal state.

This browser-only preference does not require browser tools for other work or override authorization or safety boundaries.

### Multiple browser profiles and accounts

Separate Playwright Extension MCP instances may use different authenticated profiles. Honor an explicit instance choice; otherwise use task account/organization context and user-established mappings in project memory or `AGENTS.md`. Use the project default only without profile-specific context. Tool names do not prove identity; instances need not share sessions.

Before an account-sensitive action or external write, verify the live signed-in account and relevant organization or tenant through a read-only check in the selected instance. Record the selected instance, expected identity, and verification evidence in goal state. A remembered mapping is a routing hint, not proof of current authentication. If identity is wrong or uncertain, inspect or recover the intended session; ask only when the target identity cannot be determined from existing context and evidence. A disconnected or signed-out instance does not justify silently substituting another identity, transferring credentials, or changing authorization boundaries. Verify non-browser tool authentication separately when needed; browser sign-in does not establish Git, CLI, or API identity.

Keep exact instance/profile/account mappings in project memory, updating them when the user changes them; keep task observations in goal state. Shared guidance must remain general, without local account names, tenant identifiers, or machine-specific mappings.

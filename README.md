# cloudticketing-sandbox-config

The sandbox GitOps repository of [CloudTicketingAgentTool](https://github.com/Udaybhaskargit/CloudAgentTicketingTool)
(ADR-0015 item 14, Phase 4 step 4.9).

A fix plan's `pr` steps change a service's settings here instead of in the cloud directly:

- `services/<component>.yaml` — the component's config keys (`config:<key>`) and feature flags (`flag:<name>`).
- The platform opens a pull request with exactly the change a person approved, checks the pull request
  carries that change, merges it pinned to that commit, and then applies it to the simulated cloud (standing in
  for a GitOps deploy controller).
- If the fix does not hold, the platform opens and merges a revert pull request that restores the replaced
  values.

Nothing here is a secret, and no person or agent edits these files by hand: every change comes from an
approved plan.

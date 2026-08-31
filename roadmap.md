# MEGSY — Security Hardening Roadmap

## Done
- agent-tick: fail-closed when AGENT_TICK_SECRET missing (was fail-open with service role)
- Revoked anon/authenticated EXECUTE: get_user_subscription_status, expire_prize_rewards, ensure_mailbox; revoked anon on claim_promo_slot
- Confirmed all provider-key/secret tables have RLS + no anon/authenticated grants
- Telegram game tables/functions recorded as out of scope (shared DB, other app)

## Open
- Decision needed: legacy unprefixed `ai_activate_plan`, `ai_activate_plan_with_intent`, `ad_watch_*` are anon-executable (free subscription grant). Belong to Telegram app? -> revoke if unused
- CORS wildcard review: mail, mail-poll, broadcast, anything-api, auth-email-hook (low risk, no cookie auth)
- API red team: IDOR / param tampering on edge functions
- Cost-abuse: rate limits on paid model endpoints (chat-fast, anything-api)
- Prompt-injection tests for agents
- Dependency scan, perf, SEO, a11y
- Enable leaked-password protection (dashboard setting)

# MEGSY — Security Hardening Roadmap

## Done
- agent-tick: fail-closed when AGENT_TICK_SECRET missing (was fail-open with service role)
- Revoked anon/authenticated EXECUTE: get_user_subscription_status, expire_prize_rewards, ensure_mailbox; revoked anon on claim_promo_slot
- Confirmed all provider-key/secret tables have RLS + no anon/authenticated grants
- Telegram game tables/functions recorded as out of scope (shared DB, other app)
- generate-skill and chat-fast now require a valid signed-in user before paid provider calls
- auth-email-hook verifies Supabase webhook signatures and fails closed when unconfigured
- outbound mail is limited to 30 messages per user per hour
- Dependency scan passed with no high or critical vulnerabilities; TypeScript and unit tests pass

## Open
- Decision needed: legacy unprefixed `ai_activate_plan`, `ai_activate_plan_with_intent`, `ad_watch_*` are anon-executable (free subscription grant). Belong to Telegram app? -> revoke if unused
- CORS wildcard review: mail, mail-poll, broadcast, anything-api, auth-email-hook (low risk, no cookie auth)
- API red team: IDOR / param tampering on edge functions
- Cost-abuse: move all Vercel API limits to a shared persistent store; add limits to anything-api
- Prompt-injection tests for agents
- Perf, SEO, a11y
- Database migration: protect all financial, plan, ban, reward, and workspace usage columns from client updates
- Enable leaked-password protection (dashboard setting)

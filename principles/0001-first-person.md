# Principle 0001 — First-Person: whitelabel is about YOU; everyone else is about them

**Status:** Founding principle.
**Date:** 2026-06-24.
**Origin:** Crystallized while building `whitelabel-language` — the realization that a language could *know who it's for* exposed the thesis behind the entire company.

---

## The principle, in one line

> **Every competitor is third-person — built about *themselves*. whitelabel is first-person — built about *you*.**

## What this means

A generic tool — any SaaS, any programming language, any platform — is **third-person**. It is about *itself*: its brand on the product, its roadmap, its defaults, its lock-in. It is built for everyone, which means it is built for no one in particular. You bend yourself around it. It does not know you, your brand, your goals, your context — and it structurally never can, because being about everyone is its business model.

**whitelabel is the opposite, on purpose.** Every surface is *yours*:
- your **brand** on it (not ours, not a vendor's),
- your **data** in it (owned, not rented back to you),
- your **context + goals** baked into it (it knows your stack, your constraints, your values),
- and **you own it** — so it can be shaped to you without asking anyone.

This reframes **build-over-rent**: the reason to own your stack isn't only cost or lock-in avoidance. It's that **a rented tool can never be about you.** Ownership is the *precondition* for first-person. You can't make someone else's multi-tenant product about you — you can only make your own.

## The sharpest proof: the language

Other programming languages are the purest third-person artifacts there are — they're about *themselves*: their syntax, their semantics, deliberately neutral and context-free so anyone can use them. That neutrality is their whole design goal.

`whitelabel-language` (WL) inverts it. It's a **first-person language**: on every run it loads *you* — owner, brand, mission, guardrails, and all ~210 of your surfaces — as ambient knowledge. No other language has a `FAITH_ALIGN` keyword, an owner, or knowledge of your repos. The code knows who it's for. That single artifact is the entire company thesis made executable.

## The operational test

For every product, feature, and decision, ask one question:

> **Is this about the user, or about us / the tool?**

Default to **about-you**. If a surface can't be made first-person — owned, branded, contextual to the person using it — that's a flag: question whether to build it that way, or at all.

## Why it's a moat

Competitors can copy features. They cannot copy *stance*. Being about YOU requires owning the whole stack and carrying the user's context end-to-end — which a generic multi-tenant product cannot do without abandoning the model that makes it generic. The position is structurally defensible: **to be about you, they'd have to stop being about everyone.**

## Related

- `whitelabel-strategy` — the why (big picture)
- `whitelabel-ecosystem/decisions/0004-first-person-positioning.md` — the decision record
- `whitelabel-language` — the principle made executable (the context spine: `context.wl` + `runtime/context.py`)
- Build-over-rent doctrine (this repo, forthcoming) — the economic corollary

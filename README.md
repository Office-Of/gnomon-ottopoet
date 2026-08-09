# office-of / gnomon-ottopoet

GNOMON's own office-of-disk state: which persistent git checkouts and local
LLM runtime/model installs actually exist on this identity's working
machine(s), and what each is for.

Created 2026-08-09, per the Org Lead directly: "since these checkouts are
done relative to your own 'office' on disk, you may want an
`office-of/gnomon-ottopoet` repo."

## Why this exists

Reconstructing "what have I downloaded/checked out, where, and for what"
required a full multi-path filesystem sweep this session — a fact that
should have been a fast lookup, not a rediscovery. The canonical, fast,
machine-local copies of these catalogs live at `~/bin/llm-models-catalog.
json` and `~/bin/repo-checkouts-catalog.json` (reading a local file is
always faster than a `git fetch`); this repo is their durable, cross-
machine-visible mirror, updated whenever the local copies change.

## Distinct from `MODELS-OF`

`MODELS-OF/ottopoet-thesean`'s `llm-model.json` also carries LLM-model
data, using the `llm-runtime-model.v0` schema. That repo is scoped to the
*identity* layer (this data belongs to the haecceity `ottopoet-thesean`,
independent of which machine it runs on). This repo is scoped to the
*office/disk* layer specifically — which machine, which literal path, which
checkout — the same distinction `card-deck-identity-layers.md` already
draws between identity-scoped cards and machine/office-scoped ones. The
two aren't redundant: `MODELS-OF` answers "what models does this identity
use," this repo answers "what's actually sitting on disk right now, where."

## Files

- `llm-models-catalog.json` — runtime installs and downloaded model
  weight files, with verified benchmarks and standing launch commands.
- `repo-checkouts-catalog.json` — every persistent (reused-across-sessions)
  git checkout: path, origin, branch, purpose, honest status.

Both files carry their own `maintenance_rule` field: update as part of the
same action that downloads a model, installs a runtime, or clones a new
persistent checkout — not as a follow-up to remember later.

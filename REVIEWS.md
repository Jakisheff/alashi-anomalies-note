# Self-refereeing: three hostile reviews of main.tex (14.11.2026)

Written before submission, per the decision protocol in
20261114-note-refereeing. Each review ends with a verdict and what
fixes it: framing, data, or nothing.

## R1: the methodologist

The verification engineering is unusual and strong: preregistered
thresholds, bit-exact calibration, a cross-path check, a mutation-tested
verifier, an independent reimplementation. My objections are about n.

- A1 rests on ONE model (Llama-3.1-8B). The claim "compliance is a
  property of menu poverty" generalizes from a single point. The richer
  probes are the same model. This is an anecdote wearing a lab coat.
  Verdict: MAJOR. Fix: data (more families), partially mitigable by
  framing ("a case study, one model") but then the section title
  overclaims.
- A2 is solid: 20 paired seeds, no-overlap percentile ranges,
  conditional null, sign test. I would ask for the Wilcoxon alongside
  the sign test (it is computed; report it). Verdict: MINOR (framing).
- A3's policy space is hand-designed; the "exhaustive" claim is honest
  (42/42 of the influential subspace) but the subspace itself is a
  choice. Single-gene screening can miss interactions among
  non-influential genes. Verdict: MINOR-to-MAJOR. Fix: framing (state
  the denominator precisely, which the note does) plus one optional
  control (test the strongest 2-gene interaction of non-influential
  genes).

## R2: the external-validity skeptic

Why should anyone outside this project care about one custom
political-economy engine? The note positions the anomalies as general
("bounded-action protocols", "between-arm concentration comparisons")
but every data point comes from one game. The Game Arena comparison is
absent, so the reader cannot tell whether these menus and dynamics
stress models in a way chess or Werewolf does not. The BitLLM runs that
motivated the mechanism are cited but not in the package, so the
80.56-to-7.14 anchor is trust-me. Verdict: MAJOR for a venue, MINOR
for an arXiv note if the scope is stated as "a mechanism study with
machine-verified claims, external generality untested". Fix: framing
now; the rank-correlation study is the follow-up paper.

## R3: the statistician

- The permutation test is one-sided by preregistration; say so in the
  text, not only in the repo.
- The bootstrap CI for the median paired difference uses a seeded RNG;
  fine, but state the method and seed policy.
- Multiple testing across 20 paired seeds is handled by the sign test
  at the seed level; acceptable.
- The HHI breach (0.0302 vs 0.03) is marginal; the note already says
  so, but add the trivial observation that a 0.7 percent relative
  overshoot on one of five seeds does not locate the mechanism's edge,
  it detects it. Verdict: MINOR (framing).
- One-sided midrank ties handling: the midrank correction is defined;
  keep it.

## Decision table

| Review | Verdict | Fixed by |
|---|---|---|
| R1 A1 single model | MAJOR | data: v2 multi-family smoke (all L40S-hostable NIM images) |
| R1 A3 space choice | MINOR-MAJOR | framing (already present) + optional interaction control |
| R2 one engine | MAJOR (venue) / MINOR (note) | framing: scope as mechanism study; correlation study is next paper |
| R3 one-sided/bootstrap/marginality | MINOR | framing: two sentences each |

## Venue norm (measured, not remembered)

arXiv 2611.10404 (reward-hacking traces): 9 models x 20 tasks x 3 runs.
tau-bench-LILT README: at least 5 frontier families plus judge models.
Norm for compliance claims: 5-9 families. Conclusion: v1 publishes A1
as an explicit single-model case study; v2 lifts it to the venue norm
by testing every model family hostable on the local GPU.

## Version plan

- v1 (now): three anomalies; A1 framed as one-model case study with
  the public one-command smoke harness so outsiders can extend n;
  timestamp fixes priority.
- v2 (1-2 weeks): multi-family compliance cliff (all bundled-weight
  NIM images on L40S), Wilcoxon reported alongside sign test, optional
  interaction control for A3. arXiv versioning carries the update.

## v2 addendum (14.11.2026, same day)

R1's MAJOR (single model) is addressed: the compliance cliff was tested
across four families with the recorded prompts. Result: the cliff is
family-dependent --- Llama-3.1-8B (NIM bf16) and Mistral-7B (Ollama Q4)
fail on the single-action menu with different hallucination flavors
(invented produce_goods vs invented bribe with a wrong parameter name);
Gemma-2-9B and Phi-3.5 pass everything. All four comply on the richer
menu. Verdicts stable at 3/3 temperature-0 runs. Quantization differs
across serving stacks and is stated in the table. Venue norm is five to
nine families; four is below it, and the one-command harness is the
mechanism for outsiders to extend the table.

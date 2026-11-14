# Three Machine-Verified Anomalies from 100-Agent Political-Economy Games

Preprint v1 (November 14, 2026). Single-author empirical note: three
anomalies from preregistered experiments on a deterministic
political-economy engine, every number recomputed from published data
rows by a verifier that runs green in public CI.

- **Protocol-compliance cliff** (single-model case study): a frontier
  instruction-tuned model fails 0/100 first mandatory moves when the
  legal menu contains a single action, and complies on richer menus.
- **Volume-confounded concentration**: between-arm concentration
  comparisons invert the targeting signal (18/20 paired seeds); the
  conditional permutation test catches it on every seed.
- **Adversary coverage**: exhaustive enumeration of the influential
  policy subspace keeps the share cap (0.07 < 0.08) but breaches the
  HHI line (0.0302 > 0.03); the preregistered downgrade fires.

Verification: https://github.com/Jakisheff/world-100-grid (verify.py,
mutation journal, one-command model-compliance smoke harness).
Engine and preregistrations: https://github.com/Jakisheff/alashi
Self-refereeing record: REVIEWS.md.

Cite as: Amir Zhakyshev. Three Machine-Verified Anomalies from
100-Agent Political-Economy Games. Preprint v1, 2026.
DOI: assigned on release via repository settings.

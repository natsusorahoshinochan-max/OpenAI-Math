# Mathematical Research Notes

Organize the collection around reusable proof methods, supported by precise propositions and traceable applications. A reader should be able to assess a method's applicability, follow its use, and locate the underlying argument.

## Note types

| Kind | Purpose | Required content |
| --- | --- | --- |
| `paper` | Map a paper's proof structure | Problem, results, obstacles, proof routes, methods, dependencies, section coverage |
| `claim` | State a mathematical result | Objects, definitions, quantifiers, assumptions, conclusion, parameter dependencies, proof explanation |
| `method` | Explain a reusable mechanism | Obstacle, required structure, operations, justification, output, costs, scope, applications |
| `application` | Connect a method to a particular proof | Joint inputs, correspondence of objects and notation, concrete steps, outputs, costs, source locations |

A method may have multiple applications. Keep alternative proof routes as separate applications leading to the same claim.

## Method notes

Use these headings, with detail proportional to the argument:

1. **Obstacle** — What prevents the direct approach?
2. **Required structure** — Which objects, assumptions, and relations make the method work?
3. **Construction** — What operations are performed, and in what order?
4. **Mechanism** — Why do they work? Identify where each assumption is used and which properties are preserved.
5. **Output** — What estimate, construction, reduction, or conclusion results?
6. **Costs and scope** — Track losses, additional requirements, degeneracies, and relevant counterexamples.
7. **Applications** — Link to concrete uses.
8. **Related methods** — Explain composition, specialization, generalization, alternatives, or analogy.

Name methods by their operation and purpose, such as “Separating coupled sums through shared linear measurements.”

Keep broad strategies as navigation aids. Develop reusable mechanisms from concrete applications with explicit hypotheses and guarantees. When only the original construction is understood, retain that application and record the unresolved abstraction. Identify extensions proposed in the notes separately from source results.

Adapt technical detail to the subject: scales and norms in analysis; degree, precision, time, and space in algorithms; coefficient fields, degrees, and correspondence maps in geometry.

## Selection and granularity

Create a separate claim or application when it:

- supplies a reusable intermediate result;
- introduces a decisive construction or reduction;
- establishes a method's prerequisites or preserves a necessary property;
- controls an exponent, dimension range, regularity requirement, precision, or complexity;
- explains a limitation or a failed extension.

Select by mathematical role, including arguments inside proofs and remarks. Include classical tools when their use matters. Keep routine substitutions and repeated calculations within the surrounding explanation.

Preserve quantifiers, assumption scope, parameter ranges, strict inequalities, constant dependencies, and uniformity requirements. Define notation locally or link to its definition. Explain enough of the proof to reconstruct the key deductions, with source pointers for standard calculations.

Track quantities through the argument: where losses arise, how parameters are chosen, and what the final step requires.

## Relations and graph

Store relations in note metadata and generate the graph from them.

| Relation | Meaning |
| --- | --- |
| `requires` | Inputs jointly required by an application |
| `produces` | Claims or constructions established by an application |
| `uses_method` | Method instantiated by an application |
| `part_of` | Containing paper, proof route, or larger method |
| `specializes` | A specific case of the target |
| `generalizes` | An established extension of the target |
| `analogous_to` | A structural resemblance, with similarities and differences explained |

All `requires` entries in one application are joint premises. Represent alternative premise sets through separate applications.

Give each substantive relation a mathematical reason or source location in the body. Establish dependencies from the argument. Use analogy links for connections that remain heuristic.

## Files and sources

Write notes in English using Markdown and LaTeX.

| Path | Content |
| --- | --- |
| `notes/CONVENTIONS.md` | This standard |
| `notes/index.md` | Collection coverage and entry points |
| `notes/papers/<paper-slug>/` | Paper, claim, and application notes |
| `notes/methods/` | Reusable method notes |

Use one Markdown file per independent record. Give each record a unique, stable ID. Titles and classifications may evolve. Methods may belong to several fields.

Required YAML fields are `id`, `kind`, and `title`. Add source records and applicable relation lists. Relation targets are note IDs.

For repository sources, record the path, full commit hash, and a precise locator: a LaTeX label, theorem number, section, or page. For external sources, record a citation, version where available, URL or DOI, and locator.

Example application metadata, with illustrative IDs:

```yaml
---
id: example/measurement-separation
kind: application
title: Separating a sum by fixing shared measurements
sources:
  - path: preprints/<paper>/build/paper.tex
    commit: <full-commit-hash>
    locator: <lemma-label>
uses_method:
  - methods/shared-measurement-separation
requires:
  - example/measurement-design
produces:
  - example/factorized-sum
part_of:
  - example/paper
---
```

## Collection workflow

Work in passes across the collection:

1. **Map proofs.** Cover the main text and appendices; identify routes, obstacles, methods, and dependencies.
2. **Extract methods.** Write applications and supporting claims, then formulate reusable mechanisms.
3. **Check relations.** Match inputs, outputs, assumptions, and parameter changes against the source.
4. **Connect papers.** Compare related applications and organize methods as evidence accumulates.

Use paper families to recognize shared arguments, companion results, revisions, and alternative proofs. Extend classifications as new structures appear.

Each paper note records section coverage, completed passes, indexed material awaiting expansion, and unresolved steps. Record any independent proof checks with their scope and findings.

A completed note lets a new reader assess applicability, reconstruct the key argument, and trace every substantive claim and connection to its evidence.

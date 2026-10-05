# AGENTS.md

## Purpose of this repository

This repository contains the source of truth for the Water Intake Tracker
product requirements and system-level specifications.

Implementation code does not belong in this repository.

## Source of truth

- `docs/product.md` defines the current expected product behavior.
- Requirement IDs such as `MAIN-001`, `ADD-001`, and `DAY-001`
  must remain unique.
- Do not silently change existing product behavior while implementing
  or documenting another feature.

## Working with requirements

When adding or changing requirements:

- Make requirements observable and testable where possible.
- Prefer explicit values and behavior over vague descriptions.
- Separate product behavior from implementation details.
- Do not introduce technical implementation decisions into
  `product.md` unless they are themselves product requirements.
- Preserve existing requirement IDs.
- New requirements should receive new IDs.

## Ambiguities

If a requirement allows multiple materially different interpretations,
do not choose one silently.

Identify the ambiguity and request a product decision before treating
the requirement as final.

## Scope

Do not add functionality that is outside the currently documented
product scope unless explicitly requested.

## Role

When working in this repository, act as a specification and product
requirements assistant.

You may:
- identify ambiguities and contradictions;
- propose requirement wording;
- identify missing edge cases;
- update specifications after product decisions are made;
- derive acceptance criteria from approved requirements.

You MUST NOT:
- silently make product decisions when requirements are ambiguous;
- change existing product behavior without explicit approval;
- modify requirements merely to match an existing implementation.
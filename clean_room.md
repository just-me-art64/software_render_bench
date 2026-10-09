# Clean Room Policy for AGENTS

This repository is a clean-room software benchmark and development project. The goal is to evaluate software rendering systems and related tooling in a way that minimizes external contamination, copied logic, and hidden dependencies.

## Core Principle

We want all work to be created from scratch or implemented in-house unless there is a very explicit, documented exception. We do not want code that is merely re-exported, lightly adapted, or copied from existing projects without clear provenance.

## What "clean room" means here

For this repository, the expected standard is:

- Prefer original implementation over direct reuse.
- Prefer in-house logic, authored by the project, over vendored or copied code.
- Prefer small, understandable building blocks over large imported libraries when the goal is to study or benchmark rendering behavior.
- If a dependency is used, it must be justified, documented, and clearly separated from project-authored code.
- No hidden "code-left behind" patterns such as copying existing open-source implementations and changing names or comments while keeping structure, algorithms, or style from another system.

## Explicitly discouraged

The following are discouraged or disallowed unless explicitly approved in writing:

- Copying code from other repositories and pretending it is original work.
- Translating an implementation from another language without meaningful re-implementation and documentation.
- Reusing large blocks of third-party code for core benchmark logic.
- Adapting prior art in a way that preserves significant algorithmic structure, naming patterns, or implementation details without attribution and justification.
- Bringing in external render engines, libraries, or reference code as if they were authored in-house when they are not.
- Creating a benchmark that is effectively a re-wrapped clone of an existing project.

## Preferred approach

When implementing features:

- Write the algorithm from first principles.
- Build the minimal abstraction needed for the task.
- Document assumptions and trade-offs in the code and/or README.
- Keep the project understandable to future contributors and benchmark reviewers.
- Prefer a clear, deliberate implementation path over a fast copy-and-adapt path.

## What counts as acceptable

Acceptable examples include:

- A small utility written from scratch for parsing, scheduling, or image processing.
- Original data structures, render pipelines, or evaluation scripts designed for this repository.
- Standard external libraries used as tooling dependencies only when they are not part of the benchmark logic itself.
- External packages for packaging, testing, or developer ergonomics when clearly separated from the production benchmark implementation.

## What counts as not acceptable

Not acceptable without explicit approval:

- Porting a full render engine from another repository with only cosmetic edits.
- Reusing benchmark logic, data structures, or render algorithms from another project with minor rename changes.
- Checking in generated files or copied sources from another project as though they are original work.
- Keeping references to external code in comments or docs as a substitute for genuine in-house implementation.

## Review guidance for AGENTS

Before finalizing a change, ask:

- Is this code original or clearly authored in-house?
- Did we copy or heavily adapt logic from another project?
- Is there a clean boundary between third-party dependencies and our own code?
- If a dependency is used, is it necessary and documented?
- Would a reviewer be able to tell what was authored here versus imported?

If the answer to the above is unclear, the change should be revised.

## Summary

This repository should be built in a true clean-room manner: mostly from scratch, mostly in-house, and intentionally free of code-left code. The benchmark should reflect our own design decisions, our own implementation, and our own evaluation logic unless a dependency is justified and disclosed.

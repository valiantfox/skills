---
name: implement-v2
description: Implement changes from a developer-specified file and method-level design.
disable-model-invocation: true
---

# Implement from a developer's design

**Developer owns:** intended behavior and architecture: production files to create or modify, their methods or other relevant interfaces, and how they interact. For files without methods, specify their relevant changes instead.

**Agent owns:** implementation details within that design, test cases and test files, and running relevant checks. Follow any verification requirements the developer specifies.

1. Obtain the developer's design from their request or referenced documents. Inspect the affected code, callers, tests, and repository instructions.
2. If the design is incomplete, conflicts with the code, or requires an architectural decision or additional production file change, explain what is needed and ask the developer to decide or approve it. Wait for their answer before implementing the affected work.
3. Implement the agreed design and add or update tests as needed, preserving existing conventions and behavior outside its scope. Ask the developer before making any newly discovered architectural or additional production file change.
4. Run relevant tests and checks. Report the changes, results, and any unverified behavior or deviation.

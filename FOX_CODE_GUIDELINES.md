# Fox Code Guidelines

Apply these guidelines when implementing or reviewing code with a Fox skill.

- **Error handling.** Surface unexpected errors and handle them at a boundary that can respond meaningfully; use fallbacks only when they are expected behavior.
- **Backward compatibility.** Add backward compatibility only when the user explicitly requires it.
- **Explicit interfaces.** Introduce a separate interface type only when it serves a current need, not hypothetical flexibility.
- **Shared extraction.** Consider extracting shared logic on its third occurrence, when the underlying responsibility is genuinely shared. Extract sooner when necessary for correctness, security, or data integrity.

## Deep modules

- **Module:** Anything with an interface and an implementation, from a function to a tier-spanning slice.
- **Interface:** Everything a caller must know to use a module correctly, including invariants, ordering, errors, configuration, and performance.
- **Depth:** Leverage at the interface. A module is deep when a small interface exposes substantial behavior without requiring callers to understand its internal decisions.
- **Seam:** The place where a module's interface lives and behavior can be altered without editing at that place.
- **Adapter:** A concrete implementation that satisfies an interface at a seam.
- **Leverage:** The capability callers gain from a deep module relative to the interface they must learn.
- **Locality:** The concentration of related changes, knowledge, bugs, and verification in one place.
- **Cohesion:** Organize modules around cohesive business or technical responsibilities; keep their decisions and invariants inside, delegating supporting work where appropriate.

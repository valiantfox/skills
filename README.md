# skills

Agent skills for planning and implementing work.

- `fox-write-code`: Started as a fork of `mattpocock/implement` but was completly rewritten
- `fox-implement`: New skill
- `fox-implement-all`: Started as a fork of `mattpocock/implement-spec` but was completly rewritten
- `fox-plan` is a fork of `mattpocock/wayfinder` and uses `plans`
- `fox-refine` is a fork of `mattpocock/grilling`
- `fox-research`, `fox-prototype`, and `fox-tdd` are forks of the corresponding Matt Pocock skills
- `fox-spec-review` is a fork of `mattpocock/code-review` but was renamed because its focus is not on reviewing the code through a technical lense
- `fox-code-review` is a fork of `ponytail-review`

Thanks go out to Matt Pocock [mattpocock/skills](https://github.com/mattpocock/skills) and Dietrich Gebert [ponytail](https://github.com/DietrichGebert/ponytail) (MIT).

# Changes
#### Move `code-review` and `spec-review` calls out of the `implement` skill
Multiple times I ran into the scenario where a subagent would skip reviews, because something set it to `low-effort`. I verbatim got the response once `I skipped reviewing the code because this subsession is set to low-effort. If the main session wants it, it will do it`. 

This can be the agent provider, the harness or something else. But `code-review` and `spec-review` are *essential* to a refined piece of software and MUST not be skipped.

#### Move `codebase-design` vocabulary to global `FOX_CODE_GUIDELINES.md`
The most useful part I found here is the vocabulary, which is used by `tdd`. I want `implement` skill to also be aware of it and focus on building deep modules.

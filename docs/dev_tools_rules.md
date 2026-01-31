# Development Tools, Rules, Standards

## Tooling (proposed)

- Build system: CMake or Make (TBD)
- Compiler toolchain: GCC ARM or vendor toolchain (TBD)
- IDE: VS Code + extensions (TBD)
- Debug: SWD/JTAG (TBD)
- Docs: Markdown in `docs/`

## Coding standards

- C/C++ style: LLVM or Google style (TBD)
- Naming: clear, consistent; no cryptic abbreviations.
- Warnings: treat warnings as errors where feasible.
- Static analysis: clang-tidy or cppcheck (TBD).

## Version control rules

- Trunk-based or short-lived branches.
- Small, reviewable commits.
- Update `docs/milestones.md` and `docs/tasks.md` with progress.

## Documentation rules

- Keep requirements and specs updated with decisions.
- Use TODO markers for actionable gaps.
- Link related decisions in `docs/open_questions.md`.

## Testing standards (future)

- Unit tests for DSP utilities.
- Hardware-in-the-loop smoke tests.

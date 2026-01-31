# Development Tools, Rules, Standards

## Tooling (proposed)

- Build system: STM32CubeMX-generated project (STM32CubeIDE files)
- Compiler toolchain: GCC ARM (via STM32Cube toolchain/CLT)
- IDE: VS Code with STM32 extensions (installed)
- Debug: SWD/JTAG (TBD)
- Docs: Markdown in `docs/`
- RTOS: use ST-recommended RTOS (TBD, likely STM32Cube/FreeRTOS).

## Hardware change workflow (CubeMX)

- Treat the `.ioc` file as the source of truth for hardware configuration.
- Keep generated code isolated under `firmware/cubemx/`; avoid manual edits in generated files.
- If manual changes are needed, place them in user code sections or in separate modules under `firmware/`.
- For parallel hardware variants:
  - Keep a single primary `.ioc` and branch for experimental variants, or
  - Add a `firmware/cubemx/variants/` folder with variant `.ioc` files and document the differences.
- Always regenerate via CubeMX after hardware changes and commit both `.ioc` and generated output.

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

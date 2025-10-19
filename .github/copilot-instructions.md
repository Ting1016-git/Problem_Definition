# Copilot instructions for Problem_Definition

This repository is a small prototype for generating simple instrument music in plain-text form. The codebase currently consists of a single README describing inputs/outputs and high-level design goals. The instructions below are focused on making AI coding agents productive when working on this project.

1. Big picture
- Purpose: generate sequences of instrument notes (letters A-G) with durations, optionally adding lyrics/artist metadata later.
- Primary inputs: total length (number of notes or duration), musical style, instrument type.
- Primary output: plain-text note sequences (e.g., "A4 quarter, B4 half").

2. Architecture and code locations
- The repository currently contains only `README.md` at the repo root. New modules should be added under `src/` and tests under `tests/`.
- Suggested components:
  - `src/generator.py` or `src/generator.js`: core note-sequence generator.
  - `src/representations.py`: data models for Note, Duration, Instrument, Style.
  - `src/io.py`: CLI or simple input helpers that parse user-specified length/style/instrument.

3. Conventions & patterns
- Keep the code minimal and functional; prefer pure functions for generation (no global mutable state).
- Represent notes as objects/dicts with fields: `pitch` (A-G), `octave` (integer), `duration` (string/enum), and optional `lyric`.
- Duration should be a small enum: `whole`, `half`, `quarter`, `eighth`, `sixteenth`.

4. Developer workflows
- There are no build or test scripts yet. When adding Python code:
  - Provide a `requirements.txt` if external libs are needed.
  - Add tests and run with `pytest`.
  - Add a top-level `Makefile` or `pyproject.toml` later if project grows.

5. Integration & extension points
- Add a `--format` option to output either `text` (default) or `midi` (if MIDI lib added).
- If adding persistent storage or web service, place API code under `api/` and keep `src/` pure logic.

6. Examples to follow (if code added)
- A generator function signature (Python):
  `def generate(length: int, style: str, instrument: str) -> List[Note]:`
  - Should validate inputs and raise ValueError on bad parameters.

7. What to avoid
- Don't invent heavy frameworks; this project is a small learning prototype.
- Avoid using global random seeds unless tests explicitly set them.

8. When updating these instructions
- Keep them short (20-50 lines). Focus on concrete file paths, function signatures, and test commands.

If you'd like, I can: create an initial `src/` layout with a minimal generator, add unit tests, and add a `requirements.txt`. Tell me which language you prefer (Python/JavaScript) and whether you want a CLI or library-only interface.
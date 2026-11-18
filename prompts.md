# Prompts

## 2026-11-18

- Asked: Set up the top-level single-file web app structure and numbered project folders.
- Changed: Created `AGENTS.md`, `spec.md`, `prompts.md`, `index.html`, and folder README files for `00_planning`, `01_data`, `02_validation`, and `03_output`.
- Result: Worked.

- Asked: Commit the project setup.
- Changed: No project files changed; prepared the existing setup for a Git commit.
- Result: Worked.

- Asked: Read the current spec and provide an initial high-level assessment without changing code or the spec.
- Changed: Added this prompt entry only.
- Result: Worked.

- Asked: Work on the Inputs section, clarify missing inputs, units, ranges, defaults, and controls, and make no spec or code changes.
- Changed: Added this prompt entry only; no spec or code changes were made.
- Result: Worked.

- Asked: Add the reviewed Inputs-section changes to the spec.
- Changed: Expanded `## Inputs` in `spec.md` with support type, span, point loads, uniform loads, section material, steel shape and grade, lumber size, and their units, ranges, defaults, and controls.
- Result: Worked.

- Asked: Review the Calculations section for equations, units, undefined variables, and missing output calculations, without changing or building anything.
- Changed: Added this prompt entry only; no spec or code changes were made.
- Result: Worked.

- Asked: Expand the Calculations section with the equations and missing variables discussed.
- Changed: Added reaction equilibrium, shear and moment equations, elastic deflection requirements, sign conventions, unit conversions, maximum values, bending stress, and deflection-limit calculations to `spec.md`.
- Result: Worked.

- Asked: Review and update the Outputs section.
- Changed: Expanded `## Outputs` in `spec.md` with units and precision, the beam/load drawing, shear/moment/deflection diagrams, summary values, utilization ratios, separate pass/fail badges, live updates, and invalid-input behavior.
- Result: Worked.

- Asked: Perform a whole-spec gap review and add the W-shape and lumber dropdown tables.
- Changed: Added exact steel and lumber property tables, dropdown behavior, input validation details, downward-deflection sign convention, completed responsive Look and feel requirements, recomputed validation results, and clarified additional out-of-scope calculations in `spec.md`.
- Result: Worked.

- Asked: Read the spec and suggest 4–6 testable implementation stages, starting with a mockup and not writing code.
- Changed: Added this prompt entry only; no code or spec changes were made.
- Result: Worked.

- Asked: Add the six proposed build stages to the end of `spec.md`.
- Changed: Added `## Build stages` with six stages and their testing checks.
- Result: Worked.

- Asked: Build Stage 1 as a single-file HTML mockup with every spec input, output, and plot using realistic placeholder values.
- Changed: Replaced `index.html` with a responsive single-file mockup for beam inputs, section properties, beam/load drawing, summary results, shear/moment/deflection plots, and pass/fail cards. Added basic UI-only add/remove and steel/lumber switching behavior.
- Result: Worked.

- Asked: Commit the completed Stage 1 mockup.
- Changed: No project files changed; prepared the existing mockup and specification updates for a Git commit.
- Result: Worked.

- Asked: Build Stage 2 interactive inputs and validation only, with calculations kept separate from drawing code.
- Changed: Added live span/load/section validation, dynamic point-load and uniform-load rows, point-load direction controls, exact W-shape and lumber property updates, invalid-field feedback, and separate `BeamCalculations` and `BeamDrawing` JavaScript objects in `index.html`.
- Result: Worked.

- Asked: Commit the Stage 2 changes.
- Changed: No project files changed; prepared the existing Stage 2 implementation for a Git commit.
- Result: Worked.

- Asked: Build Stage 3 reactions, shear, moment, and beam/shear/moment diagrams.
- Changed: Added live support/reaction calculations, point and uniform load collection, simply supported and cantilever formulas, maximum shear/moment summaries, and dynamic beam/shear/moment SVG drawing in `index.html`. Deflection and pass/fail remain mock outputs pending Stage 4.
- Result: Worked.

- Asked: Fix the point-load arrows and add a top-right dancing GIF.
- Changed: Replaced the point-load SVG marker with centered downward/upward markers using fixed SVG user-space sizing, and added a small animated dancing figure in the top-right masthead.
- Result: Worked.

- Asked: Remove the header image and fix the point-load arrow again.
- Changed: Removed the top-right animation and replaced SVG marker-based point loads with explicit vertical line-and-triangle shapes for a reliably centered downward or upward arrow.
- Result: Worked.

- Asked: Commit the completed Stage 3 implementation.
- Changed: No project files changed; prepared the Stage 3 reactions, diagrams, and arrow correction for a Git commit.
- Result: Worked.

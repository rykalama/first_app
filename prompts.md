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

- Asked: Review four beam scenarios and verify which supplied hand-check answers match.
- Changed: No app or spec code changed; provided a review-only comparison of the scenarios.
- Result: Verification completed below.

- Asked: Adjust the website so Case 2 is unambiguously treated as a 10 kip point load at 5 ft.
- Changed: Preparing the app updates for the exact 10 kip/5 ft point-load case.
- Result: Commit requested before implementation.

- Asked: Commit the completed Stage 3 implementation.
- Changed: No project files changed; prepared the Stage 3 reactions, diagrams, and arrow correction for a Git commit.
- Result: Worked.

- Asked: Build Stage 4 deflection and section checks.
- Changed: Added built-in E/I/Sx/Fb calculations, numerical elastic deflection, maximum deflection and L/360 limit output, bending stress, utilization ratios, pass/fail badge updates, and a live deflection diagram in `index.html`.
- Result: Worked.

- Asked: Report whether all app behavior has been checked.
- Changed: Added this prompt entry only; no app changes were made.
- Result: Verification scope reported below.

- Asked: Commit the Stage 4 implementation.
- Changed: No project files changed; prepared the completed Stage 4 implementation for a Git commit.
- Result: Worked.

- Asked: Update the spec to match the final implementation changes that differed from the original spec.
- Changed: Added explicit point-load arrow geometry and a rule that no GIF or top-right entertainment image appears in the masthead.
- Result: Worked.

- Asked: Commit the Stage 5 implementation and spec updates.
- Changed: No project files changed; prepared the completed Stage 5 implementation and synchronized spec for a Git commit.
- Result: Worked.

- Asked: Build Stage 6 with a full validation pass.
- Changed: Fixed cantilever moment calculation in `index.html` and added this prompt entry for the Stage 6 validation pass.
- Result: Worked. Verified the 20 ft W12x26 uniform-load example and 10 ft cantilever uniform-load case, and recorded additional Stage 6 validation cases in `spec.md`.

- Asked: Commit the completed Stage 6 implementation and validation updates.
- Changed: No project files changed; prepared the Stage 6 cantilever correction and validation documentation for a Git commit.
- Result: Worked.

- Asked: Add dark mode to the specification.
- Changed: Added sun/moon theme-control, light-first and remembered-preference behavior, contrast, persistence, accessibility, responsive, and Stage 5 acceptance requirements to `spec.md`.
- Result: Worked.

- Asked: Also place the dark-mode requirements in the Look and feel section.
- Changed: Confirmed the existing `- Dark mode:` block is already under `## Look and feel`; no spec changes were needed.
- Result: Worked.

- Asked: Acknowledge the completed dark-mode spec update.
- Changed: Added this prompt entry only.
- Result: Worked.

- Asked: Add dark mode to the app.
- Changed: Added a top-right sun/moon button, light-first initial theme, saved theme preference with localStorage, live theme switching, dark CSS variables, and dark-mode form/SVG/status styling in `index.html`.
- Result: Worked.

- Asked: Commit the dark-mode implementation.
- Changed: No project files changed; prepared the completed dark-mode app update for a Git commit.
- Result: Worked.

- Asked: Build Stage 5 live behavior and polish.
- Changed: Added clearing of stale beam and result outputs for invalid inputs, Waiting states for pass/fail cards, empty-plot feedback, and live recalculation cleanup in `index.html`.
- Result: Worked.

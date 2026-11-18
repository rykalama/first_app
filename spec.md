# Beam Designer

## Purpose
Shear, moment, and deflection diagrams for a beam, with a check of
whether the beam is strong and stiff enough.

## Inputs
- Beam configuration
  - Units: not applicable
  - Range: Simply supported or Cantilever
  - Default: Simply supported
  - Control: Segmented control or dropdown
- Span
  - Units: ft
  - Range: 1 to 200 ft
  - Default: 20 ft
  - Control: Numeric input
- Point loads
  - Magnitude units: kip
  - Magnitude range: 0 to 100 kip
  - Location units: ft
  - Location range: 0 to the span
  - Zero-magnitude loads should be treated as removed.
  - Direction range: Down or Up
  - Default: No point loads
  - Direction default: Down
  - Control: Repeatable load rows with numeric magnitude and location fields, a direction
    dropdown, and add/remove buttons
- Uniform loads
  - Magnitude units: kip/ft
  - Magnitude range: 0 to 10 kip/ft
  - Start and end units: ft
  - Start and end range: 0 to the span
  - The start location must be less than or equal to the end location.
  - Zero-magnitude loads should be treated as removed.
  - Default: 1 kip/ft over the full span
  - Control: Repeatable load rows with numeric magnitude, start, and end fields,
    plus add/remove buttons
- Section material
  - Units: not applicable
  - Range: Steel or Lumber
  - Default: Steel
  - Control: Segmented control or dropdown
- Steel shape
  - Units: shape designation
  - Range: Common built-in W-shapes
  - Default: W12x26
  - Control: Dropdown with shape, moment of inertia, section modulus, and
    weight visible in the table below
- Steel grade
  - Units: not applicable
  - Range: A992 only
  - Default: A992
  - Control: Fixed label; no selection is required
- Lumber size
  - Units: nominal lumber dimensions
  - Range: Built-in preset lumber sizes
  - Default: 2x12
  - Control: Dropdown

### Built-in section properties

#### Steel W-shapes

Steel W-shapes use E = 29,000 ksi and allowable bending stress Fb = 30 ksi.

| Section | Ix (in^4) | Sx (in^3) | Weight (lb/ft) |
|---|---:|---:|---:|
| W8x10 | 30.8 | 7.81 | 10 |
| W10x12 | 53.8 | 10.9 | 12 |
| W12x26 | 204 | 33.4 | 26 |
| W14x22 | 199 | 29.0 | 22 |
| W16x26 | 301 | 38.4 | 26 |
| W18x35 | 510 | 57.6 | 35 |
| W21x44 | 843 | 81.6 | 44 |
| W24x55 | 1350 | 114 | 55 |

The shape dropdown should use these exact section values. The app should
also display the selected shape's Ix, Sx, weight, E, and Fb in the input
area or a nearby section summary.

#### Douglas Fir-Larch lumber

Douglas Fir-Larch No. 2 lumber uses E = 1,600 ksi and allowable bending
stress Fb = 0.900 ksi.

| Section | Ix (in^4) | Sx (in^3) |
|---|---:|---:|
| 2x8 | 47.63 | 13.14 |
| 2x10 | 98.93 | 21.39 |
| 2x12 | 177.98 | 31.64 |

## Calculations
- Use imperial units throughout: loads and reactions in kip, lengths and
  deflections in inches, distributed loads in kip/in for equations, E in ksi,
  I in in^4, and Sx in in^3.
- Convert the span and all load locations from ft to inches where needed.
- Apply the selected beam configuration and signs as follows:
  - Positive shear is upward on the left face of a cut.
  - Positive moment causes compression at the top of the beam.
  - Downward loads are positive in magnitude and enter the shear and moment
    equations with the appropriate sign defined by the selected sign convention.
- Reactions:
  - Require equilibrium of vertical forces and moments: sum(Fy) = 0 and
    sum(M) = 0.
  - For a simply supported beam, calculate RA and RB at x = 0 and x = L.
  - For a cantilever beam, calculate the support reaction and fixed-end moment
    at x = 0.
- Shear diagram:
  - V(x) = sum of all upward forces to the left of x minus
    sum of all downward forces to the left of x.
  - Express V in kip and determine maximum absolute shear as
    Vmax = max(|V(x)|).
- Moment diagram:
  - M(x) = sum of moments about x caused by loads and reactions to the left.
  - Express M in kip-ft for display and kip-in for stress calculations.
  - Determine Mmax = max(|M(x)|) and its location along the span.
- Deflection:
  - Calculate y(x) from elastic beam theory using
    EI y'' = M(x), with E and I selected for the beam section.
  - Apply simply supported boundary conditions y(0) = y(L) = 0, or fixed-end
    cantilever boundary conditions y(0) = y'(0) = 0.
  - Report deflection positive downward.
  - Determine ymax = max(|y(x)|) and its location along the span.
- Bending stress:
  - Convert Mmax to kip-in: Mmax,in = Mmax,kip-ft * 12.
  - Calculate fb = Mmax,in / Sx, with fb in ksi.
  - Compare fb to the built-in allowable bending stress Fb in ksi.
  - Bending passes when fb <= Fb.
- Deflection limit:
  - Convert the span to inches: Lin = Lft * 12.
  - Calculate the deflection limit: yallow = Lin / 360, in inches.
  - Deflection passes when ymax <= yallow.
- Overall result:
  - Report bending pass/fail and deflection pass/fail separately.

## Outputs
- Display all results using imperial units:
  - Reactions in kip
  - Shear in kip
  - Moment in kip-ft
  - Deflection in inches
  - Bending stress and allowable bending stress in ksi
- Round displayed numeric values to 2 decimal places.
- Beam and load drawing:
  - Show the beam span and support configuration.
  - Show every point load with its magnitude and position.
  - Render each point load as a centered vertical arrow: downward loads use a
    shaft ending in a downward triangle, and upward loads use a shaft ending
    in an upward triangle.
  - Do not use SVG markers for point-load arrows; use explicit line-and-triangle
    geometry so the arrow remains vertically aligned with the load.
  - Show every uniform load with its magnitude and loaded interval.
  - Label the support reactions in kip.
- Shear diagram:
  - Plot shear in kip against position along the span in ft.
  - Label Vmax and its location.
- Moment diagram:
  - Plot moment in kip-ft against position along the span in ft.
  - Label Mmax and its location.
- Deflection diagram:
  - Plot deflection in inches against position along the span in ft.
  - Label ymax and its location.
- Results summary:
  - Show each support reaction.
  - Show Vmax and Mmax.
  - Show ymax and the deflection limit yallow = L/360 in inches.
  - Show bending stress fb and allowable bending stress Fb in ksi.
- Pass/fail checks:
  - Show a separate bending badge for Pass or Fail.
  - Show a separate deflection badge for Pass or Fail.
  - Show the bending utilization ratio fb/Fb and its limiting ratio.
  - Show the deflection utilization ratio ymax/yallow and its limiting ratio.
  - Bending passes when fb <= Fb.
  - Deflection passes when ymax <= yallow.
- Update all drawings and summary values whenever an input changes.
- Do not display stale results after an input becomes invalid or incomplete;
  show validation feedback instead.

## Look and feel
- Inputs at the top.
- Diagrams and answers underneath.
- Place a BYU logo at the top of the page with "Construction Management"
  underneath it.
- Do not place a GIF, video, animated character, or other entertainment image
  in the masthead or at the top right of the page.
- Use a navy-blue background for the page header and navy, white, and
  restrained neutral accents for the interface.
- Keep the layout clean and professional, responsive, and readable on
  desktop and mobile widths.
- Do not use a full-page reload or navigation for calculations.
- Dark mode:
  - Place a sun/moon icon button in the top-right area of the masthead.
  - Use light mode on first use.
  - Remember the user's selected theme in browser local storage.
  - A saved theme choice overrides the first-use light-mode default.
  - Switch between themes immediately without reloading the page.
  - In dark mode, use dark page and card surfaces with light text and preserve
    navy accents.
  - Keep borders, gridlines, plots, SVG text, input fields, validation messages,
    and pass/fail states readable with sufficient contrast in both themes.
  - Use an accessible label such as "Switch to dark mode" or
    "Switch to light mode", and support keyboard activation and visible focus.

## Validation
20 ft simply supported W12x26 with 1 kip/ft: M = 50.0 kip-ft,
deflection 0.609 in.

- For this example, Ix = 204 in^4, E = 29,000 ksi, Sx = 33.4 in^3,
  and Fb = 30 ksi.
- The maximum moment is M = wL^2/8 = 50.0 kip-ft.
- The maximum deflection is 5wL^4/(384EI) = 0.609 in.
- The bending stress is fb = (50.0 kip-ft * 12 in/ft) / 33.4 in^3
  = 17.96 ksi, so bending Pass.
- The deflection limit is 240 in / 360 = 0.67 in, so deflection Pass.
- The numerical display should round M to 50.00 kip-ft and deflection
  to 0.61 in.

### Stage 6 validation cases
- 20 ft simply supported W12x26 with 1 kip/ft full-span uniform load:
  Mmax = 50.00 kip-ft and ymax = 0.609 in.
- 10 ft cantilever W12x26 with 1 kip/ft full-span uniform load:
  fixed-end moment magnitude = 50.00 kip-ft and ymax = 0.365 in.
- 20 ft simply supported W12x26 with one 5 kip downward point load at 10 ft:
  RA = RB = 2.50 kip and Mmax = 25.00 kip-ft.
- 20 ft simply supported 2x12 Douglas Fir-Larch lumber with 1 kip/ft:
  Mmax = 50.00 kip-ft and ymax should be greater than the W12x26 deflection
  because lumber has E = 1,600 ksi.
- Partial uniform loads, upward point loads, and multiple loads must obey the
  stated sign conventions and must update all reactions and diagrams.

## Out of scope
- Continuous beams
- Buckling
- Shear stress and shear-strength checks
- Torsion
- Load combinations and factor design
- Moving loads

## Build stages

### Stage 1: Page layout mockup
Build the static visual structure: header, BYU/Construction Management branding,
input panel, beam area, diagram placeholders, and results panel.

Check:
- Inputs appear above results.
- The layout is readable on desktop and mobile.
- Navy styling is consistent.
- Placeholder areas have sensible labels.

### Stage 2: Interactive inputs
Add beam configuration, span, steel/lumber selection, section dropdowns, and
repeatable point/uniform load controls. Add the supplied ranges and default values.

Check:
- Changing every control works.
- Adding and removing loads works.
- Invalid values show feedback.
- Switching between steel and lumber updates the available section properties.

### Stage 3: Reactions and beam diagrams
Implement reactions, shear, and moment calculations for simply supported and
cantilever beams. Draw the beam, loads, reaction arrows, shear diagram, and
moment diagram.

Check:
- Simple point and uniform load cases work and can be checked manually.
- Equilibrium, signs, units, and maximum shear/moment locations are correct.
- The supplied example reaches 50.00 kip-ft of maximum moment.

### Stage 4: Deflection and section checks
Use built-in E, I, Sx, and Fb values to calculate deflection, bending stress,
deflection limit, utilization ratios, and pass/fail badges.

Check:
- The W12x26 example produces about 17.96 ksi of bending stress and
  0.609 in of deflection.
- The 0.67 in deflection limit passes.
- Changing section properties changes the answers.

### Stage 5: Complete live behavior and polish
Connect all inputs and outputs so diagrams and summaries update immediately.
Finalize rounding, stale-result handling, section-property summaries, loading
arrows, labels, and mobile behavior.

Check:
- Invalid or incomplete inputs remove stale results and show clear feedback.
- Valid changes update every result without refreshing.
- The design is complete and remains usable at common desktop and mobile widths.
- Light and dark modes switch immediately, preserve readable contrast, and
  retain the user's choice after a reload.

### Stage 6: Full validation pass
Test the supplied example plus cantilevers, multiple point loads, partial uniform
loads, upward loads, lumber sections, and boundary/range cases.

Check:
- Results are mathematically reasonable and consistent across all cases.
- The validation example passes.
- No out-of-scope behavior appears.
- The app can be tested through GitHub Pages.
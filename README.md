# Temogram Simulator

An interactive web-based simulator for viscoelastic coagulation testing, replicating the output of **ROTEM Sigma** and **TEG 6s** devices. This educational tool allows users to visualize how different coagulation parameters affect temogram/thromboelastogram curves.

## Overview

This simulator provides realistic visual representations of:
- **ROTEM Sigma** - Rotational Thromboelastometry
- **TEG 6s** - Thromboelastography

Both devices are used in clinical settings to assess hemostasis and guide transfusion therapy.

## Features

### General Features
- ✅ Device selection splash page
- ✅ Real-time curve animation (20-second timelapse)
- ✅ Pause/Resume functionality
- ✅ Reset capability
- ✅ Export temograms as JPG images
- ✅ Authentic device interface replication
- ✅ Responsive design (mobile-friendly)

### ROTEM Sigma Simulator

**Input Parameters:**
- **FIBTEM A5** - Fibrinogen contribution to clot firmness (mm)
  - Normal range: 8-30 mm
- **EXTEM CT** - Clotting time (seconds)
  - Normal: <75 seconds

**Visual Features:**
- 2×2 panel layout matching real ROTEM device
- Four test channels: FIBTEM C, EXTEM C, INTEM C, APTEM C
- INTEM and APTEM panels crossed out (inactive)
- Color-coded traces:
  - FIBTEM: Magenta/pink filled curves
  - EXTEM: Blue filled curves
- Blue header bar with "ROTEM® Measurement module"
- White graph backgrounds with gray grid lines
- Amplitude range: -60mm to +60mm
- Time range: 0-50 minutes

### TEG 6s Simulator

**Input Parameters:**
- **CK R Time** - Reaction time before clot formation (minutes)
  - Normal: <7.6 minutes
- **CK MA** - Maximum amplitude for Kaolin channel (mm)
  - Normal range: 52-69 mm
- **CFF A10 (MA)** - Functional fibrinogen amplitude (mm)
  - Normal range: 17-40 mm

**Visual Features:**
- Dark background interface matching real TEG 6s
- Color-coded test buttons on left:
  - CK (Red) - Active
  - CRT (Purple) - Crossed out
  - CKH (Green) - Crossed out
  - CFF (Cyan/Blue) - Active
- Hill equation curve morphology for realistic clot formation
- Parameter display panel on right side
- Amplitude range: -100mm to +100mm
- Time range: 0-100 minutes
- "Gerätename: TEG 6s" label

## Usage

### Getting Started

1. Open `temogram-simulator.html` in any modern web browser
2. Select either **ROTEM Sigma** or **TEG 6s** from the splash page

### Running a Simulation

#### For ROTEM:
1. Enter **FIBTEM A5** value (e.g., 15)
2. Enter **EXTEM CT** value (e.g., 60)
3. Click **Run** button
4. Watch the curves animate over 20 seconds
5. Use **Pause** to pause/resume animation
6. Click **Reset** to clear and start over
7. Click **Save as JPG** to export the image
8. Click **Start Again** to return to device selection

#### For TEG:
1. Enter **CK R Time** value (e.g., 5.0)
2. Enter **CK MA** value (e.g., 60)
3. Enter **CFF A10** value (e.g., 25)
4. Click **Run** button
5. Watch the curves animate over 20 seconds
6. Use **Pause** to pause/resume animation
7. Click **Reset** to clear and start over
8. Click **Save as JPG** to export the image
9. Click **Start Again** to return to device selection

## Technical Details

### Curve Algorithms

**ROTEM Curves:**
- **FIBTEM**: Starts after ~50% of CT time, rises to A5 value using sigmoid function
- **EXTEM**: Starts after CT time, rises to approximately 35mm using sigmoid function
- Both curves are filled symmetric spindles (positive and negative amplitudes)

**TEG Curves:**
- **CFF**: Starts at time 0, uses Hill equation with n=3 to reach A10 value
- **CK**: Flat until R time, then uses Hill equation with n=3 to reach MA value
- Hill equation: `amplitude = (max × t^n) / (k^n + t^n)`
- Symmetric outline curves (not filled)

### Technology Stack
- Pure HTML5, CSS3, and JavaScript
- Canvas API for rendering
- No external dependencies
- Single-file application

### Browser Compatibility
- Chrome/Edge (recommended)
- Firefox
- Safari
- Any modern browser with Canvas support

## Clinical Context

### ROTEM Parameters
- **FIBTEM (Fibrinogen Temogram)**: Assesses fibrinogen contribution to clot strength by platelet inhibition
- **EXTEM (External Activation)**: Screens extrinsic pathway and detects coagulation factor deficiencies
- **CT (Clotting Time)**: Time until clot begins to form (reflects clotting factor activity)
- **A5**: Amplitude at 5 minutes (reflects fibrinogen levels)

### TEG Parameters
- **CK (Kaolin)**: Standard kaolin-activated whole blood test
- **CFF (Citrated Functional Fibrinogen)**: Measures functional fibrinogen contribution
- **R Time**: Reaction time - time until initial fibrin formation
- **MA (Maximum Amplitude)**: Greatest clot strength achieved
- **A10**: Amplitude at 10 minutes

## Educational Use

This simulator is designed for:
- Medical education and training
- Understanding viscoelastic testing principles
- Demonstrating how parameters affect curve morphology
- Preparing healthcare professionals for device interpretation
- Research presentations and teaching materials

**Note**: This is a simulation tool for educational purposes only. It should not be used for clinical decision-making or patient care.

## File Structure

```
temogram-simulator.html
├── HTML Structure
│   ├── Splash page
│   ├── ROTEM simulator page
│   └── TEG simulator page
├── CSS Styling
│   ├── Responsive layout
│   ├── Device-specific themes
│   └── Canvas containers
└── JavaScript Functions
    ├── Device selection
    ├── Grid drawing (ROTEM & TEG)
    ├── Curve animation (ROTEM & TEG)
    ├── Control functions (run/pause/reset)
    └── Export functionality
```

## Customization

### Modifying Normal Ranges
Edit the `<span class="unit">` text in the HTML to update displayed normal ranges.

### Adjusting Curve Parameters
- **ROTEM**: Modify `maxAmplitude` and sigmoid parameters in `animateRotem()`
- **TEG**: Adjust Hill coefficient `n` and `timeToMax` values in `animateTeg()`

### Changing Colors
- **ROTEM**: Update `color` properties in panel configurations
- **TEG**: Modify `strokeStyle` values in curve drawing functions

## Limitations

- Simplified curve algorithms (approximations of real device output)
- Limited to two parameters per device (expandable)
- No lysis phase simulation
- No time-dependent amplitude changes after MA
- Static K time and angle calculations

## Future Enhancements

Potential additions:
- [ ] Additional ROTEM tests (INTEM, APTEM, HEPTEM)
- [ ] Additional TEG channels (CRT, CKH)
- [ ] Lysis curves (LY30, LY60)
- [ ] Angle and K time inputs
- [ ] Side-by-side comparison mode
- [ ] Interpretation guidelines
- [ ] Clinical scenarios library
- [ ] Print-optimized layouts

## Version History

**Version 1.0** (Current)
- Initial release
- ROTEM Sigma with FIBTEM/EXTEM
- TEG 6s with CK/CFF
- 2×2 panel layout for ROTEM
- Hill equation curves for TEG
- Export functionality

## License

This educational tool is provided as-is for non-commercial educational purposes.

## Acknowledgments

Developed to replicate the visual output of:
- ROTEM® (Werfen/Tem Innovations)
- TEG® (Haemonetics Corporation)

Device interfaces and methodologies are proprietary to their respective manufacturers.

## Contact & Support

For questions, suggestions, or bug reports regarding this simulator, please refer to the development documentation or contact the maintaining institution.

---

**Disclaimer**: This simulator is for educational purposes only and does not replace proper training on actual ROTEM or TEG devices. Always follow manufacturer guidelines and institutional protocols when interpreting real patient results.

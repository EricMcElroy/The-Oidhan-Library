# DUAL-LAYER LIGHT PIPE DISPLAY SYSTEM

### INDEPENDENT OPTICAL CHANNELS IN LAYERED ACRYLIC FOR CONSUMER PRODUCT APPLICATIONS

**Author:** Eric Don McElroy **Date:** 2026-06-07 **Contact:**
Eric.mcelroy@gmail.com \|
[[https://substack.com/@eskamick]{.underline}](https://substack.com/@eskamick)
**Version:** 1.0 **Status:** Public Release / Prior Art Disclosure

## Abstract

Traditional consumer products utilizing edge-lit acrylic technology
suffer from limited visual complexity. Standard single-layer
illumination methods restrict light dispersion to a single geometric
plane, resulting in flat, uniform glow effects that look nearly
identical across different designs. This homogeneity restricts the
premium aesthetic appeal of edge-lit components in high-end consumer
electronics and display systems.

This white paper establishes a technical framework for a *Dual-Layer
Light Pipe Display System*. By separating two discrete, laser-etched
acrylic sheets with an intentional air gap and supplying independent
light channels, the system isolates optical paths to create
multi-dimensional depth, selective illumination zones, and interactive
layered glow effects impossible to achieve in single-layer
configurations.

## Problem Statement

The integration of light-pipe illumination in consumer interfaces and
display hardware faces several structural design limitations:

1.  **Lack of Visual Depth:** Single-layer acrylic displays can only
    > render flat, two-dimensional graphics because all etched elements
    > share an identical optical plane.

2.  **Optical Saturation:** When multiple design features are etched
    > onto a single panel, illuminating one feature inadvertently bleeds
    > light into adjacent areas, preventing dynamic or state-dependent
    > visual layering.

3.  **Product Homogeneity:** Because the underlying physics of a single
    > homogeneous layer limits the aesthetic variation, consumer
    > products using basic edge lighting appear visually
    > interchangeable, suppressing their perceived value.

## Concept Overview

The system isolates independent optical paths across separate structural
layers to generate a rich, three-dimensional visual hierarchy from a
static display footprint.

\[ VISUAL VIEWPORT / VIEWER \]\
=======================================================\
\[ LAYER 1: FOREGROUND ACRYLIC PANEL (3mm Cast) \]\
- Direct Vector Laser Etching / Diffusion
Design\[span_13\](start_span)\[span_13\](end_span)\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
\[ ISOLATION BOUNDARY: OPTICAL AIR GAP \] (No
Crosstalk)\[span_14\](start_span)\[span_14\](end_span)\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
\[ LAYER 2: BACKGROUND ACRYLIC PANEL (3mm Cast) \]\
- Secondary Texturing / Layered Graphic
Elements\[span_15\](start_span)\[span_15\](end_span)\
=======================================================\
\[ INDEPENDENT LED EDGE LIGHTING SOURCE SYSTEM \]

### Technical Mechanism

-   **Total Internal Reflection Control:** Introduced light travels
    > through the homogeneous acrylic medium via total internal
    > reflection, escaping only where precise surface disruptions---such
    > as laser cuts or vector etches---scatter the waves toward the
    > viewer.

-   **Crosstalk Mitigation:** The mechanical air gap structurally
    > separates the panels, ensuring that light introduced into one
    > layer cannot refract into the adjacent layer, effectively
    > maintaining total optical isolation.

-   **Dynamic Graphic Layering:** Because the layers interact visually
    > without optically interfering, different etch patterns can be
    > illuminated independently or simultaneously to display multi-state
    > graphics, shifting backgrounds, or deep contextual alerts.

## Why This Works --- Feasibility Basis

The structural and financial viability of this architecture rests on
standard fabrication parameters and highly predictable optical physics.

-   **Predictable Diffusion Density:** The intensity and luminance of
    > the glow effect are controlled directly by adjusting the vector
    > depth and line density during the laser etching process.

-   **High-Yield Manufacturing Compatibility:** Commercial CNC laser
    > cutters handle both the perimeter profiling and surface texturing
    > of standard 3mm cast acrylic sheets in a single processing run,
    > making production fast and highly repeatable.

-   **Linear Transmission Integrity:** Low-voltage 5V addressable LED
    > strips, mounted flush against the polished edges of the acrylic
    > panels, provide a sufficient luminous flux to fully illuminate
    > complex etched patterns up to approximately 200mm away from the
    > emitter edge.

## Known Engineering Challenges

### Surface Reflection and Internal Ghosting

While the air gap prevents internal light bleeding between layers,
highly polished external surfaces can still cause minor external
reflections, causing visual \"ghosting\" under harsh ambient light. To
maximize contrast and clarity, the front face of the foreground panel
may require a subtle anti-reflective coating or specific orientation
tuning relative to the viewer\'s primary line of sight.

### Edge Sealing and Dust Ingress

Over time, atmospheric dust or moisture can settle within the internal
air gap between the two acrylic sheets, creating permanent dark spots or
accidental light-scattering nodes. The final physical enclosure must
incorporate a sealed perimeter gasket or interlocking bezel that
encloses the air gap without putting direct mechanical pressure on the
polished light-entry edges.

## Suggested Development Path

### Phase 1: Material and Etch Optimization

-   Run a series of laser-etch calibrations on cast acrylic to establish
    > the optimal speed and power curves for uniform light scattering.

-   Test different air-gap tolerances (ranging from 0.5mm to 3mm) using
    > precision shims to determine the ideal balance between physical
    > compactness and crisp visual separation.

### Phase 2: Application-Specific Shell Integration

-   Integrate the dual-layer array into targeted consumer electronics
    > housings, such as the back panel of a premium charging station or
    > automated desktop accessories.

-   Configure microcontroller firmware (e.g., via an ESP32 or Arduino
    > architecture) to drive independent, pulse-width-modulated (PWM)
    > LED channels, enabling smooth cross-fading and state-dependent
    > lighting transitions between the foreground and background layers.

### Phase 3: Commercial Scale Deployment

-   Partner with commercial plastic service bureaus to outsource mass
    > profile cutting and baseline etching, reserving custom, low-volume
    > graphic etching for localized final assembly.

## Why Now

Consumer demand for high-end, tactile, and visually expressive desktop
environments is expanding rapidly. Meanwhile, high-precision desktop
laser cutters and efficient addressable LED drivers have become standard
maker tools. Utilizing dual-layer optical isolation allows designers to
move past basic single-plane lighting and manufacture genuinely complex,
three-dimensional ambient interfaces with minimal tooling investment.

## Appendix: Available Technology & Prior Art

### Target System Applications

The dual-layer display system functions as a modular platform with broad
product cross-compatibility:

-   **Premium Charging Nodes:** Back panels featuring responsive ambient
    > iconography and floating background indicators (e.g., Acrylic Qi
    > Charging Stand alignment).

-   **Depth-Enhanced Signage:** Commercial branding boards featuring
    > layered typography and rich parallax depth effects.

-   **Architectural Elements:** Interior accent panels, smart luxury
    > display cases, and expressive product presentation backdrops.

### Material Substrate Specifications

Cast acrylic is specified exclusively over extruded acrylic due to its
superior molecular structure and uniform optical density. Extruded
variants possess internal stress lines from manufacturing that cause
unpredictable light scattering, whereas cast acrylic provides perfectly
clean, repeatable light pipe paths.

## Author Note

The strength of this dual-layer system is its structural simplicity and
high aesthetic scalability. By changing only the vector art files
uploaded to a standard laser cutter, a builder can pivot from
manufacturing minimalist technical telemetry displays to ornate,
stylized art pieces without altering a single element of the physical
framework, LEDs, or enclosure architecture.

This document is released as a public prior art disclosure. The author
asserts origination of the concept as described herein as of the date
above. No patent is claimed. Builders are free to develop, implement,
and commercialize this concept without restriction or licensing
requirement. Attribution appreciated but not required.

© Eric Don McElroy --- Released to the public domain.

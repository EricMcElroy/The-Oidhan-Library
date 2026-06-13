# PEPPER\'S GHOST HOLOGRAPHIC CLOCK STATION

### A CONSUMER AMBIENT DISPLAY AND CHARGING STATION USING PEPPER\'S GHOST OPTICAL ILLUSION

**Author:** Eric Don McElroy **Date:** 2026-06-07 **Contact:**
Eric.mcelroy@gmail.com \|
[[https://substack.com/@eskamick]{.underline}](https://substack.com/@eskamick)
**Version:** 1.0 **Status:** Public Release / Prior Art Disclosure

## Abstract

Consumer desk accessories and charging devices are historically
functional but visually inert. The premium market segment for
compelling, multi-dimensional ambient display objects---items that
function as visual art pieces while serving a daily utility---is highly
underserved at accessible consumer price points. Existing
pseudo-holographic displays are either prohibitively expensive
industrial units or fragile, single-purpose novelties.

This white paper establishes the architecture for an integrated charging
station and ambient timepiece using a optimized Pepper\'s Ghost optical
system. By pairing an inexpensive high-brightness display module with
angled teleprompter film and a dark, light-absorbing contrast enclosure,
the system projects floating graphics, clock telemetry, and real-time
particle simulations directly into the user's field of view.

## Problem Statement

Desktop interface design and premium consumer electronics face three
primary challenges:

1.  **Visual Flatness:** Modern desktop screens and smart displays rely
    > on standard, flat LCD or OLED panels encased in plastic bezels,
    > offering zero true spatial depth or ambient novelty.

2.  **High Cost of Multi-Planar Optics:** Volumetric or true holographic
    > projection systems require specialized lasers, high-speed rotating
    > mirrors, or expensive optical glass arrays, making them unviable
    > for commercial consumer goods.

3.  **Ambient Light Washout:** Simple reflective illusion setups
    > frequently fail in normal residential and commercial environments
    > due to ambient light flooding the viewing chamber, which washes
    > out the contrast and destroys the depth illusion.

## Concept Overview

The system utilizes a 19th-century stage illusion technique modernized
via digital microcontrollers and high-density display sources to
generate floating imagery within a contained desktop footprint.

\[ VIEWER LINE OF SIGHT \]\
│\
▼\
┌─────────────────────────────────────┐\
│ \[ DARK BOX ENCLOSURE \] │\
│ (Three-Sided Light-Absorbing Cavity)│\
│ │\
│ / \[REFLECTIVE INTERFACE\] │\
│ / (45° Teleprompter Film) │ \<── Floating Image\
│ / │ Plane Created\
└────╪────────────────────────────────┘\
│\
\[ HIDDEN CAVITY SOURCE \]\
(High-Brightness OLED/LCD)

### The Pepper\'s Ghost Optical Assembly

-   **The Reflector:** A partially reflective teleprompter film
    > (configured at a 30/70 or 50/50 reflection-to-transmission ratio)
    > is applied directly to an angled acrylic substrate, mounted at
    > approximately 45 degrees relative to the viewer\'s horizontal line
    > of sight. This satisfies geometric reflection requirements at a
    > fraction of the cost of optical glass.

-   **The Contrast Enclosure:** A three-sided dark box enclosure
    > (shielding the back and both sides of the viewing volume) absorbs
    > stray ambient light, maximizes the display\'s contrast ratio, and
    > maintains sharp daytime visibility for high-contrast graphics.

-   **The Illusion Matrix:** An open-front viewing volume, optimized for
    > standard desk and entryway viewing distances of 0.5 to 2 meters,
    > allows the viewer to see objects behind the glass while the hidden
    > display reflects off the surface, making graphics appear to float
    > natively in space.

## Why This Works --- Feasibility Basis

The system\'s technical framework relies on high-brightness
micro-displays and low-cost, high-performance microcontrollers.

-   **Hidden Emission Source:** A small, ultra-bright LCD or OLED module
    > is recessed completely inside the base cavity, facing upward into
    > the angled mirror array to hide the true source pixel grid from
    > the user\'s view.

-   **Computationally Trivial Particle Systems:** Real-time
    > environmental particle systems---such as drifting embers, falling
    > snow, fireflies, and cosmic dust---are processed directly on an
    > inexpensive ESP32 microcontroller.

-   **Perceived Depth Layering:** Time telemetry digits or analog clock
    > hands are rendered digitally so that particle systems drift both
    > in front of and behind the time plane, creating a strong parallax
    > effect and a convincing illusion of three-dimensional depth.

## Known Engineering Challenges

### Heat and Geometry Constraints of Recessed Electronics

Mounting a high-brightness panel and an ESP32 inside a tight,
unventilated base cavity alongside wireless charging coils can cause
rapid thermal saturation. The internal base geometry must feature
dedicated ventilation channels to draw heat out through the rear of the
unit, preventing the display panel from degrading or shifting colors
over prolonged use.

### Screen-to-Film Alignment and Trapped Air Bulbs

Applying teleprompter film to an acrylic backing sheet without
introducing optical distortion requires strict clean-room assembly or
wet-application workflows. Any microscopic air pocket or dust particle
trapped behind the film will cause a lens flare effect from the
high-brightness display, breaking the holographic illusion.

## Suggested Development Path

### Phase 1: Microcontroller and Optical Benchmarking

-   Flash an ESP32 microcontroller to drive high-frame-rate SPI or I2C
    > display interfaces.

-   Author basic particle rendering scripts to test the brightness
    > contrast when reflected off 50/50 teleprompter film.

### Phase 2: Dual-Layer Acrylic Charging Integration

-   Merge the Pepper\'s Ghost cavity directly into the physical
    > footprint of the *Dual-Layer Acrylic Charging Stand* architecture.

-   Use the dual-layer acrylic light pipes to provide a subtle ambient
    > background glow while the Pepper\'s Ghost system projects the
    > primary foreground telemetry.

-   Wire the entire device to run from a single unified USB-C power
    > input, managing power routing for the display, the ESP32, the
    > edge-lit LEDs, and the Qi induction coils simultaneously.

### Phase 3: Firmwaring and Network Features

-   Connect the ESP32 to local WiFi networks to enable automated Network
    > Time Protocol (NTP) clock synchronization, live weather data
    > scraping, and mobile notification casting.

## Why Now

The open-source availability of advanced graphics libraries for
microcontrollers allows developers to easily create complex particle
animations on sub-\$5 chips. Combined with the availability of low-cost,
high-contrast OLED panels from the smartphone supply chain, builders can
now manufacture high-end holographic desk ornaments that once required
expensive industrial manufacturing.

## Appendix: Available Technology & Prior Art

### Ambient Mode Profiles

To adapt to changing room illumination, the system features
state-dependent display profiles:

-   **Daytime Profile:** High-contrast, simplified vector shapes---such
    > as clean clock faces and bold telemetry indicators---optimized to
    > punch through strong ambient light.

-   **Nighttime Profile:** Deep, complex particle animations, floating
    > 3D wireframe geometries, and slow-moving ambient patterns that
    > minimize room glare while maintaining a smooth visual flow.

## Author Note

This system succeeds by transforming a historically large, fragile
theatrical trick into a functional desktop utility. By anchoring the
optical cavity to a high-use tool like a smartphone charger, the device
ceases to be a short-lived novelty and becomes a permanent, high-value
element of the user\'s daily workspace.

This document is released as a public prior art disclosure. The author
asserts origination of the concept as described herein as of the date
above. No patent is claimed. Builders are free to develop, implement,
and commercialize this concept without restriction or licensing
requirement. Attribution appreciated but not required.

© Eric Don McElroy --- Released to the public domain.

*Note: There is **one** system remaining in the file portfolio (\"6.
Salvage-Based XY Soldering Gantry\"). Let me know when you are ready to
pull it.*

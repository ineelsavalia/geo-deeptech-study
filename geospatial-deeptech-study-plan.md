# Geospatial & Deep Tech — 18 Month Study Plan

> **Note for any AI reading this file.** This is a personal 18-month study and build plan for a geospatial deep-tech startup founder in Gujarat, India. It holds 587 topics and build steps across 24 modules, plus the full source library. Read the "Plan context" section first — it states the goal, the time budget, the learning method, the balloon design decisions with their physics constraints, the hardware on hand, and how to teach this person. A companion file, **Teaching Contract — Geospatial & Deep Tech**, holds the per-module teaching briefs: what to teach, how deep, the tone, the examples and the hard questions. Use both together when they are both available.

**The goal.** In 18 months: design the full system for a satellite-data and GeoAI product, judge engineers' work with authority, and build and fly a returning stratospheric balloon payload personally.

---

## Topic codes

Every one of the 587 topics has a code. Quote a code to an AI and ask it to teach that topic.

**Format:** `M14-C05` means **module 14**, topic **group C** (the third group in that module), **item 5** in that group.

- The module number is always two digits: `M01` to `M24`.
- Group letters run A, B, C and so on, in the order the groups appear inside the module.
- The item number is always two digits, counting from 01.

**Using one:** *"Teach me M08-D07."* The AI should resolve the code against the module list below, find the exact topic, and teach that one thing. The companion file, **Teaching Contract — Geospatial & Deep Tech**, says how deep to go and how to teach it.

**If a code does not resolve,** say so and name the nearest valid code in that module. Do not guess which topic was meant.

The code is also the checkbox id in the HTML tracker, so an exported progress file lists completed topics by code under `completed_topic_codes`.

---

## Plan context

### Who this is for

- **Role:** founder and CEO of a geospatial deep-tech startup
- **Location:** Gujarat, India
- **Business:** using satellite data, building satellites, and building GeoAI software
- **Existing knowledge:** some GIS; little else
- **On coding:** does not intend to write code by hand; uses AI for implementation. Priority is system design and architecture.
- **Budget:** INR 500000 to 600000 across the 18 months, covering parts, test and flights

### Time budget

- 7 days a week, 2 hours a day
- one day per week is 1 hour of review and building only, no new topics
- Session split: 60 min learn, 45 min build or practise, 15 min review
- Total: about 810 study hours

### Learning method

1. Big picture before details — learn how the whole system fits together first
2. Ask why until the answer is physics or a number, not industry convention
3. Every topic ends in something built or calculated
4. Explain it back in own words after each topic
5. Weekly spaced review of older topics
6. Study past failures to build judgement fast

### Hardware already on hand

- Orange Pi 4 Pro 6GB with 3 TOPS NPU
- Raspberry Pi Pico 2 W + LAFVIN development kit
- Nooelec RTL-SDR v5 + SAWbird+ NOAA LNA + telescopic V-dipole
- BNO085 9-DOF IMU
- NEO-7M GPS modules
- A2212 1000KV brushless motor + 30A ESC + propellers
- MG996R servos
- BPW34 photodiodes (sun sensing)
- 8-channel 24MHz logic analyser

### The balloon programme

**Status:** concept, not final design

- **Version 1:** camera, sensors, live telemetry and streaming from ~35 km, wings for controlled descent, propellers deployed below ~10 km for powered return to base
- **Version 2:** flown ~2 months after v1; wide-area weather and imaging profile positioned as a reusable alternative to disposable radiosondes
- **After that:** feeds directly into a CubeSat prototype design
- **Regulatory:** DGCA permission for an unmanned free balloon with powered return; to be applied for near the end of the study period

**Physics constraints already agreed, which must not be relitigated as if unsettled:**

- Air at 35 km is ~150x thinner than sea level, so propellers produce ~1/150 of sea-level thrust and cannot provide meaningful thrust or attitude authority up there
- Attitude control above ~10 km must use momentum/reaction wheel or aerodynamic control surfaces, the same technique a satellite uses
- Winds at altitude can displace the payload 100-200 km during descent, so controlled descent, not powered cruise, does the main work of getting home

### How an AI should help

- Teach from first principles with real numbers, not analogies alone
- Use plain language; avoid jargon unless defining it
- When the learner is wrong about physics, say so directly with the number
- Connect every topic back to either the balloon build or the GeoAI product
- Do not rewrite this plan wholesale; make surgical edits when asked

### Where the study materials are

Sources appear in two places in this document: a reading list under each module ("Where to learn it"), and a global library in the **Study materials** section near the end.

**Source types:** book, free course, primary standard or handbook (usually a free PDF), open dataset, free software, paper archive or community.

**How to use them:**

- When teaching a module, fetch that module's res urls first and teach from the actual source rather than from memory.
- Prefer the primary document over any summary of it: the NASA SoA report, CubeSat 101, the CubeSat Design Specification, GEVS, ECSS, CCSDS and OGC are all free and authoritative.
- For any practical exercise, pull a real scene over Gujarat from the open data sources rather than using a toy dataset.
- Books carry no url. Do not invent one. Quote sparingly and paraphrase; point the learner to the chapter instead of reproducing it.
- If a url has moved or cannot be reached, say so plainly and suggest the nearest live equivalent rather than guessing a new address.
- Links were assembled in October 2026 and were not all individually verified; treat a dead link as a stale link, not as evidence the resource is gone.

### Progress tracking

Progress is not stored in this file. The learner keeps it in the companion HTML tracker, in browser storage under the key `geo-deeptech-plan-v1`. To know where they are, ask them to export that progress and share the JSON; its keys match the format `the topic code itself, e.g. M14-C05`.

---

## How top operators learn

**Big picture first** — Learn how the whole system fits together before any detail. You are designing architecture, not components.

**Ask why to the bottom** — Keep asking until the answer is physics or a number. 'That's how the industry does it' is where most competitors stop.

**Build every week** — Every topic ends in something calculated, measured or soldered. Knowledge that never touched hardware is not judgement.

**Explain it back** — Say it in plain words with no jargon. If you cannot, you have not learned it — you have only read it.

**Review on a loop** — Fifteen minutes a day on older topics. Without it, month 3 is gone by month 9.

**Study failures** — Post-mortems of dead missions teach more per hour than any textbook. This is where engineering judgement actually comes from.

### The two hours

| Block | What happens |
|---|---|
| 60 minutes | Learn the topic — read, watch, or work through it with an AI tutor |
| 45 minutes | Build, calculate, or test something with it |
| 15 minutes | Explain it back in your own words, then review two older topics |
| Lighter day | One day a week: 1 hour of review and building only, no new topics |

---

## The six stages

Order is not arbitrary. Each stage is built on numbers established in the one before it, and each ends in something that flies, transmits or computes.

### Stage 0 · Month 1 — Foundations

The maths and physics you skipped, plus how a satellite system actually hangs together. One month, no shortcuts.

**Build milestone:** Decode a live weather satellite with your RTL-SDR and V-dipole.

### Stage 1 · Months 1–3 — Orbits & mission design

Everything downstream is designed against the orbit. Get it wrong and every later budget rests on a false assumption.

**Build milestone:** Predict and log real passes; write your first mission requirement document.

### Stage 2 · Months 3–6 — The three budgets

Mass, power, link. This is the working language of satellite design, and where most founders get out-argued by their own engineers.

**Build milestone:** Full power budget and link budget for your own payload, on paper, defended.

### Stage 3 · Months 6–11 — Subsystems

Pointing first — it is hardest and touches everything. Thermal after power, since heat follows electronics. Then the brain.

**Build milestone:** Single-axis pointing demo: BNO085 plus a reaction wheel, holding an angle.

### Stage 4 · Months 9–14 — Payload, data & GeoAI

Optics sets your resolution ceiling. Calibration makes imagery trustworthy. GeoAI is where your company actually earns money.

**Build milestone:** A model running on the Orange Pi NPU, screening and georeferencing frames live.

### Stage 5 · Months 12–18 — Reality layers

Environment, test, reliability, operations, Indian regulation, and how to judge other people's engineering. These only make sense once you know what you are testing.

**Build milestone:** Balloon flight 1, then flight 2 two months later, then the CubeSat design package.

---

## The modules

24 modules, 587 topics and build steps. Module 24 is the build track; its steps run alongside the studying, not after it.

| # | Module | Stage | Topics | Code range |
|---|---|---|---|---|
| 1 | Maths & physics warm-up | 0 | 25 | `M01-A01`–`M01-C04` |
| 2 | How a satellite system hangs together | 0 | 14 | `M02-A01`–`M02-C03` |
| 3 | Orbital mechanics | 1 | 33 | `M03-A01`–`M03-E07` |
| 4 | Systems engineering & mission design | 1 | 20 | `M04-A01`–`M04-C04` |
| 5 | Mass budget & structures | 2 | 21 | `M05-A01`–`M05-D03` |
| 6 | Power subsystem | 2 | 21 | `M06-A01`–`M06-C10` |
| 7 | Communications & link budget | 2 | 23 | `M07-A01`–`M07-C08` |
| 8 | Attitude determination & control | 3 | 35 | `M08-A01`–`M08-E07` |
| 9 | Thermal control | 3 | 18 | `M09-A01`–`M09-B11` |
| 10 | Onboard computer & flight software | 3 | 24 | `M10-A01`–`M10-C05` |
| 11 | Optical payload | 4 | 19 | `M11-A01`–`M11-C03` |
| 12 | Remote sensing & calibration | 4 | 27 | `M12-A01`–`M12-D06` |
| 13 | Geospatial core — data models & coordinates | 4 | 24 | `M13-A01`–`M13-C04` |
| 14 | Geospatial analysis — the arguments you must win | 4 | 41 | `M14-A01`–`M14-E08` |
| 15 | GeoAI | 4 | 28 | `M15-A01`–`M15-E04` |
| 16 | Edge AI on the payload | 4 | 24 | `M16-A01`–`M16-E03` |
| 17 | Geospatial software architecture | 4 | 22 | `M17-A01`–`M17-D06` |
| 18 | Space & stratosphere environment | 5 | 20 | `M18-A01`–`M18-D05` |
| 19 | Assembly, integration & test | 5 | 23 | `M19-A01`–`M19-D05` |
| 20 | Reliability engineering | 5 | 15 | `M20-A01`–`M20-C04` |
| 21 | Launch, ground segment & operations | 5 | 21 | `M21-A01`–`M21-D07` |
| 22 | Indian regulation & programme management | 5 | 21 | `M22-A01`–`M22-D05` |
| 23 | Judging work & reading the industry | 5 | 24 | `M23-A01`–`M23-D07` |
| 24 | Build track — balloon programme | 5 | 44 | `M24-A01`–`M24-G04` |

---

### Module 1 — Maths & physics warm-up

*Stage 0 · Month 1 · the floor everything stands on · 25 topics · codes `M01-A01`–`M01-C04`*

**A · Maths you will actually use**  (codes `M01-A01`–`M01-A11`)

- `M01-A01` Units, dimensional analysis, and sanity-checking any number you are given
- `M01-A02` Vectors: addition, dot product, cross product, and what each one means physically
- `M01-A03` Rotating a vector in 2D, then in 3D
- `M01-A04` Trigonometry for angles, pointing and field of view
- `M01-A05` Logarithms, and why the decibel scale exists
- `M01-A06` Exponential growth and decay
- `M01-A07` Derivatives as rates of change — reading them, not deriving them
- `M01-A08` Integrals as accumulated totals
- `M01-A09` Matrices and what multiplying by one does to a vector
- `M01-A10` Solving simultaneous equations
- `M01-A11` Reading and interpreting a log-scale graph

**B · Physics you will actually use**  (codes `M01-B01`–`M01-B10`)

- `M01-B01` Newton's three laws, stated precisely
- `M01-B02` Force, mass, acceleration, momentum
- `M01-B03` Work, energy and power — and why they are constantly confused
- `M01-B04` Circular motion and centripetal force
- `M01-B05` Gravity as an inverse-square law
- `M01-B06` Heat transfer: conduction, convection, radiation, and which exist in vacuum
- `M01-B07` Electricity: voltage, current, resistance, power, and energy stored
- `M01-B08` Waves: frequency, wavelength, speed, and how they relate
- `M01-B09` Pressure, density, and how both fall with altitude
- `M01-B10` The standard atmosphere model up to 40 km

**C · The estimation habit**  (codes `M01-C01`–`M01-C04`)

- `M01-C01` Order-of-magnitude (Fermi) estimation — the core CEO skill
- `M01-C02` Significant figures and false precision
- `M01-C03` Error bars, and propagating error through a calculation
- `M01-C04` Spotting a wrong number before you check it

**Where to learn it**

- [Khan Academy — Physics and Linear Algebra](https://www.khanacademy.org/science/physics) — Free, fast, exactly this level
- [3Blue1Brown — Essence of Linear Algebra](https://www.3blue1brown.com/topics/linear-algebra) — Free video series; builds intuition for vectors and matrices
- [Engineering ToolBox — standard atmosphere](https://www.engineeringtoolbox.com/standard-atmosphere-d_604.html) — Reference tables for pressure and density by altitude

---

### Module 2 — How a satellite system hangs together

*Stage 0 · Month 1 · systems thinking before detail · 14 topics · codes `M02-A01`–`M02-C03`*

**A · The system, in one picture**  (codes `M02-A01`–`M02-A06`)

- `M02-A01` The seven subsystems and what each one owes the others
- `M02-A02` The payload is the mission; everything else exists to serve it
- `M02-A03` Why every subsystem fights over the same three things: mass, power, data
- `M02-A04` Interfaces as the real source of failure, not components
- `M02-A05` The difference between a requirement, a constraint and a wish
- `M02-A06` How one decision early (orbit, band, aperture) locks a dozen later ones

**B · First-principles habit**  (codes `M02-B01`–`M02-B05`)

- `M02-B01` Breaking any industry claim down to physics and a number
- `M02-B02` Separating a real constraint from an inherited convention
- `M02-B03` Asking 'what would have to be true for this to work?'
- `M02-B04` Real cost drivers in space hardware versus cost myths
- `M02-B05` Why 'space-grade' sometimes means necessary and sometimes means lazy

**C · Reading the field**  (codes `M02-C01`–`M02-C03`)

- `M02-C01` Reading a satellite mission datasheet and knowing what is missing from it
- `M02-C02` Reading a conference paper's method and results before its abstract
- `M02-C03` Telling a demo apart from a product

**Where to learn it**

- [NASA CubeSat 101](https://www.nasa.gov/wp-content/uploads/2017/03/nasa_csli_cubesat_101_508.pdf) — Free PDF — read cover to cover, twice
- [MIT OCW 16.851 — Satellite Engineering](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Free lecture notes for the whole system
- [eoPortal mission database](https://www.eoportal.org/) — Look up any real Earth-observation mission's specs
- Wertz & Larson — Space Mission Analysis and Design (SMAD) — Book · the spine text for this whole plan

---

### Module 3 — Orbital mechanics

*Stage 1 · Months 1–3 · the constraint behind every other number · 33 topics · codes `M03-A01`–`M03-E07`*

**A · Core mechanics**  (codes `M03-A01`–`M03-A07`)

- `M03-A01` Newton's law of gravitation and the two-body problem
- `M03-A02` Kepler's three laws
- `M03-A03` The vis-viva equation
- `M03-A04` Orbital velocity and orbital period
- `M03-A05` Escape velocity
- `M03-A06` Specific orbital energy and why it is conserved
- `M03-A07` Angular momentum in orbit

**B · The six orbital elements**  (codes `M03-B01`–`M03-B07`)

- `M03-B01` Semi-major axis (a)
- `M03-B02` Eccentricity (e)
- `M03-B03` Inclination (i)
- `M03-B04` Right ascension of the ascending node (RAAN)
- `M03-B05` Argument of perigee (ω)
- `M03-B06` True anomaly (ν)
- `M03-B07` Converting elements to position and velocity, and back

**C · Manoeuvres**  (codes `M03-C01`–`M03-C05`)

- `M03-C01` Delta-v budgeting
- `M03-C02` Hohmann transfer
- `M03-C03` Plane changes and why they are brutally expensive
- `M03-C04` Phasing manoeuvres
- `M03-C05` Station keeping and its lifetime cost

**D · Orbit types & Earth-observation geometry**  (codes `M03-D01`–`M03-D07`)

- `M03-D01` LEO, MEO, GEO, HEO and when each is right
- `M03-D02` Polar orbits
- `M03-D03` Sun-synchronous orbit, and exactly why EO missions use it
- `M03-D04` Local time of descending node, and its effect on shadows and usability
- `M03-D05` Ground track calculation and repeat cycles
- `M03-D06` Revisit time versus swath width — the first real trade
- `M03-D07` Eclipse duration and beta angle

**E · Real orbits, not ideal ones**  (codes `M03-E01`–`M03-E07`)

- `M03-E01` J2 perturbation and nodal precession — the reason SSO exists at all
- `M03-E02` Atmospheric drag and orbital decay
- `M03-E03` Solar radiation pressure
- `M03-E04` Third-body effects from the Moon and Sun
- `M03-E05` Satellite lifetime estimation
- `M03-E06` TLE format, field by field
- `M03-E07` SGP4 propagation — and how fast its accuracy degrades

**Where to learn it**

- [Braeunig — Rocket & Space Technology](http://www.braeunig.us/space/) — Free orbital mechanics primer with worked maths
- [CelesTrak](https://celestrak.org/) — TLEs, SGP4 documentation, orbit theory papers
- [GMAT (NASA)](https://sourceforge.net/projects/gmat/) — Free mission analysis tool — install in week one
- [Gpredict](http://gpredict.oz9aec.net/) — Free pass prediction and tracking
- Curtis — Orbital Mechanics for Engineering Students — Book · the standard first text

---

### Module 4 — Systems engineering & mission design

*Stage 1 · Months 1–3 · how missions get planned and reviewed · 20 topics · codes `M04-A01`–`M04-C04`*

**A · Defining a mission**  (codes `M04-A01`–`M04-A07`)

- `M04-A01` Mission statement versus mission objectives
- `M04-A02` Concept of operations (CONOPS)
- `M04-A03` Writing a mission requirement document
- `M04-A04` Requirement types: functional, performance, interface, environmental
- `M04-A05` Writing a requirement that can actually be verified
- `M04-A06` Requirements traceability matrix
- `M04-A07` Verification methods: test, analysis, inspection, demonstration

**B · The process**  (codes `M04-B01`–`M04-B09`)

- `M04-B01` The V-model lifecycle
- `M04-B02` Review gates: MCR, PDR, CDR, TRR, FRR — what each one is for
- `M04-B03` Technology readiness levels 1–9, and how they get inflated
- `M04-B04` Trade studies and trade-off matrices
- `M04-B05` Margin policy for mass, power, data and schedule
- `M04-B06` Interface control documents
- `M04-B07` Work breakdown structure
- `M04-B08` Configuration management
- `M04-B09` Risk register and risk scoring

**C · Where programmes die**  (codes `M04-C01`–`M04-C04`)

- `M04-C01` Requirements creep and how to detect it early
- `M04-C02` The cost multiplier of a late change
- `M04-C03` Why 'we will fix it in software' fails in orbit
- `M04-C04` Single-person-dependency as a programme risk

**Where to learn it**

- [MIT OCW 16.842 — Fundamentals of Systems Engineering](https://ocw.mit.edu/courses/16-842-fundamentals-of-systems-engineering-fall-2015/) — Free full course built around the V-model
- [MIT OCW 16.83X — Space Systems Engineering](https://ocw.mit.edu/courses/16-83x-space-systems-engineering-spring-2002-spring-2003/) — Capstone-level mission design
- [NASA CSLI resources hub](https://www.nasa.gov/kennedy/launch-services-program/cubesat-launch-initiative/cubesat-launch-initiative-resources/) — Handbooks, ICDs, real programme documents

---

### Module 5 — Mass budget & structures

*Stage 2 · Months 3–6 · budget 1 of 3 · 21 topics · codes `M05-A01`–`M05-D03`*

**A · Form factor & standards**  (codes `M05-A01`–`M05-A05`)

- `M05-A01` CubeSat form factors: 1U, 3U, 6U, 12U
- `M05-A02` CubeSat Design Specification (Cal Poly) — read in full
- `M05-A03` Rail and tab tolerances for deployer compatibility
- `M05-A04` Centre of gravity requirements
- `M05-A05` Fit check with the deployer

**B · Budgeting**  (codes `M05-B01`–`M05-B03`)

- `M05-B01` Building a mass budget with margin allocation per maturity level
- `M05-B02` Mass properties: centre of gravity and moment of inertia tensor
- `M05-B03` Balancing a payload so pointing does not fight the structure

**C · Materials & loads**  (codes `M05-C01`–`M05-C10`)

- `M05-C01` Aluminium 6061-T6 versus 7075; titanium; composites
- `M05-C02` Outgassing limits: ASTM E595, TML and CVCM
- `M05-C03` Quasi-static launch loads
- `M05-C04` Random vibration and PSD curves
- `M05-C05` Sine vibration and resonance
- `M05-C06` Acoustic loads
- `M05-C07` Shock events and their frequency content
- `M05-C08` Natural frequency requirement from the launch provider
- `M05-C09` Finite element analysis basics: modal and static
- `M05-C10` Factor of safety, and where it is conventionally set

**D · Mechanisms**  (codes `M05-D01`–`M05-D03`)

- `M05-D01` Deployables: hinges, burn-wire release, spring mechanisms
- `M05-D02` Fasteners, staking, torque specs and thread locking against vibration
- `M05-D03` Why mechanisms are the most common single point of failure

**Where to learn it**

- [CubeSat Design Specification (Cal Poly)](https://www.cubesat.org/cubesatinfo) — The rulebook — free PDF
- [NASA State of the Art — Small Spacecraft Technology](https://www.nasa.gov/smallsat-institute/sst-soa) — Current hardware, updated yearly
- [FreeCAD](https://www.freecad.org/) — Free CAD for structural modelling
- [Ansys Student](https://www.ansys.com/academic/students) — Free FEA licence for learning

---

### Module 6 — Power subsystem

*Stage 2 · Months 3–6 · budget 2 of 3 · 21 topics · codes `M06-A01`–`M06-C10`*

**A · Generation**  (codes `M06-A01`–`M06-A06`)

- `M06-A01` Photovoltaic effect, I-V curve, fill factor
- `M06-A02` Triple-junction GaAs versus silicon cells
- `M06-A03` Solar array sizing and packing factor
- `M06-A04` Body-mounted versus deployable arrays
- `M06-A05` Sun incidence angle and cosine loss
- `M06-A06` Cell degradation from radiation across mission life

**B · Storage**  (codes `M06-B01`–`M06-B05`)

- `M06-B01` Li-ion versus LiPo chemistry and cell selection
- `M06-B02` Depth of discharge and cycle life
- `M06-B03` Battery sizing calculation from the eclipse load
- `M06-B04` Charge temperature limits — the tightest constraint on the satellite
- `M06-B05` Cell balancing and protection circuits

**C · Budget & distribution**  (codes `M06-C01`–`M06-C10`)

- `M06-C01` Orbit-average power versus peak power
- `M06-C02` Duty cycles per operating mode
- `M06-C03` Energy balance across eclipse and sunlight
- `M06-C04` Direct energy transfer versus MPPT architecture
- `M06-C05` Power conditioning and distribution unit
- `M06-C06` DC-DC converters and efficiency at low load
- `M06-C07` Bus voltage selection
- `M06-C08` Latch-up protection and current limiting
- `M06-C09` Inhibit switches and the remove-before-flight pin
- `M06-C10` Grounding, return paths and why they bite late

**Where to learn it**

- [NASA State of the Art — Power chapter](https://www.nasa.gov/smallsat-institute/sst-soa) — Flight-proven components and real specs
- [MIT OCW 16.851 — Spacecraft Power Systems](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Free lecture PDF
- Patel — Spacecraft Power Systems — Book · the dedicated reference

---

### Module 7 — Communications & link budget

*Stage 2 · Months 3–6 · budget 3 of 3 · 23 topics · codes `M07-A01`–`M07-C08`*

**A · RF fundamentals**  (codes `M07-A01`–`M07-A07`)

- `M07-A01` Frequency, wavelength, polarisation
- `M07-A02` What modulation actually is
- `M07-A03` Bands and their trade-offs: VHF, UHF, S, X, Ka
- `M07-A04` Free space path loss, derived not memorised
- `M07-A05` Antenna gain, beamwidth and the gain-coverage trade
- `M07-A06` Noise temperature and noise figure
- `M07-A07` Doppler shift and Doppler correction

**B · The link budget**  (codes `M07-B01`–`M07-B08`)

- `M07-B01` EIRP
- `M07-B02` G/T of a ground station
- `M07-B03` C/N0 and Eb/N0
- `M07-B04` Required link margin and how it is justified
- `M07-B05` Building a complete link budget end to end
- `M07-B06` Data volume per pass
- `M07-B07` Pass duration versus elevation mask
- `M07-B08` The downlink bottleneck, and what it forces on payload design

**C · Hardware & coding**  (codes `M07-C01`–`M07-C08`)

- `M07-C01` Antenna types: dipole, turnstile, patch, helical, parabolic
- `M07-C02` Modulation schemes: BPSK, QPSK, GMSK, FSK
- `M07-C03` Forward error correction: Reed-Solomon
- `M07-C04` Convolutional coding and Viterbi decoding
- `M07-C05` Turbo and LDPC codes
- `M07-C06` Protocols: AX.25, CCSDS, CubeSat Space Protocol
- `M07-C07` TT&C architecture and beacon design
- `M07-C08` Command authentication and why unauthenticated uplink is negligence

**Where to learn it**

- [GNU Radio](https://www.gnuradio.org/) — Free SDR toolkit — pairs with your RTL-SDR
- [SatDump](https://www.satdump.org/) — Decodes live weather-satellite imagery
- [RTL-SDR Blog guides](https://www.rtl-sdr.com/) — Practical tutorials for receiving satellites
- [AMSAT](https://www.amsat.org/) — Amateur satellite community, frequencies, hardware
- Maral & Bousquet — Satellite Communications Systems — Book · link budget maths done properly

---

### Module 8 — Attitude determination & control

*Stage 3 · Months 6–11 · the hardest subsystem, and your balloon needs it too · 35 topics · codes `M08-A01`–`M08-E07`*

**A · Maths you cannot skip**  (codes `M08-A01`–`M08-A07`)

- `M08-A01` Reference frames: ECI, ECEF, LVLH, body frame
- `M08-A02` Rotation matrices
- `M08-A03` Euler angles and gimbal lock
- `M08-A04` Quaternions — what flight software actually uses
- `M08-A05` Moment of inertia tensor
- `M08-A06` Euler's rotational equations
- `M08-A07` Angular momentum and why it is conserved, not created

**B · Sensors**  (codes `M08-B01`–`M08-B07`)

- `M08-B01` Coarse and fine sun sensors (your BPW34 photodiodes)
- `M08-B02` Magnetometers
- `M08-B03` MEMS gyroscope drift and bias characterisation
- `M08-B04` Star trackers and star pattern matching
- `M08-B05` GPS receivers in space and COCOM limits
- `M08-B06` Earth horizon sensors
- `M08-B07` Sensor fusion: why no single sensor is trusted alone

**C · Actuators**  (codes `M08-C01`–`M08-C06`)

- `M08-C01` Reaction wheels: momentum storage, saturation, desaturation
- `M08-C02` Magnetorquers: torque rods, coils, dipole moment sizing
- `M08-C03` Momentum wheels versus reaction wheels
- `M08-C04` Cold gas and electric propulsion basics
- `M08-C05` Why propellers produce almost no thrust above 30 km, and nothing in vacuum
- `M08-C06` Aerodynamic control surfaces — where they work and where they stop working

**D · Algorithms**  (codes `M08-D01`–`M08-D08`)

- `M08-D01` Attitude determination: TRIAD
- `M08-D02` Attitude determination: QUEST
- `M08-D03` Kalman filter, conceptually and then concretely
- `M08-D04` Extended Kalman filter
- `M08-D05` PID control
- `M08-D06` LQR control
- `M08-D07` B-dot detumbling
- `M08-D08` Pointing modes: nadir, sun, target tracking, slew

**E · Performance & disturbance**  (codes `M08-E01`–`M08-E07`)

- `M08-E01` Pointing accuracy, knowledge and stability — three different numbers
- `M08-E02` Jitter and its direct effect on image quality
- `M08-E03` Gravity gradient torque
- `M08-E04` Aerodynamic torque
- `M08-E05` Solar radiation torque
- `M08-E06` Residual magnetic dipole torque
- `M08-E07` Budgeting a pointing error from all sources

**Where to learn it**

- [MIT OCW 16.851 — ADCS lecture notes](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Free PDF, well-structured introduction
- [NASA State of the Art — GNC chapter](https://www.nasa.gov/smallsat-institute/sst-soa) — Flight-proven ADCS hardware by class
- [SmallSat Conference proceedings](https://digitalcommons.usu.edu/smallsat/) — Free papers — search 'ADCS' for real designs
- Markley & Crassidis — Spacecraft Attitude Determination and Control — Book · the definitive text

---

### Module 9 — Thermal control

*Stage 3 · Months 6–11 · no air means no convection · 18 topics · codes `M09-A01`–`M09-B11`*

**A · Physics**  (codes `M09-A01`–`M09-A07`)

- `M09-A01` Heat transfer in vacuum: conduction and radiation only
- `M09-A02` Stefan-Boltzmann law
- `M09-A03` Emissivity and absorptivity
- `M09-A04` The α/ε ratio and how surfaces are selected by it
- `M09-A05` Solar flux (1361 W/m²), Earth albedo and Earth infrared
- `M09-A06` Thermal balance equation and equilibrium temperature
- `M09-A07` Hot case and cold case analysis

**B · Design**  (codes `M09-B01`–`M09-B11`)

- `M09-B01` Operational versus survival temperature limits per component
- `M09-B02` Multi-layer insulation
- `M09-B03` Coatings, paints and tapes
- `M09-B04` Radiators and their sizing
- `M09-B05` Heaters and thermostats, and their power cost
- `M09-B06` Heat pipes
- `M09-B07` Thermal interface materials, straps and conductive paths
- `M09-B08` Battery thermal management — usually the binding constraint
- `M09-B09` Thermal cycling and fatigue across thousands of orbits
- `M09-B10` Nodal thermal modelling
- `M09-B11` The stratosphere case: −60 °C at 1% pressure, and why it is a genuine rehearsal

**Where to learn it**

- [NASA State of the Art — Thermal Control chapter](https://www.nasa.gov/smallsat-institute/sst-soa) — Current thermal hardware for smallsats
- [MIT OCW 16.851 — Environment of Space](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Free PDF covering the thermal environment
- Gilmore — Spacecraft Thermal Control Handbook — Book · industry standard reference

---

### Module 10 — Onboard computer & flight software

*Stage 3 · Months 6–11 · the brain you must be able to review · 24 topics · codes `M10-A01`–`M10-C05`*

**A · Hardware**  (codes `M10-A01`–`M10-A07`)

- `M10-A01` Microcontrollers versus systems-on-chip
- `M10-A02` ARM Cortex-M versus Cortex-A, and which job each suits
- `M10-A03` COTS versus rad-tolerant versus rad-hard parts, and the honest cost difference
- `M10-A04` Data buses: I2C, SPI, UART, CAN — and failure modes of each
- `M10-A05` Watchdog timers and reset architecture
- `M10-A06` Memory: SRAM, Flash, FRAM
- `M10-A07` Error detection and correction, and memory scrubbing

**B · Software**  (codes `M10-B01`–`M10-B12`)

- `M10-B01` What a real-time operating system guarantees
- `M10-B02` FreeRTOS and RTEMS
- `M10-B03` Bare metal versus RTOS trade-off
- `M10-B04` Bootloader design and over-the-air software update
- `M10-B05` Telemetry frame design
- `M10-B06` Housekeeping data: what to log and at what rate
- `M10-B07` Command handling and validation
- `M10-B08` Time-tagged commands
- `M10-B09` Fault detection, isolation and recovery
- `M10-B10` Safe mode design and autonomous recovery
- `M10-B11` Onboard data storage and file management
- `M10-B12` Time synchronisation across subsystems

**C · Verification**  (codes `M10-C01`–`M10-C05`)

- `M10-C01` Unit testing for flight software
- `M10-C02` Hardware-in-the-loop testing
- `M10-C03` Day-in-the-life runs
- `M10-C04` Fault injection testing
- `M10-C05` Reviewing software you did not write — what to actually look at

**Where to learn it**

- [FreeRTOS documentation](https://www.freertos.org/) — Free RTOS with excellent tutorials
- [NASA State of the Art — Avionics chapter](https://www.nasa.gov/smallsat-institute/sst-soa) — Flight computers actually used on smallsats
- [NASA Power of Ten rules](https://ntrs.nasa.gov/citations/20080039927) — Rules for safety-critical code — a review checklist

---

### Module 11 — Optical payload

*Stage 4 · Months 9–14 · this sets your resolution ceiling forever · 19 topics · codes `M11-A01`–`M11-C03`*

**A · Optics**  (codes `M11-A01`–`M11-A08`)

- `M11-A01` Focal length, f-number, field of view
- `M11-A02` The diffraction limit and the Rayleigh criterion
- `M11-A03` Aperture diameter versus ground sample distance — memorise this relationship
- `M11-A04` Telescope designs: refractive, Cassegrain, Ritchey-Chrétien, three-mirror anastigmat
- `M11-A05` Aberrations: spherical, coma, astigmatism, chromatic
- `M11-A06` Modulation transfer function
- `M11-A07` Stray light control and baffling
- `M11-A08` Focus mechanism and thermal focus drift

**B · Detector**  (codes `M11-B01`–`M11-B08`)

- `M11-B01` CCD versus CMOS sensors
- `M11-B02` Time delay integration
- `M11-B03` Push-broom versus whisk-broom versus frame imaging
- `M11-B04` Pixel pitch, well depth, quantum efficiency
- `M11-B05` Signal-to-noise ratio and radiometric sensitivity
- `M11-B06` Integration time and image smear — ties straight back to pointing stability
- `M11-B07` Spectral bands, filters and bandpass selection
- `M11-B08` Panchromatic versus multispectral, and pansharpening

**C · The central trade**  (codes `M11-C01`–`M11-C03`)

- `M11-C01` Resolution versus swath versus data rate — pick two
- `M11-C02` Why a sharper camera can make a worse product
- `M11-C03` What resolution your clients actually need, versus what they ask for

**Where to learn it**

- [MIT OCW 16.851 — Optics lectures](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Free PDFs with a real optical satellite case study
- [eoPortal — mission database](https://www.eoportal.org/) — Look up real EO payload specifications
- Schott — Remote Sensing: The Image Chain Approach — Book · links optics to final image quality

---

### Module 12 — Remote sensing & calibration

*Stage 4 · Months 9–14 · what makes imagery trustworthy · 27 topics · codes `M12-A01`–`M12-D06`*

**A · Fundamentals**  (codes `M12-A01`–`M12-A05`)

- `M12-A01` Electromagnetic spectrum and atmospheric windows
- `M12-A02` Spectral signatures: vegetation, water, soil, urban surfaces
- `M12-A03` Digital number versus radiance versus reflectance
- `M12-A04` The four resolutions — spatial, spectral, temporal, radiometric — and their trade-offs
- `M12-A05` Why you cannot improve one without paying in another

**B · Sensors & missions**  (codes `M12-B01`–`M12-B06`)

- `M12-B01` Landsat programme and its archive
- `M12-B02` Sentinel-2 and the Copernicus programme
- `M12-B03` MODIS and coarse-resolution daily data
- `M12-B04` Thermal infrared sensors and land surface temperature
- `M12-B05` Synthetic aperture radar basics, and when radar beats optical
- `M12-B06` Hyperspectral sensing and where it genuinely pays

**C · The calibration chain**  (codes `M12-C01`–`M12-C10`)

- `M12-C01` Dark current and dark frame correction
- `M12-C02` Flat fielding
- `M12-C03` Gain and offset calibration
- `M12-C04` DN to radiance to reflectance conversion
- `M12-C05` Thermal band conversion to surface temperature
- `M12-C06` Geometric calibration and distortion correction
- `M12-C07` Georeferencing and orthorectification with a DEM
- `M12-C08` Atmospheric correction: dark object subtraction, 6S, MODTRAN
- `M12-C09` Vicarious calibration and ground truthing
- `M12-C10` Why uncalibrated imagery is worthless to a serious client

**D · Products & delivery**  (codes `M12-D01`–`M12-D06`)

- `M12-D01` Processing levels L0, L1A, L1B, L1C, L2A
- `M12-D02` Cloud masking, and the ways cloud masks fail
- `M12-D03` Band math and indices: NDVI, NDWI, NDBI
- `M12-D04` Image compression: JPEG2000 and CCSDS 122
- `M12-D05` Formats: GeoTIFF, Cloud Optimized GeoTIFF, HDF5, NetCDF
- `M12-D06` Metadata standards and STAC catalogues

**Where to learn it**

- [NASA ARSET training](https://appliedsciences.nasa.gov/arset) — Free structured remote sensing courses with certificates
- [ESA SNAP toolbox](https://step.esa.int/main/toolboxes/snap/) — Free — process raw Sentinel data end to end
- [Copernicus Data Space](https://dataspace.copernicus.eu/) — Free Sentinel data including raw levels
- [USGS Landsat missions](https://www.usgs.gov/landsat-missions) — Calibration documents and data user handbooks
- Lillesand — Remote Sensing and Image Interpretation — Book · the standard course text

---

### Module 13 — Geospatial core — data models & coordinates

*Stage 4 · Months 9–14 · deeper than any GIS course goes · 24 topics · codes `M13-A01`–`M13-C04`*

**A · Data models**  (codes `M13-A01`–`M13-A08`)

- `M13-A01` Vector data: points, lines, polygons
- `M13-A02` Topology, and the specific ways it breaks
- `M13-A03` Geometry validity: self-intersections, slivers, unclosed rings
- `M13-A04` Raster data: grid cells, pixel values, nodata
- `M13-A05` Attribute tables and linking non-spatial data to features
- `M13-A06` Vector versus raster — the real trade, not the textbook one
- `M13-A07` Simple Features standard and why interoperability keeps failing
- `M13-A08` Point clouds and when they are the right model

**B · Coordinate systems, properly**  (codes `M13-B01`–`M13-B12`)

- `M13-B01` The shape of the Earth: geoid versus ellipsoid
- `M13-B02` What a datum actually defines
- `M13-B03` WGS84, ITRF, GDA2020 and the Indian datums
- `M13-B04` Plate motion: why a datum drifts with the continent
- `M13-B05` Geographic versus projected coordinate systems
- `M13-B06` Map projections and what each one distorts — area, angle, distance
- `M13-B07` UTM and MGA zones; zone-edge problems
- `M13-B08` EPSG codes and the EPSG registry
- `M13-B09` Conversion versus transformation — not the same operation
- `M13-B10` Seven-parameter transformations and grid-shift files
- `M13-B11` Accuracy lost at each step of a transformation chain
- `M13-B12` Vertical datums, orthometric height versus ellipsoidal height

**C · Judgement**  (codes `M13-C01`–`M13-C04`)

- `M13-C01` How a 2 cm survey error becomes a 2 m error downstream
- `M13-C02` Silent CRS mismatch — the single most common bug in geospatial software
- `M13-C03` Why 'it lines up on the screen' proves nothing
- `M13-C04` Choosing a CRS for a national-scale product in India

**Where to learn it**

- [EPSG Geodetic Parameter Registry](https://epsg.org/) — The authoritative CRS reference
- [PROJ documentation](https://proj.org/) — How transformations are actually computed
- [QGIS](https://qgis.org) — Free GIS — do every exercise here
- [Spatial Thoughts tutorials](https://spatialthoughts.com/) — Free, high-quality, India-based QGIS and Python training
- Iliffe & Lott — Datums and Map Projections — Book · the serious treatment of datums

---

### Module 14 — Geospatial analysis — the arguments you must win

*Stage 4 · Months 9–14 · where most of the industry is sloppy · 41 topics · codes `M14-A01`–`M14-E08`*

**A · Vector operations**  (codes `M14-A01`–`M14-A09`)

- `M14-A01` Buffer analysis
- `M14-A02` Spatial joins
- `M14-A03` Attribute joins by ID
- `M14-A04` Clipping and intersection
- `M14-A05` Union and dissolve
- `M14-A06` Spatial predicates: contains, within, intersects, touches, overlaps
- `M14-A07` Planar versus geodesic distance and area
- `M14-A08` Why buffering in degrees is almost always wrong
- `M14-A09` Geocoding, and how its error is distributed

**B · Raster analysis**  (codes `M14-B01`–`M14-B09`)

- `M14-B01` Band math fundamentals
- `M14-B02` NDVI, and exactly why it saturates over dense canopy
- `M14-B03` NDWI, NDBI, EVI, SAVI — what each one was invented to fix
- `M14-B04` Supervised versus unsupervised classification
- `M14-B05` Classification accuracy assessment and the confusion matrix
- `M14-B06` Zonal statistics: extracting raster values per polygon
- `M14-B07` Resampling methods — nearest, bilinear, cubic — and when each is wrong
- `M14-B08` Reprojecting a raster, and the error it introduces every time
- `M14-B09` Mosaicking and seamline artefacts

**C · Spatial statistics**  (codes `M14-C01`–`M14-C09`)

- `M14-C01` Spatial autocorrelation, conceptually
- `M14-C02` Tobler's first law and its limits
- `M14-C03` Spatial weights matrices — and how the choice changes the answer
- `M14-C04` Global Moran's I
- `M14-C05` Local Moran's I and LISA hotspot mapping
- `M14-C06` Getis-Ord Gi* hotspots
- `M14-C07` Multiple testing, and why some hotspots are pure noise
- `M14-C08` P-values and what they do not mean
- `M14-C09` Presenting a hotspot map honestly to a client

**D · Geostatistics**  (codes `M14-D01`–`M14-D06`)

- `M14-D01` Interpolation compared: IDW, spline, natural neighbour
- `M14-D02` The variogram and what it encodes
- `M14-D03` Kriging and its assumptions
- `M14-D04` Kriging variance as an uncertainty map
- `M14-D05` Cross-validation of an interpolated surface
- `M14-D06` When interpolation lies, and how to show that it might be

**E · Scale, integration & fallacies**  (codes `M14-E01`–`M14-E08`)

- `M14-E01` The modifiable areal unit problem
- `M14-E02` The ecological fallacy
- `M14-E03` Mixing 1 km and 30 m data — the industry's most common silent error
- `M14-E04` Resampling versus aggregation, and which direction is defensible
- `M14-E05` Census geography, boundaries and their effects
- `M14-E06` Bivariate and quadrant analysis
- `M14-E07` Correlation versus causation in spatial data
- `M14-E08` Data validation and ground-truthing a result before it reaches a client

**Where to learn it**

- [PySAL](https://pysal.org/) — Free spatial analysis library with excellent documentation
- [GeoDa](https://geodacenter.github.io/) — Free point-and-click spatial statistics — best for building intuition
- [Geographic Data Science with Python](https://geographicdata.science/book/) — Free online book, rigorous and practical
- [Geocomputation with R](https://r.geocompx.org/) — Free online book; strong on spatial operations
- [GDAL](https://gdal.org/) — The engine under almost every geospatial tool

---

### Module 15 — GeoAI

*Stage 4 · Months 9–14 · where the company actually earns · 28 topics · codes `M15-A01`–`M15-E04`*

**A · Foundations, honestly**  (codes `M15-A01`–`M15-A05`)

- `M15-A01` What a model actually learns, and what it cannot
- `M15-A02` Training, validation and test splits
- `M15-A03` Overfitting and how it hides
- `M15-A04` Loss functions and what they optimise for
- `M15-A05` Why overall accuracy is a misleading headline metric

**B · Vision for Earth observation**  (codes `M15-B01`–`M15-B07`)

- `M15-B01` Convolutional networks, conceptually
- `M15-B02` Classification versus detection versus segmentation
- `M15-B03` U-Net and land cover segmentation
- `M15-B04` Vision transformers for imagery
- `M15-B05` Foundation models for EO and what they change
- `M15-B06` Time series models and change detection
- `M15-B07` Multi-sensor fusion: optical with radar

**C · Data is the real work**  (codes `M15-C01`–`M15-C06`)

- `M15-C01` Labelling strategy, cost and quality control
- `M15-C02` Class imbalance in Earth observation data
- `M15-C03` Label noise and its effect on reported accuracy
- `M15-C04` Augmentation that is valid for satellite imagery, and what is not
- `M15-C05` Domain shift — why a model trained on Europe fails over Gujarat
- `M15-C06` Building a defensible training set for Indian conditions

**D · Evaluation & honesty**  (codes `M15-D01`–`M15-D06`)

- `M15-D01` Confusion matrix, precision, recall, F1
- `M15-D02` Intersection over union
- `M15-D03` Spatial cross-validation, and why random splits inflate every score
- `M15-D04` Uncertainty estimation and calibrated confidence
- `M15-D05` Explaining a model's output to a non-technical client
- `M15-D06` Benchmark inflation in published EO AI results

**E · Deployment**  (codes `M15-E01`–`M15-E04`)

- `M15-E01` Model size versus accuracy versus inference cost
- `M15-E02` Monitoring drift in production
- `M15-E03` Retraining cadence and data versioning
- `M15-E04` When a simple index beats a neural network — and admitting it

**Where to learn it**

- [TorchGeo](https://torchgeo.readthedocs.io/) — Free library: EO datasets, models and samplers
- [NASA ARSET — machine learning modules](https://appliedsciences.nasa.gov/arset) — Free applied training for EO machine learning
- [Awesome Satellite Imagery Datasets / Deep Learning](https://github.com/satellite-image-deep-learning/techniques) — Curated list of EO datasets and methods
- [Google Earth Engine](https://earthengine.google.com/) — Free for research; fastest way to test ideas at scale

---

### Module 16 — Edge AI on the payload

*Stage 4 · Months 9–14 · the thinking moves into the sky · 24 topics · codes `M16-A01`–`M16-E03`*

**A · Why onboard at all**  (codes `M16-A01`–`M16-A04`)

- `M16-A01` The downlink bottleneck, quantified for your own link budget
- `M16-A02` Sending decisions instead of pixels
- `M16-A03` Latency when an alert actually matters
- `M16-A04` What must stay on the ground, and why

**B · Hardware reality**  (codes `M16-B01`–`M16-B05`)

- `M16-B01` NPUs and TOPS — what the number means and what it hides
- `M16-B02` Your Orange Pi 4 Pro NPU: real throughput versus the headline figure
- `M16-B03` Power per inference, and its place in the power budget
- `M16-B04` Thermal limits on sustained compute in a sealed box
- `M16-B05` Memory bandwidth as the usual true bottleneck

**C · Making models fit**  (codes `M16-C01`–`M16-C05`)

- `M16-C01` Quantisation to INT8 and the accuracy you lose
- `M16-C02` Pruning
- `M16-C03` Knowledge distillation
- `M16-C04` Model formats and runtimes: ONNX, TFLite, vendor NPU toolchains
- `M16-C05` Benchmarking a model on the actual board, not the datasheet

**D · The onboard pipeline**  (codes `M16-D01`–`M16-D07`)

- `M16-D01` Cloud screening before anything is stored
- `M16-D02` Georeferencing each frame live from GPS and attitude
- `M16-D03` Onboard mosaicking of overlapping frames
- `M16-D04` Event detection and compact alert messages
- `M16-D05` Store-and-forward when the link drops
- `M16-D06` Autonomy: retasking the camera from what the model just saw
- `M16-D07` Prioritising what to downlink when the pass is short

**E · Verification**  (codes `M16-E01`–`M16-E03`)

- `M16-E01` Testing a model you cannot easily patch after launch
- `M16-E02` Golden test images and regression testing
- `M16-E03` Graceful fallback when the model fails or disagrees with itself

**Where to learn it**

- [ONNX Runtime](https://onnxruntime.ai/) — Cross-platform inference, including edge targets
- [ESA Φ-sat and onboard AI missions](https://www.esa.int/Applications/Observing_the_Earth/Ph-sat) — The first flown onboard-AI EO payloads
- [SmallSat Conference proceedings](https://digitalcommons.usu.edu/smallsat/) — Search 'onboard processing' for real architectures

---

### Module 17 — Geospatial software architecture

*Stage 4 · Months 9–14 · the diagram you will draw a hundred times · 22 topics · codes `M17-A01`–`M17-D06`*

**A · Data flow**  (codes `M17-A01`–`M17-A04`)

- `M17-A01` Ingest, process, store, serve, visualise — the five stages
- `M17-A02` Batch versus streaming processing
- `M17-A03` Pipeline orchestration concepts
- `M17-A04` Idempotency and reprocessing without corrupting history

**B · Storage**  (codes `M17-B01`–`M17-B06`)

- `M17-B01` Object storage and Cloud Optimized GeoTIFF
- `M17-B02` Tiling schemes and overview pyramids
- `M17-B03` Spatial databases and spatial indexes: R-tree, quadtree
- `M17-B04` Discrete global grids: H3 and S2
- `M17-B05` Partitioning data by space and by time
- `M17-B06` Cost per terabyte, and what a careless design costs per year

**C · Serving**  (codes `M17-C01`–`M17-C06`)

- `M17-C01` Tile servers and tile caching
- `M17-C02` OGC services: WMS, WFS, WMTS
- `M17-C03` STAC APIs for search and discovery
- `M17-C04` Vector tiles versus GeoJSON — and when each breaks
- `M17-C05` Web mapping clients: Leaflet and MapLibre
- `M17-C06` Designing an API your clients can actually build on

**D · Scale & quality**  (codes `M17-D01`–`M17-D06`)

- `M17-D01` What breaks at ten times the data, and at a hundred
- `M17-D02` Caching strategy
- `M17-D03` Multi-tenant design for multiple clients
- `M17-D04` Data validation gates between pipeline stages
- `M17-D05` Provenance: proving where a number came from
- `M17-D06` Versioning data, models and outputs together

**Where to learn it**

- [STAC specification](https://stacspec.org/) — The de facto catalogue standard for EO data
- [PostGIS documentation](https://postgis.net/documentation/) — The reference spatial database
- [H3 by Uber](https://h3geo.org/) — Hexagonal global grid — read the design rationale
- [MapLibre](https://maplibre.org/) — Open-source vector tile mapping client
- [Cloud Optimized GeoTIFF](https://cogeo.org/) — Why cloud-native raster changed the architecture

---

### Module 18 — Space & stratosphere environment

*Stage 5 · Months 12–18 · what tries to kill the hardware · 20 topics · codes `M18-A01`–`M18-D05`*

**A · Vacuum**  (codes `M18-A01`–`M18-A03`)

- `M18-A01` Outgassing and material selection
- `M18-A02` Cold welding
- `M18-A03` Lubricant behaviour in vacuum

**B · Radiation**  (codes `M18-B01`–`M18-B08`)

- `M18-B01` Van Allen trapped radiation belts
- `M18-B02` Solar particle events and galactic cosmic rays
- `M18-B03` The South Atlantic Anomaly
- `M18-B04` Total ionising dose and dose-depth curves
- `M18-B05` Single event effects: upset, latch-up, transient, functional interrupt
- `M18-B06` Displacement damage
- `M18-B07` Shielding strategies and spot shielding
- `M18-B08` Why more shielding is sometimes worse

**C · Other hazards**  (codes `M18-C01`–`M18-C04`)

- `M18-C01` Atomic oxygen erosion in low LEO
- `M18-C02` Spacecraft charging and electrostatic discharge
- `M18-C03` Micrometeoroid and orbital debris risk
- `M18-C04` Space weather monitoring and the solar cycle

**D · The stratosphere, for your balloon**  (codes `M18-D01`–`M18-D05`)

- `M18-D01` Conditions at 35 km: temperature, pressure, density
- `M18-D02` Air roughly 150 times thinner than sea level — and every consequence of that
- `M18-D03` UV exposure above most of the ozone layer
- `M18-D04` Stratospheric winds over Gujarat by season
- `M18-D05` What transfers honestly to a space design, and what does not

**Where to learn it**

- [MIT OCW 16.851 — The Environment of Space](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Free lecture PDF
- [NASA Small Spacecraft Systems Virtual Institute](https://www.nasa.gov/smallsat-institute/) — Reliability and environment knowledge base
- [NOAA Space Weather Prediction Center](https://www.swpc.noaa.gov/) — Live space weather and the solar cycle

---

### Module 19 — Assembly, integration & test

*Stage 5 · Months 12–18 · where first missions most often die · 23 topics · codes `M19-A01`–`M19-D05`*

**A · Cleanroom & build**  (codes `M19-A01`–`M19-A07`)

- `M19-A01` Cleanroom classes (ISO 14644)
- `M19-A02` Electrostatic discharge control
- `M19-A03` Contamination control
- `M19-A04` Handling procedures and documentation discipline
- `M19-A05` Harness design, routing, connectors, strain relief
- `M19-A06` Conformal coating and staking
- `M19-A07` Integration sequence planning

**B · Environmental test campaign**  (codes `M19-B01`–`M19-B06`)

- `M19-B01` Thermal vacuum: hot and cold cycling, bakeout
- `M19-B02` Vibration: sine sweep, random, resonance survey
- `M19-B03` Shock testing
- `M19-B04` Acoustic testing
- `M19-B05` EMC and EMI testing
- `M19-B06` Reading a test report critically

**C · Standards & philosophy**  (codes `M19-C01`–`M19-C05`)

- `M19-C01` NASA GEVS (GSFC-STD-7000)
- `M19-C02` ECSS-E-ST-10-03 test standard
- `M19-C03` Qualification versus acceptance versus protoflight
- `M19-C04` Functional and end-to-end testing
- `M19-C05` Day-in-the-life test

**D · Testing on a startup budget**  (codes `M19-D01`–`M19-D05`)

- `M19-D01` Freezer and dry-ice cold testing
- `M19-D02` Low-pressure chamber testing on a budget
- `M19-D03` Drop testing and shake-table substitutes
- `M19-D04` Long-range radio testing on the ground
- `M19-D05` IN-SPACe facility access for real vibration, TVAC and EMI/EMC

**Where to learn it**

- [NASA Technical Standards](https://standards.nasa.gov/) — GEVS and more — free download
- [ECSS standards](https://ecss.nl/) — European space standards, free registration
- [IN-SPACe](https://www.inspace.gov.in/inspace) — Private access to ISRO test facilities in India

---

### Module 20 — Reliability engineering

*Stage 5 · Months 12–18 · why space hardware costs what it does · 15 topics · codes `M20-A01`–`M20-C04`*

**A · Analysis**  (codes `M20-A01`–`M20-A06`)

- `M20-A01` FMEA and FMECA
- `M20-A02` Fault tree analysis
- `M20-A03` Single point of failure identification
- `M20-A04` Worst-case analysis
- `M20-A05` Reliability prediction, MTBF and the bathtub curve
- `M20-A06` Reliability block diagrams

**B · Design practice**  (codes `M20-B01`–`M20-B05`)

- `M20-B01` Redundancy: cold, warm, hot
- `M20-B02` Cross-strapping
- `M20-B03` Derating guidelines for electronic parts
- `M20-B04` Part screening and lot acceptance testing
- `M20-B05` Lessons-learned databases from real failures

**C · Judgement**  (codes `M20-C01`–`M20-C04`)

- `M20-C01` Smallsat first-mission failure rates, and the honest reasons
- `M20-C02` The handful of failures that kill most first CubeSats
- `M20-C03` When redundancy adds risk instead of removing it
- `M20-C04` Deciding what you are willing to lose

**Where to learn it**

- [NASA Small Satellite Reliability Initiative](https://www.nasa.gov/smallsat-institute/) — Knowledge base built from real mission failures
- [SmallSat Conference proceedings](https://digitalcommons.usu.edu/smallsat/) — Search 'lessons learned' — post-mortems are the gold
- [NASA Technical Standards](https://standards.nasa.gov/) — Reliability and parts standards, free

---

### Module 21 — Launch, ground segment & operations

*Stage 5 · Months 12–18 · start the ground station in month 2, not month 20 · 21 topics · codes `M21-A01`–`M21-D07`*

**A · Getting manifested**  (codes `M21-A01`–`M21-A06`)

- `M21-A01` Rideshare versus dedicated launch
- `M21-A02` Reading and interpreting a payload user's guide
- `M21-A03` Deployers: P-POD, ISIPOD, ISS deployment
- `M21-A04` Launch environment specifications from the provider
- `M21-A05` Launch campaign logistics and paperwork
- `M21-A06` ISRO PSLV rideshare and NSIL launch services

**B · Separation**  (codes `M21-B01`–`M21-B03`)

- `M21-B01` Separation sequence and tip-off rates
- `M21-B02` Deployment safety requirements, inhibits and arming
- `M21-B03` Orbit injection accuracy and dispersion

**C · Ground station**  (codes `M21-C01`–`M21-C05`)

- `M21-C01` Architecture: antenna, rotator, LNA, radio, TNC, computer
- `M21-C02` Antenna tracking and rotator control
- `M21-C03` Doppler correction software
- `M21-C04` Pass planning and scheduling
- `M21-C05` Site selection, noise floor and interference survey

**D · Operations**  (codes `M21-D01`–`M21-D07`)

- `M21-D01` Orbit determination and TLE updates
- `M21-D02` Mission control software: Yamcs, OpenC3 COSMOS
- `M21-D03` Telemetry archiving and trend analysis
- `M21-D04` Anomaly response procedures
- `M21-D05` LEOP and commissioning phase planning
- `M21-D06` Conjunction assessment and collision avoidance
- `M21-D07` End-of-life disposal and deorbit obligations

**Where to learn it**

- [Yamcs](https://yamcs.org/) — Free open-source mission control software
- [OpenC3 COSMOS](https://openc3.com/) — Free command and telemetry system
- [Space-Track](https://www.space-track.org/) — Conjunction data messages and TLEs (free registration)
- [ISRO](https://www.isro.gov.in/) — PSLV rideshare and NSIL launch services

---

### Module 22 — Indian regulation & programme management

*Stage 5 · Months 12–18 · start the paperwork earlier than feels necessary · 21 topics · codes `M22-A01`–`M22-D05`*

**A · India — space**  (codes `M22-A01`–`M22-A06`)

- `M22-A01` Indian Space Policy 2023 and non-government entity provisions
- `M22-A02` IN-SPACe authorisation process and application portal
- `M22-A03` WPC / DoT spectrum licensing via Saral Sanchar
- `M22-A04` ITU filing route through WPC
- `M22-A05` DGFT and SCOMET export clearance for space hardware
- `M22-A06` Remote sensing data policy in India and resolution limits

**B · India — balloon flights**  (codes `M22-B01`–`M22-B06`)

- `M22-B01` DGCA rules for unmanned free balloons
- `M22-B02` Notification and NOTAM process
- `M22-B03` Airspace constraints over Gujarat and near airports
- `M22-B04` Powered return: what it changes in the application
- `M22-B05` Third-party liability and recovery obligations
- `M22-B06` Local police and district permissions in practice

**C · International**  (codes `M22-C01`–`M22-C04`)

- `M22-C01` Outer Space Treaty, Liability Convention, Registration Convention
- `M22-C02` IARU amateur frequency coordination
- `M22-C03` Export control basics: ITAR and EAR, and what you can legally buy
- `M22-C04` Space debris mitigation: IADC guidelines and ISO 24113

**D · Programme management**  (codes `M22-D01`–`M22-D05`)

- `M22-D01` Cost estimation models for smallsats
- `M22-D02` Procurement lead times for space-grade parts
- `M22-D03` Risk register and active risk management
- `M22-D04` Launch insurance and third-party liability
- `M22-D05` Building a programme schedule that survives contact with reality

**Where to learn it**

- [IN-SPACe](https://www.inspace.gov.in/inspace) — Authorisation norms, guidelines, application portal
- [DGCA India](https://www.dgca.gov.in/) — Civil aviation rules, including unmanned free balloons
- [Saral Sanchar (WPC licensing portal)](https://saralsanchar.gov.in/) — Where wireless licence applications are filed
- [ITU — Space Services](https://www.itu.int/en/ITU-R/space/Pages/default.aspx) — Filing procedures and radio regulations
- [IARU](https://www.iaru.org/) — Amateur satellite frequency coordination

---

### Module 23 — Judging work & reading the industry

*Stage 5 · Months 12–18 · the module that makes you dangerous in a room · 24 topics · codes `M23-A01`–`M23-D07`*

**A · Running a design review**  (codes `M23-A01`–`M23-A06`)

- `M23-A01` What to ask at a preliminary design review
- `M23-A02` What to ask at a critical design review
- `M23-A03` The five questions that expose a weak design in ten minutes
- `M23-A04` Interrogating a margin: where it came from and who owns it
- `M23-A05` Demanding the number behind every qualitative claim
- `M23-A06` Spotting a budget that was reverse-engineered from the answer

**B · Judging people and work**  (codes `M23-B01`–`M23-B06`)

- `M23-B01` Confidence versus competence, and how to tell them apart
- `M23-B02` Spotting a copied architecture nobody on the team understands
- `M23-B03` Always asking for the failure mode, never only the happy path
- `M23-B04` Take-home design problems that reveal real skill
- `M23-B05` Reviewing an analysis you could not have produced yourself
- `M23-B06` Knowing when to defer to an expert — and saying so plainly

**C · Reading critically**  (codes `M23-C01`–`M23-C05`)

- `M23-C01` Method before abstract, always
- `M23-C02` Spotting cherry-picked test regions in EO papers
- `M23-C03` Benchmark inflation and leaderboard gaming
- `M23-C04` When a published accuracy number is meaningless
- `M23-C05` Separating a video demo from a deployed product

**D · The industry map**  (codes `M23-D01`–`M23-D07`)

- `M23-D01` Who sells imagery, who sells analytics, who sells platforms
- `M23-D02` How EO data is actually priced, and why analytics margins are thin
- `M23-D03` Where free Sentinel and Landsat data destroys a business model
- `M23-D04` What the large EO companies actually sell versus what they market
- `M23-D05` Where Indian players and ISRO's commercial arm fit
- `M23-D06` The gap between what clients ask for and what they will pay for
- `M23-D07` Which parts of the stack are commoditising fastest

**Where to learn it**

- [SmallSat Conference proceedings](https://digitalcommons.usu.edu/smallsat/) — Free papers — the best raw material for judgement
- [eoPortal](https://www.eoportal.org/) — Compare any two missions' real specifications
- [NASA Engineering Network — lessons learned](https://llis.nasa.gov/) — Public database of real engineering failures

---

### Module 24 — Build track — balloon programme

*Stage 5 · Runs alongside every stage · not after it · 44 build steps · codes `M24-A01`–`M24-G04`*

**A · Month 2 — first signal**  (codes `M24-A01`–`M24-A06`)

- `M24-A01` Assemble RTL-SDR, SAWbird+ NOAA filter and V-dipole
- `M24-A02` Install SatDump, GNU Radio and Gpredict
- `M24-A03` Predict a NOAA or Meteor-M pass for your location
- `M24-A04` Decode your first weather satellite image
- `M24-A05` Log image quality against pass elevation — your first real dataset
- `M24-A06` Measure your noise floor and identify local interference

**B · Months 4–6 — bench payload**  (codes `M24-B01`–`M24-B07`)

- `M24-B01` Pico 2 W running, reading a sensor over I2C
- `M24-B02` NEO-7M GPS achieving lock and logging NMEA
- `M24-B03` BNO085 streaming orientation at a usable rate
- `M24-B04` Pressure and temperature sensor added and calibrated
- `M24-B05` Data logging to storage with power-loss safety
- `M24-B06` Measure real current draw of every component
- `M24-B07` Build the actual power budget from measured numbers, not datasheets

**C · Months 7–9 — integration**  (codes `M24-C01`–`M24-C08`)

- `M24-C01` Orange Pi capturing camera frames reliably
- `M24-C02` Cloud-screening model running on the NPU, benchmarked on-board
- `M24-C03` Live georeferencing of each frame from GPS and attitude
- `M24-C04` Telemetry downlink working over the air at range
- `M24-C05` Servo-controlled camera pointing
- `M24-C06` Reaction wheel demo: brushless motor holding a single axis
- `M24-C07` Sun-pointing demo using the BPW34 photodiodes
- `M24-C08` Full payload assembled in its flight enclosure

**D · Months 10–12 — qualification**  (codes `M24-D01`–`M24-D08`)

- `M24-D01` Cold test: full payload at −40 °C or below
- `M24-D02` Low-pressure test and condensation behaviour
- `M24-D03` Drop test and landing survivability
- `M24-D04` Range test: telemetry over 10 km line of sight
- `M24-D05` Battery capacity measured cold, not warm
- `M24-D06` Day-in-the-life run: full mission profile on the bench
- `M24-D07` DGCA notification and permissions filed
- `M24-D08` Recovery plan, chase team and tracking redundancy

**E · Month 13 — flight 1**  (codes `M24-E01`–`M24-E06`)

- `M24-E01` Launch site selection and weather window analysis
- `M24-E02` Fill, release and ascent
- `M24-E03` Live telemetry and streaming held through ascent
- `M24-E04` Controlled descent and powered return below 10 km
- `M24-E05` Recovery
- `M24-E06` Post-flight data review: what the numbers actually said

**F · Months 14–15 — flight 2**  (codes `M24-F01`–`M24-F05`)

- `M24-F01` Fix everything flight 1 exposed
- `M24-F02` Wide-area imaging and weather profile objective defined
- `M24-F03` Autonomous navigation to base
- `M24-F04` Flight 2
- `M24-F05` Reusable-radiosonde case written up with real flight data

**G · Months 16–18 — toward the CubeSat**  (codes `M24-G01`–`M24-G04`)

- `M24-G01` What the two flights proved, and what they could not
- `M24-G02` CubeSat concept of operations
- `M24-G03` Preliminary design package: orbit, budgets, payload, architecture
- `M24-G04` The honest list of what you still cannot do alone

**Where to learn it**

- [SondeHub](https://sondehub.org/) — Live radiosonde tracking and prediction tools
- [CUSF landing predictor](https://predict.sondehub.org/) — Predict balloon flight path and landing site
- [Stratospheric balloon community (UKHAS wiki)](https://ukhas.org.uk/) — Practical high-altitude ballooning knowledge
- [DGCA India](https://www.dgca.gov.in/) — Rules for unmanned free balloons
- [SatDump](https://www.satdump.org/) — Decode weather satellite imagery from month 2

---

## Study materials

The library behind the modules: the books worth owning, the free courses worth finishing, the primary documents to read instead of summaries, and the open data to practise on.

### Spine books

*Buy these. Everything else is free. The first two carry the whole plan.*

- Wertz & Larson — Space Mission Analysis and Design (SMAD) — Book · the single reference for the whole satellite path. Read a chapter alongside each module.
- Curtis — Orbital Mechanics for Engineering Students — Book · module 3. Worked problems; do them, don't read them.
- Markley & Crassidis — Spacecraft Attitude Determination and Control — Book · module 8. The definitive pointing text.
- Patel — Spacecraft Power Systems — Book · module 6.
- Gilmore — Spacecraft Thermal Control Handbook — Book · module 9. Industry standard.
- Maral & Bousquet — Satellite Communications Systems — Book · module 7. Link budget maths done properly.
- Lillesand — Remote Sensing and Image Interpretation — Book · module 12. The standard course text.
- Schott — Remote Sensing: The Image Chain Approach — Book · modules 11–12. Links optics to final image quality.
- Iliffe & Lott — Datums and Map Projections — Book · module 13. The serious treatment of datums.
- Jensen — Introductory Digital Image Processing — Book · modules 12 and 14. Classification and accuracy assessment.

### Free courses & training

*Structured, finishable, no cost. Start GMAT and ARSET in month 1.*

- [MIT OCW 16.851 — Satellite Engineering](https://ocw.mit.edu/courses/16-851-satellite-engineering-fall-2003/pages/lecture-notes/) — Lecture notes covering orbits, power, ADCS, thermal, optics, environment
- [MIT OCW 16.842 — Fundamentals of Systems Engineering](https://ocw.mit.edu/courses/16-842-fundamentals-of-systems-engineering-fall-2015/) — Full course built around the V-model · module 4
- [MIT OCW 16.83X — Space Systems Engineering](https://ocw.mit.edu/courses/16-83x-space-systems-engineering-spring-2002-spring-2003/) — Capstone-level mission design
- [NASA ARSET](https://appliedsciences.nasa.gov/arset) — Free applied remote sensing and EO machine learning training, with certificates
- [EO College](https://eo-college.org/) — Free ESA-backed courses, strong on radar and SAR
- [Spatial Thoughts](https://spatialthoughts.com/) — Free India-based QGIS, Python and Earth Engine courses
- [Google Earth Engine tutorials](https://developers.google.com/earth-engine/tutorials) — Fastest way to test a geospatial idea at continental scale
- [Dive into Deep Learning (d2l.ai)](https://d2l.ai/) — Free interactive book · module 15 foundations
- [Khan Academy — physics and linear algebra](https://www.khanacademy.org/science/physics) — Module 1 warm-up, exactly the right level
- [3Blue1Brown — Essence of Linear Algebra](https://www.3blue1brown.com/topics/linear-algebra) — Builds the intuition behind rotations and quaternions

### Primary documents & standards

*Read these instead of blog summaries of them. This is what you will be held to.*

- [NASA CubeSat 101](https://www.nasa.gov/wp-content/uploads/2017/03/nasa_csli_cubesat_101_508.pdf) — Free PDF · the whole mission process end to end. Read twice.
- [CubeSat Design Specification (Cal Poly)](https://www.cubesat.org/cubesatinfo) — The mechanical rulebook · module 5
- [NASA State of the Art — Small Spacecraft Technology](https://www.nasa.gov/smallsat-institute/sst-soa) — Flight-proven hardware by subsystem, updated yearly. Your component reality check.
- [NASA Technical Standards (incl. GEVS)](https://standards.nasa.gov/) — Test levels and environmental requirements · module 19
- [ECSS standards](https://ecss.nl/) — European space standards, free registration · modules 4 and 19
- [CCSDS standards](https://public.ccsds.org/default.aspx) — Free telemetry, telecommand and compression standards · modules 7, 10, 12
- [OGC standards](https://www.ogc.org/standards/) — WMS, WFS, WMTS and the rest · module 17
- [STAC specification](https://stacspec.org/) — The catalogue standard EO data is converging on

### Free data to practise on

*Never learn an analysis on a toy dataset. Use real scenes over Gujarat.*

- [Copernicus Data Space](https://dataspace.copernicus.eu/) — Sentinel-1 and Sentinel-2, including raw levels
- [USGS EarthExplorer](https://earthexplorer.usgs.gov/) — The full Landsat archive, plus declassified historical imagery
- [NASA Earthdata Search](https://search.earthdata.nasa.gov/) — MODIS, VIIRS, thermal, atmospheric and climate products
- [Alaska Satellite Facility](https://asf.alaska.edu/) — SAR data and processing recipes · module 12
- [ISRO Bhuvan](https://bhuvan.nrsc.gov.in/) — Indian satellite data and national thematic layers
- [data.gov.in](https://data.gov.in/) — Indian government open data, including census and administrative boundaries
- [OpenStreetMap extracts (Geofabrik)](https://download.geofabrik.de/asia/india.html) — Free vector base data for India, by state
- [Copernicus DEM](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM) — Global 30 m elevation · needed for orthorectification
- [STAC Index](https://stacindex.org/) — Directory of open STAC catalogues worth pointing a pipeline at

### Software to install

*All free, or free for personal and student use. Install the first group in week one.*

- [GMAT (NASA)](https://sourceforge.net/projects/gmat/) — Mission analysis and orbit design
- [Gpredict](http://gpredict.oz9aec.net/) — Pass prediction, tracking, Doppler correction
- [GNU Radio + SatDump](https://www.satdump.org/) — SDR processing and live weather-satellite decoding
- [QGIS](https://qgis.org) — The GIS you will live in
- [GDAL / rasterio / GeoPandas](https://gdal.org/) — The engine under almost every geospatial tool
- [ESA SNAP](https://step.esa.int/main/toolboxes/snap/) — Sentinel-1 and Sentinel-2 processing end to end
- [PostGIS](https://postgis.net/documentation/) — The reference spatial database · module 17
- [PySAL and GeoDa](https://pysal.org/) — Spatial statistics · module 14
- [TorchGeo](https://torchgeo.readthedocs.io/) — EO datasets, models and samplers · module 15
- [ONNX Runtime](https://onnxruntime.ai/) — Edge inference on the Orange Pi · module 16
- [FreeCAD and KiCad](https://www.freecad.org/) — Structure and PCB design
- [FreeRTOS](https://www.freertos.org/) — Flight software foundations · module 10
- [Yamcs or OpenC3 COSMOS](https://yamcs.org/) — Real mission control software · module 21

### Papers, archives & communities

*Where judgement actually comes from. Budget time here every week.*

- [SmallSat Conference proceedings](https://digitalcommons.usu.edu/smallsat/) — Free full-text papers. Search 'lessons learned' first.
- [NASA Lessons Learned Information System](https://llis.nasa.gov/) — Public database of real engineering failures · module 23
- [eoPortal](https://www.eoportal.org/) — Specifications for almost every EO mission ever flown
- [arXiv — eess.IV and astro-ph.IM](https://arxiv.org/list/eess.IV/recent) — Open preprints for EO imaging and space instrumentation
- [Satellite image deep learning — techniques](https://github.com/satellite-image-deep-learning/techniques) — Curated index of EO AI datasets, models and papers
- [AMSAT](https://www.amsat.org/) — Amateur satellite community: frequencies, ground stations, coordination
- [UKHAS wiki](https://ukhas.org.uk/) — Practical high-altitude ballooning knowledge · module 24
- [SondeHub](https://sondehub.org/) — Live radiosonde tracking and landing prediction · module 24
- [IN-SPACe](https://www.inspace.gov.in/inspace) — Indian authorisation norms, guidelines and the application portal

---

## A closing note on what this is for

The balloon is not a hobby project. It is the cheapest honest rehearsal for everything the satellite will have to do: pointing, power, thermal, link budget, onboard autonomy, recovery and paperwork — all of it, at 35 km, for the price of a laptop.

*Links in this document were assembled in October 2026 and were not all individually verified. Treat a dead link as a stale link, not as evidence the resource is gone.*

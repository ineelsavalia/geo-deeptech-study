# Balloon Programme — Bill of Materials

> **Note for any AI reading this file.** This is the costed bill of materials for versions 1 and 2 of a stratospheric balloon payload, built by a geospatial deep-tech founder in Gujarat, India. It is the companion to **Geospatial & Deep Tech — 18 Month Study Plan** (587 topics, each with a code like `M05-B01`) and **Teaching Contract — Geospatial & Deep Tech** (how to teach them). Topic codes referenced below point into the study plan. Prices are planning estimates in INR, not quotations; the few that are grounded in a source say so. Read "What changes the BOM" before treating any line as settled.

**Version 1 as specified:** ~35 km, camera, sensors, live telemetry and streaming, wings for controlled descent, propellers deployed below ~10 km for powered return to base.

**Version 2 as specified:** flown about two months later; a wide-area weather and imaging profile positioned as a reusable alternative to disposable radiosondes.

Both are concept designs, not final architecture. This is the budget envelope for those concepts.

---

## The headline

| | Amount |
|---|---|
| Programme total as specified, with contingency | **₹952,248** |
| Your stated budget, high end | ₹600,000 |
| Gap | **−₹352,248** |
| Over budget by | **59%** |

Versions 1 and 2 as specified do not fit 5 to 6 lakh. Taking every cut on the list below still leaves it at ₹696,648. The option that fits is a shakedown flight plus version 1, with version 2 deferred to a second budget cycle: ₹606,048, which is 101% of your high budget.

| Version 1 flying payload mass, as listed | 4,450 g |
|---|---|

---

## What changes the BOM — read before buying

### Findings that would cost you a payload

**The radio licence gates the whole link design**

A published amateur build sent 640x480 video at 12 fps from a balloon using 1 W of FSK on the 70 cm band with LDPC coding, received past 50 km. In India, 1 W on 433 MHz is amateur-band operation. The licence-free allowance in 433-434.79 MHz is about 10 mW ERP, a hundred times less power. The amateur route means the ASOC exam, and the Restricted grade permits voice only, which does not cover a data downlink. Digital privileges need a higher grade, and Grade I requires a Morse test. After passing there is police verification, which takes months. Start this in month 1. It is the longest-lead item in the programme and it decides what link you may legally fly.

**Licence-free telemetry works, but the duty cycle does not allow video**

India permits up to 500 mW ERP in 865-868 MHz for tracking, tracing and data acquisition, with adaptive power control mandatory and a 2.5% duty cycle. That is ample for position and housekeeping telemetry and nowhere near enough for live video. Note also that the Indian band tops out at 868 MHz, so the standard European LoRa channels at 868.1, 868.3 and 868.5 MHz fall outside it. Use the India 865-867 plan.

**Your GPS probably works, but prove it**

I expected the NEO-7M to stop at the 18 km export-control limit. Checking it, the u-blox 6/7/8 family combines its altitude and speed limits with AND logic, so it keeps reporting above 18 km as long as speed stays under 515 m/s, and is rated to about 50 km in flight mode. The real risk is that clone boards do not persist the airborne dynamic model across a power cycle. Test it: set airborne mode, power cycle, confirm it still reports. Buy one known-good module as primary and keep yours as secondary.

**A barometer rated for aviation is not rated for the stratosphere**

Pressure at 35 km is about 5 to 6 hPa. A common BMP280 bottoms out near 300 hPa, which is roughly 9 km, so it would stop reading about a quarter of the way up. Specify the minimum pressure from the datasheet rather than an altitude claim in a product listing. This is the most commonly mis-specified part on a balloon payload.

**Your servos and propeller are sized for the wrong air**

MG996R servos are not rated for stratospheric cold and weigh about 55 g each. Use them for bench and drop testing, and buy cold-rated servos for flight. Separately, air at 10 km is roughly a quarter of sea-level density, so your A2212 with a 1045 propeller will not produce the thrust it does on the bench. Expect a larger diameter and a higher pitch, and test at altitude-equivalent loading rather than assuming.

### The finding that challenges version 1 as specified

**Returning to base from 35 km is the highest-risk requirement in the programme**

A documented autonomous glider flight aimed for a 30 km release and settled for 10 km, because forecast stratospheric winds would have carried the vehicle hundreds of miles out over the ocean. From its 10 km release it still flew about 196 km in a little over two hours, at a top speed near 95 m/s, and landed roughly 10 m from its target waypoint. It used a Pixhawk commanded over MAVLink by a Raspberry Pi Zero, weighed about 1300 g, and the team made six drop tests from a quadcopter before flying it. Two things follow. First, the glide approach works and is proven, which answers your doubt about it. Second, the wind problem at 35 km is real and was enough to make an experienced team lower their release altitude by two thirds. Your version 1 asks for 35 km and a powered return to the launch point. That is a harder problem than the documented precedent, on a first flight. Recommendation: fly a tracker-only shakedown first. It costs a balloon, gas and a few thousand rupees of tracker, and it tells you what the winds over Gujarat actually do to a descending payload. Then commit the expensive vehicle.

### How to read the prices in this workbook

**Three figures are grounded, the rest are estimates**

Grounded: helium at about 2,300 rupees for a 7 cubic metre balloon-grade cylinder, from a current Indian supplier listing. The radio architecture and the glider architecture, both from published builds named above. Everything else is a planning estimate, marked as such in the price basis column. Re-quote before ordering, and expect import duty and shipping on anything not available in India.

**Two lines are deliberately left at zero**

The RF test report on the fees sheet, and the antenna rotator on the ground station sheet. Both are real possible costs that should not be budgeted until a question is answered: whether you need your own type approval at all, and whether manual antenna tracking actually limits you. Filling in a guess for either would make the rollup look more certain than it is.

**Mass is the number that moves the budget**

The balloon and its gas are the largest consumable, and balloon size follows from payload mass. An extra 500 g can push you up a balloon size and add a cylinder of helium. Weigh parts as they arrive and keep the mass column current. Separate the flying payload mass from the lift and recovery hardware when you build the real budget; the version 1 sheet totals them together.

### Where this connects to the study plan

**The BOM is module 5 and module 6 made physical**

M05-B01 is building a mass budget with margin per item. M06-C01 to M06-C03 are the energy balance. M07-B05 is the link budget that decides whether your downlink can carry what your camera produces. M19-D01 to M19-D04 are the budget-constrained environmental tests this workbook funds. Do not finalise any of these numbers before you have worked through those modules. The point of the plan is that you can defend each figure yourself.

---

## Already in hand

*Listed at zero cost so the programme total reflects only new spending. The caveat column matters more than the credit: three of these items need checking or replacing before they fly. Hover the item name where a comment marker appears.*


**ALREADY IN HAND — credited against the programme, with the caveats that matter**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| ALR-01 | **Orange Pi 4 Pro 6 GB, 3 TOPS NPU**<br>Onboard compute and the GeoAI payload (modules 15 and 16). Benchmark it yourself; the advertised TOPS figure will not predict sustained throughput in a sealed warm box. | 1 | ₹0 | ₹0 | 120 | Y | Owned | — | Owned |
| ALR-02 | **Raspberry Pi Pico 2 W and LAFVIN kit**<br>Sensor and housekeeping microcontroller, independent of the main computer. Good practice: let the small reliable thing hold the telemetry. | 1 | ₹0 | ₹0 | 15 | Y | Owned | — | Owned |
| ALR-03 | **Nooelec RTL-SDR v5, SAWbird+ NOAA LNA, V-dipole**<br>Complete receive chain for weather satellite imagery. This is build step M24-A01 and needs nothing further. | 1 | ₹0 | ₹0 | — | Y | Owned | — | Owned |
| ALR-04 | **BNO085 9-DOF IMU**<br>Attitude sensing for the pointing demonstration (M24-C06) and for the glider. | 1 | ₹0 | ₹0 | 12 | Y | Owned | — | Owned |
| ALR-05 | **NEO-7M GPS modules, two**<br>Usable as the secondary GPS. The u-blox 6/7/8 family keeps working above 18 km when set to the airborne dynamic model, but verify the setting survives a power cycle on these clone boards. | 2 | ₹0 | ₹0 | 15 | Y | Owned — verify airborne mode persists | — | Owned |
| | ⚠ Test this specifically: set airborne mode, power cycle, and confirm it still reports. A GPS that silently stops at 18 km loses the vehicle. | | | | | | | | |
| ALR-06 | **A2212 1000KV motor, 30 A ESC, 1045 props**<br>Propulsion starting point. The 1045 prop is sized for sea level; expect to fit a larger, higher-pitch prop for 8–10 km. | 1 | ₹0 | ₹0 | 120 | Y | Owned | — | Owned |
| ALR-07 | **MG996R servos**<br>Bench and drop testing only. Not rated for stratospheric cold, and heavy at roughly 55 g each. | 1 | ₹0 | ₹0 | 55 | Y | Owned — not flight rated | — | Owned |
| | ⚠ Keep these for ground testing. Flying them is the kind of avoidable single-point failure module 20 is about. | | | | | | | | |
| ALR-08 | **BPW34 photodiodes, five**<br>Sun sensing for the sun-tracking demonstration (M24-C07) and the satellite attitude work in module 8. | 5 | ₹0 | ₹0 | 1 | Y | Owned | — | Owned |
| ALR-09 | **Logic analyser, 8 channel, 24 MHz**<br>I2C, SPI and UART debugging. Covers most of what you will need on the bench. | 1 | ₹0 | ₹0 | — | Y | Owned | — | Owned |

**Already in hand total: ₹0** · flying payload mass 357 g

---

## Version 1 — full bill of materials

*Version 1 as specified: ~35 km, camera, sensors, live telemetry and streaming, wings for controlled descent, propellers deployed below ~10 km for powered return to base. Prices are planning estimates in INR and must be re-quoted at purchase time. Blue cells are yours to edit. Mass drives balloon size, so fill the mass column before ordering the balloon.*


**LIFT & RECOVERY — the consumable half of every flight**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-01 | **Sounding balloon, 3000 g latex**<br>Sized for a ~3 kg payload to 33–35 km. A 2000 g balloon tops out near 2 kg; confirm against your own mass budget (module 5, M05-B01) before ordering. | 1 | ₹26,000 | ₹26,000 | 3,000 | N | Estimate — verify with supplier | Pawan Exports (India) or import | To buy |
| | ⚠ Balloon size follows directly from total payload mass. Do the mass budget first: an extra 500 g can push you up a balloon size and add a cylinder of gas. | | | | | | | | |
| V1-02 | **Sounding balloon, spare**<br>One spare. A burst or mishandled balloon on fill day otherwise ends the campaign. | 1 | ₹26,000 | ₹26,000 | 3,000 | N | Estimate — verify with supplier | Same as above | To buy |
| V1-03 | **Helium, balloon grade, 7 m³ cylinder**<br>About 14–17 m³ of fill for a 3 kg payload with adequate free lift, so three cylinders. Industrial balloon-grade is adequate; research grade is not needed. | 3 | ₹2,800 | ₹8,400 | — | N | Verified: ₹2,300/7 m³ cylinder listed on IndiaMART (Jaipur, 2026) | Local industrial gas supplier | To buy |
| | ⚠ Helium supply in India is intermittent and priced by region. Book early and confirm cylinder availability before fixing a launch date. | | | | | | | | |
| V1-04 | **Cylinder regulator, fill hose and nozzle**<br>Reusable across flights. Must match the cylinder valve standard your supplier uses. | 1 | ₹10,000 | ₹10,000 | — | N | Estimate | Industrial gas supplier | To buy |
| V1-05 | **Parachute, 1.8 m ripstop nylon**<br>Independent of the glider. If the glider fails to release or its control fails, this is what stops the payload becoming a falling object. | 1 | ₹6,000 | ₹6,000 | 350 | Y | Estimate | RC / rocketry supplier | To buy |
| | ⚠ Not optional. This is the difference between a failed flight and an incident. | | | | | | | | |
| V1-06 | **Rigging set: cord, swivels, carabiners, load tape**<br>50 m braided nylon, rated well above payload mass, plus swivels to stop the train spinning. | 1 | ₹2,500 | ₹2,500 | 250 | N | Estimate | Local / hardware | To buy |
| V1-07 | **Nichrome cutdown and relay**<br>Releases the glider from the balloon train at the chosen altitude. The documented Rutgers glider flight used exactly this method. | 2 | ₹1,200 | ₹2,400 | 40 | Y | Method verified from published glider flight | Electronics supplier | To buy |

**AIRFRAME — the glider that does the real work of getting home**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-08 | **Glider airframe, 1.6–2.0 m span**<br>EPP or foamboard with carbon spars. The published 10 km glider drop was a homemade foamcore body at about 1300 g all-in and flew 196 km. | 1 | ₹15,000 | ₹15,000 | 700 | Y | Mass verified from published flight (≈1300 g total vehicle) | RC supplier / self-built | To buy |
| | ⚠ Build two. The first airframe is a prototype whatever you intend it to be. | | | | | | | | |
| V1-09 | **Glider airframe, second unit**<br>For drop testing. The published flight made six test drops from a quadcopter before the balloon flight. | 1 | ₹15,000 | ₹15,000 | 700 | N | Practice verified from published flight | Same as above | To buy |
| V1-10 | **Carbon tube and rod spar set**<br>Wing spar and tail boom. Carbon keeps stiffness at low temperature where foam alone goes floppy. | 1 | ₹4,000 | ₹4,000 | 120 | Y | Estimate | RC supplier | To buy |
| V1-11 | **Control surface hardware: horns, linkages, hinges, film**<br>Consumable. Buy twice what you think you need. | 1 | ₹3,500 | ₹3,500 | 80 | N | Estimate | RC supplier | To buy |
| V1-12 | **Servos, metal gear digital, low-temperature rated**<br>Four: two elevons or aileron/elevator, one rudder, one spare channel. Specify a rated operating temperature below −40 °C. | 4 | ₹2,500 | ₹10,000 | 60 | Y | Estimate | RC supplier | To buy |
| | ⚠ Your MG996R servos are not rated for stratospheric cold and are heavy at ~55 g each. Keep them for bench and drop testing only; buy cold-rated servos for flight. | | | | | | | | |
| V1-13 | **Airspeed sensor and pitot tube**<br>The flight controller needs airspeed, not just GPS ground speed, to hold a glide at altitude where true airspeed and indicated airspeed diverge sharply. | 1 | ₹4,000 | ₹4,000 | 30 | Y | Estimate | Drone supplier | To buy |
| | ⚠ At 35 km, indicated airspeed is a small fraction of true airspeed. A controller flying on GPS speed alone will stall or overspeed. | | | | | | | | |

**PROPULSION — only useful below about 10 km**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-14 | **Propeller set, folding, 11–13 inch, assorted pitch**<br>Air at 10 km is roughly a quarter of sea-level density, so the same motor needs a larger, higher-pitch prop to produce the same thrust. Buy a range and test. | 1 | ₹3,500 | ₹3,500 | 60 | Y | Density figure from the standard atmosphere | RC supplier | To buy |
| | ⚠ Your A2212 1000KV with a 1045 prop is sized for sea level. Expect to go to a bigger diameter and higher pitch for 8–10 km. | | | | | | | | |
| V1-15 | **Brushless motor, lower KV alternative**<br>A second motor option with lower KV and a bigger prop is usually more efficient at altitude than spinning a small prop faster. | 1 | ₹3,000 | ₹3,000 | 70 | Y | Estimate | RC supplier | To buy |
| V1-16 | **Propeller deployment mechanism**<br>Folding props self-deploy under rotation; a servo-held latch keeps them stowed during ascent and descent. | 1 | ₹2,500 | ₹2,500 | 80 | Y | Estimate | Self-built / 3D printed | To buy |
| V1-17 | **Spare motor and ESC**<br>Props and motors are the parts most likely to be damaged on landing. | 1 | ₹3,500 | ₹3,500 | 120 | N | Estimate | RC supplier | To buy |

**FLIGHT CONTROL & NAVIGATION**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-18 | **Flight controller, Pixhawk class**<br>The published glider used a Pixhawk with GPS, commanded over MAVLink by a Raspberry Pi Zero, and landed about 10 m from its target waypoint. | 1 | ₹18,000 | ₹18,000 | 40 | Y | Architecture verified from published glider flight | Drone supplier | To buy |
| | ⚠ Use an autopilot with a documented autonomous glide and return-to-launch mode. Do not write your own guidance loop. | | | | | | | | |
| V1-19 | **GPS module, altitude-capable u-blox M8/M10**<br>Primary navigation. Must be set to the airborne dynamic model. The u-blox 6/7/8 family combines its altitude and speed limits with AND logic, so it keeps working above 18 km while under 515 m/s. | 1 | ₹5,000 | ₹5,000 | 15 | Y | Verified: UKHAS GPS module guide | Electronics supplier | To buy |
| | ⚠ Your NEO-7M should work to high altitude once set to airborne mode, but clone boards often fail to persist that configuration across a power cycle. Buy a known-good module as primary and verify the setting survives a reboot before flight. Keep the NEO-7M as the secondary. | | | | | | | | |
| V1-20 | **GPS module, secondary**<br>Independent of the primary, ideally a different model. Losing position means losing the vehicle. | 1 | ₹4,000 | ₹4,000 | 15 | Y | Estimate | Electronics supplier | To buy |
| V1-21 | **External magnetometer / compass**<br>Away from the motor and power wiring, or the heading will be wrong exactly when the propellers run. | 1 | ₹2,200 | ₹2,200 | 20 | Y | Estimate | Drone supplier | To buy |

**COMPUTE & IMAGING**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-22 | **Camera module, global shutter, nadir**<br>Global shutter avoids the rolling-shutter smear a swinging payload produces. Nadir view is the one that georeferences cleanly. | 1 | ₹8,000 | ₹8,000 | 40 | Y | Estimate | Electronics supplier | To buy |
| V1-23 | **Camera module, horizon**<br>The horizon shot is what people actually want to see, and it is useful for attitude verification after the flight. | 1 | ₹6,000 | ₹6,000 | 40 | Y | Estimate | Electronics supplier | To buy |
| V1-24 | **Lens set, wide and narrow**<br>Field of view sets your swath; focal length sets your ground resolution. This is module 11 (M11-A01) made physical. | 1 | ₹5,000 | ₹5,000 | 60 | Y | Estimate | Optics supplier | To buy |
| V1-25 | **High-endurance microSD cards, 128 GB**<br>Onboard recording is the guaranteed data path. The radio link is a bonus, not the record. | 3 | ₹1,500 | ₹4,500 | 2 | N | Estimate | Any retailer | To buy |
| | ⚠ Record everything onboard at full quality. Treat the downlink as a preview, never as the archive. | | | | | | | | |
| V1-26 | **Heatsink and thermal pads for the Orange Pi**<br>Running a model on the NPU in a sealed insulated box is a thermal problem, not only a compute one (M16-B04). | 1 | ₹1,200 | ₹1,200 | 60 | Y | Estimate | Electronics supplier | To buy |

**SENSORS**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-27 | **Barometric pressure sensor, MS5611 or BMP390 class**<br>Pressure at 35 km is about 5–6 hPa. A common BMP280 bottoms out near 300 hPa, which is only about 9 km, so it would stop reading three quarters of the way up. | 2 | ₹2,000 | ₹4,000 | 2 | Y | Pressure figure from the standard atmosphere | Electronics supplier | To buy |
| | ⚠ Check the minimum pressure in the datasheet, not just the maximum altitude a seller claims. This is the single most commonly mis-specified sensor on a balloon payload. | | | | | | | | |
| V1-28 | **External air temperature probe, PT1000 with amplifier**<br>Radiation-shielded and mounted clear of the payload box, or you will measure the box rather than the atmosphere. | 2 | ₹3,000 | ₹6,000 | 25 | Y | Estimate | Instrumentation supplier | To buy |
| V1-29 | **Humidity sensor, SHT85 class**<br>Needed for the radiosonde-replacement story in version 2; worth flying in version 1 to characterise it. | 1 | ₹3,500 | ₹3,500 | 5 | Y | Estimate | Electronics supplier | To buy |
| V1-30 | **Thermistors for internal monitoring**<br>Six points: battery, each camera, the Orange Pi, the radio, and ambient inside the box. | 8 | ₹80 | ₹640 | 2 | Y | Estimate | Electronics supplier | To buy |

**COMMUNICATIONS — read the legal note on the Rules sheet before buying**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-31 | **Imagery and telemetry downlink transmitter, 70 cm**<br>A published amateur build used a 1 W FSK transmitter on 70 cm with LDPC coding to send 640×480 video at 12 fps within a 200 kbit/s budget, received beyond 50 km. | 1 | ₹6,000 | ₹6,000 | 25 | Y | Verified: published amateur balloon video build | Import / electronics supplier | To buy |
| | ⚠ LEGAL GATE. 1 W on 433 MHz is amateur-band operation and requires an Indian amateur licence with digital privileges. The licence-free 433–434.79 MHz allowance is about 10 mW ERP, which is a hundred times less power. See the Rules sheet. | | | | | | | | |
| V1-32 | **LoRa module, 865–867 MHz, ETA-compliant**<br>The licence-free path. India permits up to 500 mW ERP in 865–868 MHz for tracking, tracing and data acquisition, with adaptive power control and a 2.5% duty cycle. | 2 | ₹3,000 | ₹6,000 | 10 | Y | Verified: G.S.R. 853(E) short range device rules, Table II | Electronics supplier | To buy |
| | ⚠ The 2.5% duty cycle is the catch. It is ample for position and housekeeping telemetry and nowhere near enough for live video. Plan the link budget around that (M07-B05). | | | | | | | | |
| V1-33 | **Airborne antennas: quarter-wave ground plane and dipole**<br>Built, not bought, mostly. Budget covers wire, SMA connectors and a spare. | 1 | ₹3,000 | ₹3,000 | 60 | Y | Estimate | Electronics supplier | To buy |
| V1-34 | **Independent GSM/GPS tracker**<br>A completely separate recovery path that needs no equipment of yours to work. It acquires signal on the way down below about 3 km. | 2 | ₹3,000 | ₹6,000 | 60 | Y | Method verified from published glider flight (car-style GSM tracker as backup) | Any retailer | To buy |
| | ⚠ Independent means separate battery, separate antenna, separate everything. A backup sharing the main power bus is not a backup. | | | | | | | | |
| V1-35 | **Satellite tracker, Iridium short-burst or Swarm**<br>The only tracker that reports from anywhere, including the 35 km cruise and a landing with no cellular coverage. Expensive, and the difference between recovering the vehicle and writing it off. | 1 | ₹32,000 | ₹32,000 | 80 | Y | Estimate — verify current hardware and airtime pricing | Import | To buy |
| | ⚠ Weigh this against the cost of the payload it protects. If the vehicle is worth more than the tracker, buy the tracker. | | | | | | | | |
| V1-36 | **RF cabling, pigtails and connectors**<br>Consumable. Bad connectors cause more link failures than bad radios. | 1 | ₹3,000 | ₹3,000 | 40 | Y | Estimate | Electronics supplier | To buy |

**POWER & THERMAL**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-37 | **Lithium AA primary cells for avionics**<br>Lithium iron disulfide AA cells hold capacity down to roughly −40 °C, where ordinary alkaline cells collapse. The standard choice for balloon avionics. | 24 | ₹250 | ₹6,000 | 15 | Y | Estimate | Any retailer | To buy |
| | ⚠ Measure your real capacity cold, not warm (M06-B03). A battery characterised at room temperature will mislead you about flight duration. | | | | | | | | |
| V1-38 | **LiPo pack, 4S, for propulsion**<br>Only the propellers need this much current, and only below 10 km. Size it for the powered leg, not the whole flight. | 2 | ₹5,500 | ₹11,000 | 400 | Y | Estimate | RC supplier | To buy |
| V1-39 | **Battery protection and balancing board**<br>For the LiPo packs. A cell going out of balance in flight is unrecoverable. | 2 | ₹900 | ₹1,800 | 20 | Y | Estimate | RC supplier | To buy |
| V1-40 | **DC-DC regulators, 5 V and 12 V**<br>Efficiency at low load matters more than peak rating here; most of the flight is a light load (M06-C06). | 4 | ₹700 | ₹2,800 | 25 | N | Estimate | Electronics supplier | To buy |
| V1-41 | **Battery heater pads and thermostat**<br>Keeping the battery warm is usually the tightest thermal constraint on the vehicle. | 2 | ₹1,200 | ₹2,400 | 40 | Y | Estimate | Electronics supplier | To buy |
| | ⚠ The published glider flight used chemical hand warmers sealed in the fuselage to stop the electronics freezing. Simple, and it worked. | | | | | | | | |
| V1-42 | **Chemical hand warmers**<br>Zero power, zero complexity, and a documented solution on a real stratospheric glider flight. | 30 | ₹40 | ₹1,200 | 20 | N | Method verified from published glider flight | Any retailer | To buy |
| V1-43 | **Power distribution board, fuses, arming plug**<br>One obvious physical arming point. You do not want propellers live while you are holding the vehicle. | 1 | ₹2,500 | ₹2,500 | 80 | Y | Estimate | Electronics supplier | To buy |
| | ⚠ A remove-before-flight arming plug is a safety requirement, not a nicety. Module 6 (M06-C09) covers the equivalent on a satellite. | | | | | | | | |
| V1-44 | **Wiring, connectors and heat shrink**<br>XT60, JST and silicone-insulated wire. PVC insulation goes brittle in the cold. | 1 | ₹3,000 | ₹3,000 | 120 | Y | Estimate | Electronics supplier | To buy |

**STRUCTURE, ENCLOSURE & THERMAL PROTECTION**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V1-45 | **Extruded polystyrene foam, 50 mm**<br>The payload enclosure. Cheap, light, and the standard material for this job. | 1 | ₹1,500 | ₹1,500 | 300 | Y | Estimate | Local hardware | To buy |
| V1-46 | **Multi-layer insulation or aerogel sheet**<br>For the battery and any component with a narrow temperature window. | 1 | ₹5,000 | ₹5,000 | 80 | Y | Estimate | Import / specialist | To buy |
| V1-47 | **Mounting hardware, standoffs, vibration isolation**<br>Everything must survive the landing, which is the highest-shock event of the flight. | 1 | ₹2,500 | ₹2,500 | 150 | Y | Estimate | Local hardware | To buy |
| V1-48 | **Tapes: Kapton, aluminium, gaffer, and zip ties**<br>Consumable across every build and test. | 1 | ₹2,500 | ₹2,500 | 100 | N | Estimate | Local / electronics | To buy |
| V1-49 | **3D printing filament, PETG and ASA**<br>Brackets, camera mounts, antenna bases. PLA is unsuitable: it is brittle in the cold. | 2 | ₹1,800 | ₹3,600 | 200 | N | Estimate | Any retailer | To buy |

**Version 1 — full bill of materials total: ₹315,140** · flying payload mass 4,450 g

---

## Version 2 — additions and changes only

*Version 2 reuses the version 1 avionics, radios, power system and ground station. Only the deltas are listed here, so the programme total is version 1 plus this sheet. Version 2 as discussed: a wide-area weather and imaging profile positioned as a reusable alternative to disposable radiosondes.*


**WHAT CHANGES FOR VERSION 2 — flown about two months after version 1**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| V2-01 | **Airframe, third unit, longer range**<br>Version 2 trades the return-to-base demonstration for coverage: a wider wing and a better glide ratio buy range for the wide-area weather and imaging profile. | 1 | ₹25,000 | ₹25,000 | 900 | Y | Estimate | RC supplier / self-built | To buy |
| | ⚠ Decide before building whether version 2 returns to base or flies a long one-way profile. The two airframes are not the same vehicle. | | | | | | | | |
| V2-02 | **Calibrated humidity and temperature sensor set**<br>For the reusable-radiosonde claim you need instruments you can defend against a reference, not hobby sensors. | 1 | ₹18,000 | ₹18,000 | 60 | Y | Estimate — verify against instrument suppliers | Instrumentation supplier | To buy |
| | ⚠ The whole commercial story is that one reusable unit replaces many disposable ones. That claim only survives if the measurements are traceable. | | | | | | | | |
| V2-03 | **Higher-resolution or multispectral camera**<br>The imaging half of the version 2 profile. Specify it from the ground resolution and swath you actually need, not from the highest number available (M11-C02). | 1 | ₹35,000 | ₹35,000 | 120 | Y | Estimate | Import / specialist | To buy |
| V2-04 | **Extended battery capacity**<br>A longer flight profile needs more energy. Re-run the energy balance rather than adding cells by feel (M06-C03). | 1 | ₹12,000 | ₹12,000 | 500 | Y | Estimate | As above | To buy |
| V2-05 | **Second satellite tracker**<br>Two independent long-range trackers once the flight profile takes the vehicle beyond easy reach. | 1 | ₹32,000 | ₹32,000 | 80 | Y | Estimate | Import | To buy |
| V2-06 | **Sounding balloon, 3000 g, and spare**<br>Two more balloons for flight 2 and its reflight margin. | 2 | ₹26,000 | ₹52,000 | 3,000 | N | Estimate — verify with supplier | Pawan Exports (India) or import | To buy |
| V2-07 | **Helium, 7 m³ cylinders, flight 2**<br>Three cylinders again, assuming a similar payload mass. | 3 | ₹2,800 | ₹8,400 | — | N | Verified: ₹2,300/7 m³ listed on IndiaMART (Jaipur, 2026) | Local gas supplier | To buy |
| V2-08 | **Spares and replacements from flight 1 lessons**<br>Reserved, unallocated. Every documented first flight produces a list of things to replace. | 1 | ₹25,000 | ₹25,000 | — | N | Allowance | Various | To buy |
| | ⚠ Do not allocate this line until flight 1 has flown. Its purpose is to absorb what you have not thought of yet. | | | | | | | | |

**Version 2 — additions and changes only total: ₹207,400** · flying payload mass 1,660 g

---

## Ground station

*Reused across every flight and the most valuable thing you can build early. It turns link budgets, Doppler and pass planning from abstractions into measurements. Your RTL-SDR v5, SAWbird+ NOAA filter and V-dipole already cover weather satellite reception.*


**RECEIVE CHAIN — build this in month 2, long before anything flies**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| GRO-01 | **Software defined radio, 14-bit class**<br>Your RTL-SDR v5 is 8-bit and adequate for weather satellite imagery. A 14-bit receiver gives real dynamic range for a weak payload downlink; the published balloon video build used one. | 1 | ₹24,000 | ₹24,000 | — | Y | Verified: receiver class named in published balloon video build | Import | To buy |
| | ⚠ Start with the RTL-SDR you own. Buy this when you can show, with a measurement, that the receiver is your limiting factor. | | | | | | | | |
| GRO-02 | **Low noise amplifier, 70 cm**<br>At the antenna, not at the radio. Cable loss ahead of the amplifier is unrecoverable. | 1 | ₹4,000 | ₹4,000 | — | Y | Estimate | Electronics supplier | To buy |
| GRO-03 | **Yagi antenna, 70 cm, 7–11 element**<br>The published build tracked a balloon with a hand-held directional antenna on a tripod and held the link past 50 km. | 1 | ₹8,000 | ₹8,000 | — | Y | Verified: method from published balloon video build | Import / self-built | To buy |
| GRO-04 | **Tripod with manual azimuth/elevation mount**<br>Manual tracking first. A rotator is an optimisation of something that already works. | 1 | ₹6,000 | ₹6,000 | — | Y | Estimate | Photography / local | To buy |
| GRO-05 | **Low-loss coaxial cable, 20 m, with connectors**<br>LMR-400 class. Thin coax at 433 MHz over 20 m throws away much of what the antenna gained. | 1 | ₹5,500 | ₹5,500 | — | Y | Estimate | Electronics supplier | To buy |
| GRO-06 | **LoRa 865 MHz receiver and antenna**<br>The licence-free telemetry path, independent of the amateur-band downlink. | 1 | ₹6,000 | ₹6,000 | — | Y | Estimate | Electronics supplier | To buy |
| GRO-07 | **Field power: portable battery and inverter**<br>The ground station runs where the launch is, not where the mains is. | 1 | ₹11,000 | ₹11,000 | — | Y | Estimate | Any retailer | To buy |
| GRO-08 | **Azimuth/elevation rotator**<br>DEFER. Only once manual tracking is proven to be the constraint. | 1 | ₹0 | ₹0 | — | Y | Deferred — set cost when you decide to buy | Import | Deferred |
| | ⚠ Left at zero deliberately. Fill in a price only when manual tracking has been shown to limit you. | | | | | | | | |

**Ground station total: ₹64,500**

---

## Test equipment and tools

*Bought once, used across both flights and into the CubeSat work. Your 8-channel logic analyser already covers I2C, SPI and UART debugging.*


**BENCH — needed from month 4, when the payload starts coming together**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| TES-01 | **Bench power supply, 0–30 V, 5 A, current limited**<br>For measuring real current draw per component, which is how a power budget gets built from measurements instead of datasheets (M06-C01). | 1 | ₹9,000 | ₹9,000 | — | Y | Estimate | Electronics supplier | To buy |
| TES-02 | **Digital multimeter, good quality**<br>You will trust this instrument for every electrical decision. Buy one you can trust. | 1 | ₹5,000 | ₹5,000 | — | Y | Estimate | Electronics supplier | To buy |
| TES-03 | **Temperature-controlled soldering station with hot air**<br>Hot air for the surface-mount sensor breakouts. | 1 | ₹9,000 | ₹9,000 | — | Y | Estimate | Electronics supplier | To buy |
| TES-04 | **Precision scale, 0.1 g to 5 kg**<br>Mass budget work. Every gram changes the balloon sizing, so weigh the parts rather than trusting the listings. | 1 | ₹4,500 | ₹4,500 | — | Y | Estimate | Any retailer | To buy |
| TES-05 | **Oscilloscope, 2 channel, 100 MHz**<br>DEFER if budget is tight. Your logic analyser covers the digital bus debugging you will do most often. | 1 | ₹30,000 | ₹30,000 | — | Y | Estimate | Electronics supplier | Deferred |

**ENVIRONMENTAL TEST — needed from month 10, before flight 1**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| TES-06 | **Vacuum chamber and two-stage pump**<br>Tests the payload at stratospheric pressure. Low pressure changes thermal behaviour, kills convective cooling, and finds sealing failures. | 1 | ₹22,000 | ₹22,000 | — | Y | Estimate | Lab supplier | To buy |
| | ⚠ Test as you fly. A payload tested only at sea-level pressure has been tested as a different object (M19-D02). | | | | | | | | |
| TES-07 | **Dry ice for cold testing, per campaign**<br>Cheapest route to −60 °C-class testing. Budget per test campaign rather than buying a freezer outright. | 4 | ₹2,000 | ₹8,000 | — | Y | Estimate | Industrial gas supplier | To buy |
| TES-08 | **Chest freezer for repeated cold soak**<br>Optional alternative to dry ice if you expect many cold cycles. Reaches roughly −20 °C, not stratospheric, but useful for repeated functional testing. | 1 | ₹18,000 | ₹18,000 | — | Y | Estimate | Any retailer | Optional |
| TES-09 | **Load cell and lift measurement rig**<br>Measures neck lift on fill day. Guessing the fill is how balloons burst low or ascend too slowly. | 1 | ₹3,500 | ₹3,500 | — | Y | Estimate | Local / electronics | To buy |
| TES-10 | **Anemometer and weather instruments**<br>Launch-day go/no-go decisions at the site. | 1 | ₹3,000 | ₹3,000 | — | Y | Estimate | Any retailer | To buy |
| TES-11 | **Gas handling safety kit: gloves, goggles, trolley, first aid**<br>Compressed gas cylinders are the most immediately dangerous thing in this entire programme. | 1 | ₹5,000 | ₹5,000 | — | Y | Estimate | Safety supplier | To buy |

**Test equipment and tools total: ₹117,000**

---

## Per-flight recurring costs

*Excludes the balloon and gas, which are listed on the version 1 and version 2 sheets. Multiply this sheet by the number of launch attempts, not the number of flights you plan.*


**PER FLIGHT — recurring, and the reason a lost payload hurts twice**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| PER-01 | **Chase vehicle fuel and tolls**<br>Gujarat, planning for a recovery drive of up to 200 km each way. The published glider flew 196 km from a 10 km release. | 1 | ₹4,500 | ₹4,500 | — | Y | Range verified from published glider flight | — | Per flight |
| PER-02 | **Satellite tracker airtime**<br>Monthly plan plus per-message cost. Verify current pricing when you buy the hardware. | 2 | ₹2,000 | ₹4,000 | — | Y | Estimate — verify with provider | Provider | Per flight |
| PER-03 | **Mobile data and connectivity for the field team**<br>Live tracking and prediction updates from the launch site. | 1 | ₹1,000 | ₹1,000 | — | Y | Estimate | — | Per flight |
| PER-04 | **Consumables: tape, cord, cable ties, batteries**<br>Replaced every flight. | 1 | ₹3,000 | ₹3,000 | — | Y | Estimate | Local | Per flight |
| PER-05 | **Contingency for a second launch attempt**<br>Weather scrubs happen. Budget for travelling to the site and not launching. | 1 | ₹5,000 | ₹5,000 | — | Y | Allowance | — | Per flight |

**Per-flight recurring costs total: ₹17,500**

---

## Fees, licences and permissions

*These cost little and take the longest. Two of them gate the flight entirely: the radio licence decides what link you may legally run, and the DGCA permission decides whether you may fly at all.*


**PERMISSIONS AND FEES — the longest-lead items in the programme**

| Ref | Item | Qty | Unit | Line cost | Mass ea (g) | Flies | Price basis | Where | Status |
|---|---|---|---|---|---|---|---|---|---|
| FEE-01 | **Amateur radio licence: ASOC exam and licence fee**<br>The exam is a 100-mark written paper plus a Morse test, except for the Restricted grade. After passing there is police verification, and the process takes a few months. | 1 | ₹2,000 | ₹2,000 | — | Y | Verified: Indian amateur licensing information (VU2MSY) | WPC, Ministry of Communications | To start |
| | ⚠ CRITICAL PATH. The Restricted grade permits voice only on VHF/UHF, which does not cover a data downlink. Digital modes need a higher grade, and Grade I requires Morse. Start this in month 1, not month 12. | | | | | | | | |
| FEE-02 | **Equipment Type Approval, if required**<br>ETA is a self-declaration process on the Saral Sanchar portal for licence-free band equipment, reported at ₹10,000 per model. | 1 | ₹10,000 | ₹10,000 | — | Y | Verified: reported ETA fee, to be confirmed on the portal | DoT Saral Sanchar | To verify |
| | ⚠ Confirm whether ETA applies to you at all. It is normally the obligation of a manufacturer or importer, and buying an already-certified module may discharge it. Verify before budgeting a test report. | | | | | | | | |
| FEE-03 | **RF test report for ETA, if required**<br>Only if you must certify a module yourself. Verify necessity first, because this line is large. | 1 | ₹0 | ₹0 | — | Y | Left at zero pending the ETA question | Accredited lab | To verify |
| | ⚠ Deliberately zero. If you find you do need your own test report, this becomes one of the larger single lines in the programme. | | | | | | | | |
| FEE-04 | **DGCA notification for an unmanned free balloon**<br>Notification and NOTAM process, plus airspace coordination. A powered return changes how the application is read. | 1 | ₹5,000 | ₹5,000 | — | Y | Estimate — fees to be confirmed with DGCA | DGCA | To start |
| | ⚠ Start the conversation early and in writing. A powered, controlled return is not an ordinary free balloon, and the category matters. | | | | | | | | |
| FEE-05 | **Local and district permissions, launch site**<br>Police and district administration, plus any landowner agreement at the site. | 1 | ₹5,000 | ₹5,000 | — | Y | Estimate | Local authorities | To start |
| FEE-06 | **Third-party liability insurance**<br>Ask for a quote early. The answer also tells you how an underwriter reads your risk. | 1 | ₹15,000 | ₹15,000 | — | Y | Estimate — obtain a quote | Insurer | To verify |

**Fees, licences and permissions total: ₹37,000**

---

## Budget rollup

| Line | Cost | Note |
|---|---|---|
| Already in hand | ₹0 | Credited at zero. Three items need checking or replacing before flight. |
| Version 1 flight hardware | ₹315,140 | Includes the balloon, gas and a spare balloon for flight 1. Mass column shows flying payload only. |
| Version 2 additions | ₹207,400 | Deltas only. Reuses the version 1 avionics, radios and power system. |
| Ground station | ₹64,500 | Reused across every flight and into the satellite work. |
| Test equipment and tools | ₹117,000 | Bought once. Includes two lines marked deferred. |
| Per-flight recurring costs | ₹52,500 | Multiplied by three launch attempts, not two flights. Weather scrubs happen. |
| Fees, licences and permissions | ₹37,000 | Two lines are unresolved and left at zero. See the Rules sheet. |
| **Subtotal** | **₹793,540** | New spending before contingency. |
| Contingency at 20% | ₹158,708 | Breakage, re-orders, shipping, customs, and what you have not thought of. |
| **PROGRAMME TOTAL** | **₹952,248** | |
| Your budget, high end | ₹600,000 | As you stated it. |
| **Headroom** | **−₹352,248** | Negative means it does not fit. |

---

## Making it fit

### The cut path, in order

| Cut | Saves | Running total | What it costs you |
|---|---|---|---|
| Defer the oscilloscope | ₹30,000 | ₹30,000 | Your logic analyser covers the digital bus debugging you will actually do. Buy a scope when you can name the measurement you cannot make without one. |
| Defer the 14-bit SDR | ₹24,000 | ₹54,000 | Start with the RTL-SDR v5 you own. Buy the better receiver when a measurement shows the receiver is your limiting factor, not before. |
| Drop the chest freezer, use dry ice | ₹18,000 | ₹72,000 | Dry ice reaches stratospheric-class cold; the freezer only reaches about minus 20. Keep the dry ice line and lose the appliance. |
| One satellite tracker, not two | ₹32,000 | ₹104,000 | Carry it over from flight 1 to flight 2 rather than buying a second. You lose redundancy on the long-range link, so keep two independent GSM trackers. |
| Defer the version 2 imaging upgrade | ₹35,000 | ₹139,000 | Fly version 2 on the version 1 cameras. Specify the upgrade from what flight 1 and flight 2 actually show you need, which is the honest order anyway. |
| Defer the calibrated sensor set to flight 3 | ₹18,000 | ₹157,000 | The reusable-radiosonde claim needs traceable instruments, but it does not need them before you have proven the vehicle returns. |
| One spare balloon across both flights, not two | ₹26,000 | ₹183,000 | Buy three balloons rather than four. You accept that a second burst on fill day ends that campaign. |
| Halve the unallocated version 2 spares | ₹12,500 | ₹195,500 | From 25,000 to 12,500. Thin, and the first thing to restore if flight 1 goes badly. |
| Trim third launch attempt allowance | ₹17,500 | ₹213,000 | Budget two launch attempts rather than three. You accept that a second weather scrub costs you money you have not set aside. |
| **Total saved** | **₹213,000** | | |

**After all the cuts:** ₹696,648, which is 116% of the high budget. Still over.

### The cuts are not enough

Taking every cut above still leaves the programme over your budget. That is the honest result, and it points at one conclusion: two full flights plus a complete ground station plus a test bench plus the licences is roughly a seven lakh programme, not a six lakh one. The way to fit six lakh is not to shave it further. It is to stop after version 1 and let version 2 fall into the next budget cycle, which is also the right engineering order, since version 2 should be specified from what version 1 actually teaches you.

### Option: shakedown plus version 1, version 2 deferred

| Line | Amount |
|---|---|
| Version 2 spending removed | −₹83,900 |
| Second helium fill, for the shakedown flight | ₹8,400 |
| Subtotal | ₹505,040 |
| Contingency at the same rate | ₹101,008 |
| PROGRAMME TOTAL, this option | ₹606,048 |
| Headroom against the high budget | −₹6,048 |
| Share of the high budget | 101.0% |

One caveat on that total: it funds two balloons and two fills, which the shakedown and version 1 consume between them. It retains no spare balloon. If a balloon bursts on fill day, that campaign stops until you buy another, at roughly 26,000 rupees plus gas. Decide deliberately whether you are carrying that risk or budgeting it.

### The cheaper option I would actually take

Before either of these flights, fly a shakedown: one balloon, one parachute, two independent trackers, a camera and the sensor board. No glider, no propellers, no return to base. It costs roughly a balloon, three cylinders of gas and the trackers, and it buys you the one thing no calculation gives you, which is what the winds over Gujarat actually do to a payload descending from 35 km. A documented autonomous glider team aimed for a 30 km release and settled for 10 km for exactly that reason. Fly the cheap one first and the expensive vehicle second, and the odds of recovering the expensive vehicle go up sharply.

**Shakedown flight, rough cost: ₹45,000** — balloon, gas, parachute, rigging, two GSM trackers and the chase. Re-quote it; the figure is an estimate.

---

*Prepared October 2026. Prices and regulations both change; re-verify before committing money. Three figures are grounded in named sources: the helium cylinder price, the radio architecture, and the glider architecture. Everything else is a planning estimate.*

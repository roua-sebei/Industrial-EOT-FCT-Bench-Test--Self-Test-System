# EOT Bench Self-Test System

**Test bench diagnostics | LabVIEW | Hardware verification**

> An engineering  project completed in an industrial setting. This repository presents the approach and outcomes; proprietary schematics, production software, and customer data are not published.

## Overview

This project consists of developing an external self-test device and a LabVIEW application to verify the resources of a generic EOT test bench before product testing.

The system checks the bench’s digital inputs and outputs, relays, fixed power supplies, and multimeter measurement lines. Its purpose is to help distinguish bench faults from product faults and support troubleshooting.

## Engineering challenge

A product test failure can originate from the product itself or from the test bench. Identifying the source requires checking that the bench resources operate correctly.

Key objectives:

- Develop a dedicated hardware device for checking bench resources.
- Automate verification through a LabVIEW application.
- Verify digital I/O, relay switching, power supplies, and measurement paths.
- Present diagnostic results to support maintenance and troubleshooting.

## System architecture

```mermaid
flowchart TD
    A["LabVIEW self-test application"] <--> B["EOT bench resources"]
    B <--> C["External self-test device"]
    B --> D["Acquired measurements and states"]
    D --> E["Verification against expected results"]
    E --> F["Diagnostic results"]
```

## Hardware implementation

The external self-test device connects to the EOT bench and provides the electrical paths required to verify its resources.

The hardware and LabVIEW application work together to stimulate outputs, acquire input states, and check measurement paths.
### Self-test device

<img src="Screenshot 2026-07-01 120142.png" alt="External EOT bench self-test device" width="700">

## Verification coverage

| Resource | Verification |
| --- | --- |
| Digital outputs | Check commanded output states through the self-test connections. |
| Digital inputs | Verify that applied states are correctly acquired. |
| Relays | Check switching operation and associated electrical paths. |
| Fixed power supplies | Verify the 24 V, 12 V, and 5 V supplies. |
| Multimeter lines | Check the measurement paths used by the bench. |
| Continuity paths | Verify continuity through the relevant self-test connections. |

## LabVIEW application

The LabVIEW application coordinates the verification sequence, communicates with the bench resources, and evaluates the acquired measurements and digital states.

The results help identify which resource or electrical path requires further investigation.
### Application interface

<img src="Screenshot 2026-06-21 095815.png" alt="LabVIEW self-test application interface" width="800">

## LabVIEW maintenance application

During development and debugging of the automatic self-test, a second need emerged: allowing technicians to control bench resources individually and observe their responses.

A dedicated LabVIEW maintenance VI was added to bring manual control of digital I/O and other bench resources into one interface. This supports targeted investigation when a self-test identifies a failing path.

### Automatic self-test and maintenance control

| Application | Purpose |
| --- | --- |
| Automatic self-test | Execute the verification sequence and identify failing bench resource paths. |
| Maintenance application | Manually control individual resources and inspect their responses during troubleshooting. |

The two applications support a complementary workflow: the automatic self-test detects a problem, and the maintenance application helps investigate the affected resource.

### Maintenance interface

<img src="Screenshot 2026-08-31 133952.png" alt="LabVIEW bench maintenance and manual resource control interface" width="800">
## Operating workflow

1. Connect the external self-test device to the EOT bench.
2. Launch the LabVIEW self-test application.
3. Run the verification sequence.
4. Review the diagnostic results.
5. Investigate any detected faults before product testing.

## Outcome

- Developed an external device for verifying EOT bench resources.
- Implemented automated verification using LabVIEW.
- Combined digital I/O, relay, power supply, and measurement-path checks.
- Provided a diagnostic tool to support bench troubleshooting before product testing.

## Technologies and skills

`LabVIEW` · `Test Bench Diagnostics` · `Digital I/O` · `Relay Testing` · `Voltage Measurement` · `Continuity Testing` · `Hardware Integration` · `Test Automation` · `Troubleshooting`

## Project context

Graduation engineering project carried out at **Eleonetech (OneTech Group)**.

The descriptions reflect the author's engineering work and are provided for portfolio purposes, not as an official company reference or a complete reproducible implementation.

## Related project

**Automotive Fuse Box PCB: FCT-to-EOT Test Migration**

Migration of an automotive fuse-box PCB functional test system to the generic EOT bench.

[View the project](https://github.com/roua-sebei/Automotive-Fuse-Box_PCB-FCT-Test)

---

**Author:** Roua Sebii · Embedded Systems Engineer

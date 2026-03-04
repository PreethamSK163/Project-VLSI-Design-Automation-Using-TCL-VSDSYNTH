# Project — VLSI Design Automation Using TCL — VSDSYNTH

> A fully automated, design-agnostic RTL-to-QoR synthesis and timing analysis framework built using TCL — integrating Yosys and OpenTimer through CSV-driven configuration, SDC constraint generation, and professional CLI reporting.

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tool](https://img.shields.io/badge/Tool-TCL-blue)
![Tool](https://img.shields.io/badge/Tool-Yosys-blue)
![Tool](https://img.shields.io/badge/Tool-OpenTimer-blue)
![PDK](https://img.shields.io/badge/PDK-OSU%200.18µm-orange)
![Language](https://img.shields.io/badge/Language-Verilog%20HDL-purple)
![Program](https://img.shields.io/badge/Program-NASSCOM%20FutureSkills%20Prime-red)
![License](https://img.shields.io/badge/License-GPL%20v3-blue)

<h2>🔍 Overview</h2>

- Developed **VSDSYNTH** — a fully automated, design-agnostic RTL-to-QoR framework using TCL scripting, driven entirely by CSV configuration files containing design details and timing constraints.
- The framework integrates **Yosys** for RTL synthesis and **OpenTimer** for static timing analysis — automating the complete flow from CSV parsing through netlist generation, SDC constraint creation, STA execution, and QoR dashboard reporting.

<h2>🛠️ Tools & Technology Stack</h2>

| Category | Tool / Technology |
|---|---|
| Scripting Language | TCL (tclsh) |
| Shell Wrapper | tcsh |
| Synthesis | Yosys + ABC |
| Static Timing Analysis | OpenTimer |
| Standard Cell Library | OSU 0.18µm |
| RTL Design (Test) | openMSP430 |
| HDL | Verilog |
| OS | Ubuntu Linux |

<h2>⚙️ Complete Automation Flow</h2>

| Stage | Description | Status |
|---|---|---|
| CLI & Argument Validation | Shell wrapper with argument checks, file validation, and help system | ✅ Complete |
| CSV Parsing & Variable Creation | CSV-to-TCL variable engine, directory management, environment setup | ✅ Complete |
| Clock Constraint Generation | Automated SDC `create_clock` generation from CSV timing data | ✅ Complete |
| Input Constraint Generation | Port categorization, RTL scanning, `set_input_delay`, `set_input_transition` | ✅ Complete |
| Output Constraint Generation | `set_output_delay`, `set_load` — full boundary timing coverage | ✅ Complete |
| Yosys Synthesis | Dynamic script generation, hierarchy check, error handling, netlist output | ✅ Complete |
| Netlist Sanitization | Post-synthesis regex-based cleanup for STA compatibility | ✅ Complete |
| SDC to OpenTimer Translation | Clock, input/output delays, transitions, bit-blasting for buses | ✅ Complete |
| STA Execution | Automated OpenTimer configuration, execution, and log capture | ✅ Complete |
| QoR Extraction & Reporting | Instance count, WNS, FEP — CLI dashboard and CSV report | ✅ Complete |

<h2>📊 Key Features</h2>

| Feature | Details |
|---|---|
| Design Agnostic | CSV-driven configuration — works across any RTL design |
| Smart Port Parser | Distinguishes single-bit and multi-bit bussed signals automatically |
| Bit-Blasting Engine | Expands bus constraints to individual bits for granular STA coverage |
| Hierarchy Validation | Detects missing modules and structural RTL issues before synthesis |
| Error Handling | Graceful termination with actionable CLI feedback on all failure modes |
| SDC Translation | Full SDC-to-OpenTimer conversion — clocks, delays, transitions, latency |
| QoR Dashboard | Professional CLI table with Instance Count, WNS, FEP, Pass/Fail status |
| CSV Reporting | Automated CSV output for design sign-off and result tracking |

## 📁 Repository Structure
```
📁 Project-TCL-VLSI-Automation-VSDSYNTH
├── 📁 01 : TCL Toolbox Setup          → CLI wrapper, argument validation, help system
├── 📁 02 : CSV Parsing                → Variable creation, environment setup, matrix parsing
├── 📁 03 : Constraint Generation      → Clock, input, output SDC constraint automation
├── 📁 04 : Synthesis & Error Handling → Yosys script generation, hierarchy check, error handling
├── 📁 05 : QoR Generation             → STA execution, QoR extraction, dashboard, CSV report
├── 📄 vsdsynth.tcl                    → Main automation script
└── 📄 README.md
```

<h2>📝 Stage Details</h2>

**01 — TCL Toolbox Setup** &nbsp;|&nbsp; `tcsh` `tclsh` `CLI`

Developed the `vsdsynth` shell wrapper using `tcsh` — implemented argument validation, file existence checks, and a dynamic `-help` subsystem. Only validated CSV inputs are passed to the TCL synthesis engine. Defensive programming practices applied to handle all user error scenarios clearly.
> 📁 [View Implementation Results](./01%20:%20TCL%20Toolbox%20Setup)

**02 — CSV Parsing & Variable Creation** &nbsp;|&nbsp; `struct::matrix` `csv` `TCL Arrays`

Built a TCL-based CSV parsing engine using `struct::matrix` and `csv` packages. Automated variable assignment, absolute path mapping, directory validation, and intelligent directory creation. Runtime debug dashboard implemented for immediate variable verification.
> 📁 [View Implementation Results](./02%20:%20CSV%20Parsing)

**03 — Constraint Generation** &nbsp;|&nbsp; `SDC` `create_clock` `set_input_delay`

Automated generation of complete SDC timing constraints from CSV data — clock definitions, input delays, input transitions, and output delays. Smart port parser developed to distinguish single-bit and bussed signals. Dynamic RTL scanning implemented to extract port names directly from Verilog sources.
> 📁 [View Implementation Results](./03%20:%20Constraint%20Generation)

**04 — Synthesis & Error Handling** &nbsp;|&nbsp; `Yosys` `yosys_run.tcl` `Hierarchy Check`

Generated dynamic Yosys synthesis scripts with absolute paths for all RTL sources and standard cell libraries. Automated hierarchy validation to detect structural RTL issues before synthesis. Graceful error handling implemented to halt the flow on synthesis failures while preserving output integrity.
> 📁 [View Implementation Results](./04%20:%20Synthesis%20%26%20Error%20Handling)

**05 — QoR Generation** &nbsp;|&nbsp; `OpenTimer` `WNS` `FEP` `CSV Report`

Translated SDC constraints to OpenTimer format — clocks, input/output delays, transitions, and bit-blasted bus constraints. Automated OpenTimer configuration file generation and STA execution. QoR metrics extracted — Instance Count, WNS, FEP — and presented in a professional CLI dashboard with CSV report output.
> 📁 [View Implementation Results](./05%20:%20QoR%20Generation)

<h2>📈 QoR Results — openMSP430 (Pre-Layout)</h2>

Validated on the **openMSP430** 16-bit RISC microcontroller — 23 Verilog RTL modules synthesized to OSU 0.18µm standard cells.

| Metric | Value |
|---|---|
| Gate Count | 6,845 |
| Hierarchy Check | PASS (0 errors) |
| Paths Analyzed | 10,000 |
| Critical Path Depth | 67–83 logic levels |
| Synthesis Runtime | ~5 sec (Yosys, peak 70 MB) |


<h2>📚 References</h2>

| **OpenTimer** | [OpenTimer by Tsung-Wei Huang, UIUC](https://github.com/OpenTimer/OpenTimer) |
|:---|:---|
| **Synthesis** | [Yosys by Claire Wolf](https://github.com/YosysHQ/yosys) |
| **Standard Cell Library** | [OSU Standard Cell Library](https://vlsiarch.ecen.okstate.edu/flows/) |

<h2>📄 License</h2>

This project is licensed under the **GNU General Public License v3.0** — as used by OpenTimer developed by Tsung-Wei Huang, University of Illinois at Urbana-Champaign.

<h2>🤝 Connect</h2>

| **Author** | Preetham SK |
|:---|:---|
| **Program** | NASSCOM FutureSkills Prime — VSD (VLSI System Design) |
| **LinkedIn** | [linkedin.com/in/preethamsk16](https://www.linkedin.com/in/preethamsk16) |
| **GitHub** | [github.com/PreethamSK163](https://github.com/PreethamSK163) |
| **Email** | preethamsk163@gmail.com |

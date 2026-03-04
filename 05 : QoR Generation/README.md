# QoR Generation
> STA Execution, SDC-to-OpenTimer Translation & QoR Dashboard — VSDSYNTH

![Tool](https://img.shields.io/badge/Tool-OpenTimer-blue)
![Tool](https://img.shields.io/badge/Tool-TCL-blue)
![Tool](https://img.shields.io/badge/Tool-Yosys-blue)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Completed the full RTL-to-QoR automation — from synthesis script finalization and netlist sanitization through SDC-to-OpenTimer constraint translation, automated STA execution, and professional QoR dashboard generation.
- Achieved a fully push-button flow with zero manual intervention from RTL to timing sign-off reporting.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| Synthesis Script Finalization | End-to-end Yosys synthesis, technology mapping, netlist generation |
| Netlist Sanitization | Regex-based cleanup, backslash removal, STA-ready formatting |
| TCL Array Commands | Associative array data management, metric tracking, structured info flow |
| Modular TCL Procedures | Functional decomposition, reusable `proc` blocks, scalable framework |
| Library & RTL Loading Procs | `read_lib`, `read_verilog` procedures, path validation, CLI logging |
| SDC to OpenTimer Conversion | Constraint syntax translation — clocks, delays, transitions |
| Clock Latency Translation | `set_clock_latency` → OpenTimer `at` arrival time mapping |
| Input Transition & Delay | `set_input_transition`, `set_input_delay` → OpenTimer `slew` and `at` |
| Output Constraint Conversion | `set_output_delay` → `rat`, `set_load` → capacitance definitions |
| Bit-Blasting Engine | Bus decomposition, scalar expansion, bit-level constraint replication |
| OpenTimer Config Generation | Automated `.conf` creation, library linking, STA execution sequencing |
| QoR Metric Extraction | Instance count, WNS setup/hold, FEP — parsed from logs |
| Dashboard & Report Generation | CLI QoR table, CSV report, Pass/Fail evaluation |

<h2>📝 Stage Details</h2>

**Task 1 — Synthesis Script Finalization** &nbsp;|&nbsp; `Yosys` `ABC` `OSU018`

Implemented end-to-end synthesis automation — RTL-to-gate using `$DesignName` as root hierarchy. Integrated technology mapping through Yosys `abc` targeting OSU 0.18µm standard cells. Applied post-synthesis optimization to clean redundant logic and eliminate unused wires. Configured batch-mode Yosys execution with detailed log capture for QoR evaluation.

**Task 2 — Automated Netlist Sanitization** &nbsp;|&nbsp; `regsub` `Regex` `OpenTimer`

Developed a post-synthesis netlist refinement engine using regex-based sanitization (`regsub`) to remove escaped characters and backslashes. Standardized bussed signal notation and instance naming for STA tool interoperability. Ensured non-destructive refinement — preserving full gate-level connectivity while producing an OpenTimer-ready netlist.

**Task 3 — TCL Array Commands & Data Structuring** &nbsp;|&nbsp; `Associative Arrays` `Metric Tracking`

Implemented a TCL associative array–based data management layer to organize synthesis and timing metrics. Developed centralized key–value mapping for area, timing slack, and QoR parameters with fast indexed access. Established a structured information flow synchronizing data across Synthesis, STA, and Reporting stages.

**Task 4 — Modular Programming via TCL Procedures** &nbsp;|&nbsp; `proc` `Functional Decomposition`

Refactored the automation flow using functional decomposition — separating environment setup, constraint handling, and synthesis execution into independent `proc` blocks. Implemented reusable procedures for regex-based port extraction, file checks, and directory validation. Established a scalable framework template enabling future EDA tool integrations without altering the core engine.

**Task 5 — Encapsulated Library & RTL Loading Procedures** &nbsp;|&nbsp; `read_lib` `read_verilog` `Path Validation`

Created dedicated `read_lib` and `read_verilog` TCL procedures for modular data ingestion. Integrated pre-execution path validation within each procedure to prevent runtime failures. Added execution-level CLI logging confirming successful library and RTL loading.

**Task 6 — SDC to OpenTimer Format Conversion** &nbsp;|&nbsp; `SDC` `OpenTimer` `Constraint Translation`

Implemented a cross-tool constraint translation engine — converting SDC clock, input/output delay, and transition commands into OpenTimer-compatible syntax. Automated OpenTimer configuration script generation, eliminating manual intervention entirely.

**Task 7 — Clock Latency to Arrival Time Translation** &nbsp;|&nbsp; `set_clock_latency` `at` `Clock Modeling`

Developed automated latency parsing to extract `set_clock_latency` from SDC and map it to OpenTimer `at` (arrival time) syntax. Correctly accounted for both source and network delays, enabling realistic setup and hold slack analysis.

**Task 8 — Input Transition & Delay Translation** &nbsp;|&nbsp; `slew` `at` `Bus Resolution`

Converted SDC `set_input_transition` and `set_input_delay` to OpenTimer `slew` and `at` specifications. Enhanced precision port and bus resolution using intelligent pattern matching for accurate constraint application on scalar and vector ports.

**Task 9 — Output Constraint Conversion** &nbsp;|&nbsp; `rat` `set_load` `Capacitance`

Implemented automated RAT mapping — converting `set_output_delay` to OpenTimer `rat` commands. Developed capacitance translation logic mapping `set_load` values to OpenTimer-compatible definitions. Enabled bus-aware output constraint generation for complete boundary timing coverage.

**Task 10 — Automated Bit-Blasting for Bussed Constraints** &nbsp;|&nbsp; `Bus Expansion` `Bit-Level STA`

Implemented a bit-blasting engine to decompose multi-bit buses into individual scalar signals. Developed uniform constraint replication logic propagating delay and transition values consistently across every bit. Leveraged nested TCL iteration to support arbitrary bus widths — from small controllers to wide datapaths.

**Task 11 — OpenTimer Configuration File Generation** &nbsp;|&nbsp; `conf` `STA Setup` `Automation`

Developed an automated OpenTimer `.conf` generation engine consolidating all timing commands into a single file. Programmatically linked Liberty files and the sanitized gate-level netlist. Enforced sequential STA execution order — initialization, constraint application, timing analysis, and reporting.

**Task 12 — QoR Metric Extraction** &nbsp;|&nbsp; `Instance Count` `WNS` `FEP`

Implemented an automated QoR extraction engine converting raw synthesis and STA logs into actionable metrics. Developed parsers for instance count, worst negative setup/hold slack (WNS), and failing endpoint count (FEP). Enabled sign-off readiness evaluation through automated Pass/Fail status derivation.

**Task 13 — Dashboard & Report Generation** &nbsp;|&nbsp; `CLI Dashboard` `CSV Report` `Sign-off`

Developed a professional CLI-based QoR dashboard presenting Instance Count, WNS, FEP, and Pass/Fail status in a clean tabular format. Implemented automated CSV report generation for result tracking and documentation. Consolidated Yosys synthesis and OpenTimer STA outputs into a single unified sign-off report.

<h2>🖼️ Implementation Results</h2>

### Synthesis Script Finalization
![1](1_Synthesis_script_creation_1.png)
![2](1_Synthesis_script_creation_2.png)

### Automated Netlist Sanitization
![1](2_Edit_output_netlist_1.png)
![2](2_Edit_output_netlist_2.png)
![3](2_Edit_output_netlist_3.png)
![4](2_Edit_output_netlist_4.png)

### TCL Array Commands & Data Structuring
![1](3_TCL_array_commands_1.png)
![2](3_TCL_array_commands_2.png)

### Modular Programming via TCL Procedures
![1](4_Setting_multiple_proc_1.png)
![2](4_Setting_multiple_proc_2.png)
![3](4_Setting_multiple_proc_3.png)
![4](4_Setting_multiple_proc_4.png)
![5](4_Setting_multiple_proc_5.png)
![6](4_Setting_multiple_proc_6.png)
![7](4_Setting_multiple_proc_7.png)
![8](4_Setting_multiple_proc_8.png)
![9](4_Setting_multiple_proc_9.png)
![10](4_Setting_multiple_proc_10.png)
![11](4_Setting_multiple_proc_11.png)
![12](4_Setting_multiple_proc_12.png)

### Encapsulated Library & RTL Loading Procedures
![1](5_read_lib_and_read_verilog_proc_1.png)
![2](5_read_lib_and_read_verilog_proc_2.png)
![3](5_read_lib_and_read_verilog_proc_3.png)
![4](5_read_lib_and_read_verilog_proc_4.png)
![5](5_read_lib_and_read_verilog_proc_5.png)
![6](5_read_lib_and_read_verilog_proc_6.png)

### SDC to OpenTimer Format Conversion
![1](6_Convert_constraint_from_sdc_format_to_opentimer_format_1.png)
![2](6_Convert_constraint_from_sdc_format_to_opentimer_format_2.png)
![3](6_Convert_constraint_from_sdc_format_to_opentimer_format_3.png)
![4](6_Convert_constraint_from_sdc_format_to_opentimer_format_4.png)
![5](6_Convert_constraint_from_sdc_format_to_opentimer_format_5.png)
![6](6_Convert_constraint_from_sdc_format_to_opentimer_format_6.png)
![7](6_Convert_constraint_from_sdc_format_to_opentimer_format_7.png)

### Clock Latency to Arrival Time Translation
![1](7_Convert_set_clock_latency_in_sdc_to_arrival_time_in_opentimer_1.png)
![2](7_Convert_set_clock_latency_in_sdc_to_arrival_time_in_opentimer_2.png)
![3](7_Convert_set_clock_latency_in_sdc_to_arrival_time_in_opentimer_3.png)
![4](7_Convert_set_clock_latency_in_sdc_to_arrival_time_in_opentimer_4.png)
![5](7_Convert_set_clock_latency_in_sdc_to_arrival_time_in_opentimer_5.png)

### Input Transition & Delay Translation
![1](8_Convert_transition_and_input_delay_to_open_timer_format_1.png)
![2](8_Convert_transition_and_input_delay_to_open_timer_format_2.png)
![3](8_Convert_transition_and_input_delay_to_open_timer_format_3.png)
![4](8_Convert_transition_and_input_delay_to_open_timer_format_4.png)
![5](8_Convert_transition_and_input_delay_to_open_timer_format_5.png)
![6](8_Convert_transition_and_input_delay_to_open_timer_format_6.png)
![7](8_Convert_transition_and_input_delay_to_open_timer_format_7.png)
![8](8_Convert_transition_and_input_delay_to_open_timer_format_8.png)
![9](8_Convert_transition_and_input_delay_to_open_timer_format_9.png)
![10](8_Convert_transition_and_input_delay_to_open_timer_format_10.png)
![11](8_Convert_transition_and_input_delay_to_open_timer_format_11.png)
![12](8_Convert_transition_and_input_delay_to_open_timer_format_12.png)
![13](8_Convert_transition_and_input_delay_to_open_timer_format_13.png)

### Output Constraint Conversion
![1](9_Convert_output_sdc_constraints_to_opentime_1.png)
![2](9_Convert_output_sdc_constraints_to_opentime_2.png)
![3](9_Convert_output_sdc_constraints_to_opentime_3.png)
![4](9_Convert_output_sdc_constraints_to_opentime_4.png)

### Automated Bit-Blasting for Bussed Constraints
![1](10_Convert_all_bussed_constraints_to_bit_blasted_1.png)
![2](10_Convert_all_bussed_constraints_to_bit_blasted_2.png)
![3](10_Convert_all_bussed_constraints_to_bit_blasted_3.png)
![4](10_Convert_all_bussed_constraints_to_bit_blasted_4.png)
![5](10_Convert_all_bussed_constraints_to_bit_blasted_5.png)
![6](10_Convert_all_bussed_constraints_to_bit_blasted_6.png)
![7](10_Convert_all_bussed_constraints_to_bit_blasted_7.png)

### OpenTimer Configuration File Generation
![1](11_Opentimer_configuration_file_creation_1.png)
![2](11_Opentimer_configuration_file_creation_2.png)
![3](11_Opentimer_configuration_file_creation_3.png)
![4](11_Opentimer_configuration_file_creation_4.png)
![5](11_Opentimer_configuration_file_creation_5.png)
![6](11_Opentimer_configuration_file_creation_6.png)
![7](11_Opentimer_configuration_file_creation_7.png)

### QoR Metric Extraction
![1](12_Instances_count_wns_fep_for_setup_and_hold_1.png)
![2](12_Instances_count_wns_fep_for_setup_and_hold_2.png)
![3](12_Instances_count_wns_fep_for_setup_and_hold_3.png)
![4](12_Instances_count_wns_fep_for_setup_and_hold_4.png)
![5](12_Instances_count_wns_fep_for_setup_and_hold_5.png)
![6](12_Instances_count_wns_fep_for_setup_and_hold_6.png)

### Dashboard & Report Generation
![1](13_Report_formatting_1.png)
![2](13_Report_formatting_2.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 04 : Synthesis & Error Handling](../04%20:%20Synthesis%20%26%20Error%20Handling)

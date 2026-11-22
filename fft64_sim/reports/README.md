# FPGA report index / FPGA 报告索引

This index separates archived runs and implementation stages. All listed reports use Vivado 2018.3. Values below were checked against report text; no simulation, synthesis, routing, or board test was rerun for this documentation correction.

本索引区分归档构建与实现阶段。以下数字已与报告文本核对，本次修正文档未重跑仿真、综合、布局布线或上板测试。

## January 9, 2026 — 7vx690tffg1761-2

| Evidence / 证据 | Source / 来源 | Interpretation / 含义 |
| --- | --- | --- |
| Flash synthesis | [utilization_report_flash_virtex.txt](../vivado_project/FFT64_SIM/utilization_report_flash_virtex.txt) | 12,289 LUTs; 15,496 registers; 768 DSPs; 4,100 IOBs. Design State: Synthesized. |
| SDF synthesis | [utilization_report_sdf_virtex.txt](../vivado_project/FFT64_SIM/utilization_report_sdf_virtex.txt) | 2,158 LUTs; 4,830 registers; 24 DSPs; 68 IOBs. Design State: Synthesized. |
| SDF placed utilization | [fft64_dit_sdf_utilization_placed.rpt](../vivado_project/FFT64_SIM/FFT64_SIM.runs/impl_1/fft64_dit_sdf_utilization_placed.rpt) | 2,283 LUTs; 4,830 registers; 24 DSPs; 68 IOBs. Do not substitute the synthesis LUT count for this stage. |
| SDF routed timing | [fft64_dit_sdf_timing_summary_routed.rpt](../vivado_project/FFT64_SIM/FFT64_SIM.runs/impl_1/fft64_dit_sdf_timing_summary_routed.rpt) | 10 ns clock; WNS +1.631 ns; WHS +0.084 ns; zero setup/hold failing endpoints. |
| Clock constraint | [timing.xdc](../vivado_project/FFT64_SIM/FFT64_SIM.srcs/constrs_1/new/timing.xdc) | Creates a 10 ns clock only. External input/output delays are absent. |
| Routed design-rule checks | [fft64_dit_sdf_drc_routed.rpt](../vivado_project/FFT64_SIM/FFT64_SIM.runs/impl_1/fft64_dit_sdf_drc_routed.rpt) | Includes missing I/O standards and pin assignments. Board-specific constraints still need completion. |
| Routed power estimate | [fft64_dit_sdf_power_routed.rpt](../vivado_project/FFT64_SIM/FFT64_SIM.runs/impl_1/fft64_dit_sdf_power_routed.rpt) | 0.437 W tool estimate, Low confidence. Not measured board power. |

The 82.4% LUT, 68.8% register, 96.9% DSP and 98.3% IOB reductions compare the two synthesis reports only. The flash interface exceeds the target's 850 available IOBs, so the table does not compare two routed implementations. The placed SDF LUT count is 2,283, not 2,158. Positive internal timing slack does not establish board operation, complete I/O timing closure, or measured maximum frequency.

82.4% LUT、68.8% 寄存器、96.9% DSP、98.3% IOB 降幅仅比较两份综合报告。Flash 接口超过器件的 850 个可用 IOB，不能将表格解释为两种布线完成的实现对比。SDF 布局后的 LUT 数为 2,283，综合后为 2,158。内部时序正裕量不等于上板运行、完整 I/O 时序收敛或实测最高频率。

## January 8, 2026 — historical 7vx485tffg1157-1 run

These files remain in place as historical records. They do not support the January 9 result on the other target device.

以下文件原位保留为历史记录，不能用于证明另一器件上 1 月 9 日的结果。

| Source / 来源 | Limitation / 限制 |
| --- | --- |
| [impl_1_util.rpt](impl_1_util.rpt) | 2,157 LUTs, 4,830 registers, 24 DSPs, 68 IOBs on 7vx485tffg1157-1; not the source of the 2,158-LUT comparison. / 不用于支持 2,158 LUT 对比。 |
| [impl_1_timing.rpt](impl_1_timing.rpt) | Explicitly states no user-specified timing constraints; WNS/WHS are NA. No 100 MHz timing conclusion can be drawn. / 无用户时序约束，不能得出 100 MHz 时序结论。 |
| [impl_1_power.rpt](impl_1_power.rpt) | Reports 103.384 W, Low confidence and junction temperature exceeded. Historical diagnostic estimate, not a usable power result or hardware measurement. / 含结温超限警告的历史诊断估算，不作为有效功耗结果。 |

## Technical report versions / 技术报告版本

Use the corrected [English Markdown report](../report_en.md) or [Chinese Markdown report](../report.md) with this index. The existing [PDF](../report.pdf) is a historical export and has not been regenerated; its wording should be read with these corrections. Original tool reports are unchanged.

阅读修订后的中英文 Markdown 报告时请同时参考本索引。现有 PDF 为未重新导出的历史版本，其表述以本次更正为准。原始工具报告保持原样。

# Bluetooth Vulnerability Analysis

I analyzed the BleedingTooth vulnerabilities in the Linux Bluetooth stack for a 2023 Safe Programming assignment. My report explains BadVibes, BadChoice, and BadKarma, traces the relevant kernel code, and examines the published exploitation chain.

> [!CAUTION]
> The reference program is a historical exploit for vulnerable Linux systems. Any execution belongs in a disposable, explicitly authorized lab with suitable hardware.

## Tech stack

- C, Linux kernel internals, BlueZ, Bluetooth HCI, L2CAP, and A2MP
- Heap memory corruption, information disclosure, type confusion, and kernel object layouts
- Hebrew technical report with annotated source-code excerpts

## Included materials

- `results/report.pdf`: my 11-page coursework report, with the student identifier removed.
- `reference/bleedingtooth/exploit.c`: Andy Nguyen's original proof of concept from Google's Security Research repository.
- `reference/bleedingtooth/LICENSE`: the upstream Apache 2.0 license for the reference source.

## Analysis scope

The report covers:

- **BadVibes (CVE-2020-24490):** handling of advertising reports and the resulting heap-memory corruption.
- **BadChoice (CVE-2020-12352):** uninitialized stack data exposed through an A2MP response.
- **BadKarma (CVE-2020-12351):** type confusion involving Bluetooth socket and channel objects.
- The relationships among memory disclosure, object layout, and control-flow manipulation in the published exploit.

My contribution is the written analysis. Andy Nguyen developed the included reference implementation. The report records a source-level study of the published work; it does not establish an independent successful execution of the exploit.

## Read the project

Start with [the report](results/report.pdf). The report is in Hebrew and discusses code excerpts from the Linux Bluetooth stack alongside the supplied reference program.

The historical upstream environment was x86-64 Ubuntu 20.04.1 with Linux `5.4.0-48-generic`. Building the reference source requires a compatible Linux C compiler and the BlueZ development library. Runtime behavior depends on that historical environment, its Bluetooth hardware, and kernel-specific addresses.

## Reference source

- [Google Security Research: BleedingTooth](https://github.com/google/security-research/tree/master/pocs/linux/bleedingtooth)
- [Upstream exploit source](https://github.com/google/security-research/blob/master/pocs/linux/bleedingtooth/exploit.c)
- [Upstream technical write-up](https://github.com/google/security-research/blob/master/pocs/linux/bleedingtooth/writeup.md)

The reference source is distributed under the [Apache License 2.0](reference/bleedingtooth/LICENSE).

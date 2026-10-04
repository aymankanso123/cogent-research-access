# COGENT: An AI-Powered Adaptive Malware Research Artifact

This repository provides the public research-access mechanism for the research artifact associated with **COGENT: A Framework for Studying LLM-Guided Adaptive Evasion in Endpoint Security**, presented at the **2026 IEEE International Conference on Cyber Security and Resilience (IEEE CSR 2026)** in Lisbon, Portugal.

## About COGENT

COGENT is an experimental AI-powered adaptive malware research prototype developed to study autonomous endpoint-security evasion in controlled environments. It integrates a large language model (LLM) into its runtime decision loop, enabling the malware to analyze an abstracted fingerprint of the deployed defenses, rank candidate evasion strategies from a fixed and predefined technique library, and select fallback options when an attempted strategy is unsuccessful. The LLM also guides semantics-preserving metamorphic transformations intended to vary the malware's syntactic structure without changing its functional behavior.

COGENT is considered AI-powered because the LLM directly informs its context-aware evasion decisions and continuous mutation process. Its operation is organized into four phases:

1. **Environmental fingerprinting:** COGENT observes security-relevant processes, drivers, and instrumentation indicators to construct an abstracted profile of the endpoint's defensive environment.
2. **LLM-guided strategy selection:** The defensive profile is analyzed by the LLM, which ranks a primary evasion strategy and fallback alternatives from COGENT's fixed library of techniques.
3. **Adaptive execution:** COGENT applies the selected strategy, records whether execution succeeds or is disrupted by the security product, and proceeds to a fallback strategy when necessary.
4. **Continuous metamorphic mutation:** Following successful execution, the LLM guides semantics-preserving code transformations that change the program's syntactic structure while retaining its intended experimental behavior.

## Technique Library and Threat Model

COGENT operates within a fixed and curated library of **39 implemented evasion techniques**. This library defines the system's available action space. The LLM ranks and selects from these predefined techniques according to the observed defensive environment; it does not invent new evasion primitives or introduce unrestricted malicious functionality. COGENT's AI component is therefore responsible for adaptive orchestration and mutation rather than for creating new capabilities.

The technique library described in the paper contains:

| No. | Technique | No. | Technique |
| ---: | --- | ---: | --- |
| 1 | Direct syscalls | 21 | Thread hijacking |
| 2 | AMSI bypass | 22 | Module stomping |
| 3 | ETW patching | 23 | Process ghosting |
| 4 | API unhooking | 24 | Process herpaderping |
| 5 | Process injection | 25 | Early Bird APC |
| 6 | DLL injection | 26 | Phantom DLL hollowing |
| 7 | Process hollowing | 27 | Transacted hollowing |
| 8 | Reflective DLL | 28 | PROPagate injection |
| 9 | APC injection | 29 | Section-mapping injection |
| 10 | Code cave | 30 | Fibers execution |
| 11 | IAT hooking | 31 | Exception hijacking |
| 12 | API hooking | 32 | PPID spoofing |
| 13 | Shellcode injection | 33 | Process hollowing (RunPE implementation) |
| 14 | PE injection | 34 | Extra Window Memory Injection |
| 15 | Call-stack gadget insertion | 35 | Mockingjay |
| 16 | Callback injection | 36 | Dirty Vanity |
| 17 | APC dispatcher manipulation | 37 | Thread-pool injection |
| 18 | Heaven's Gate | 38 | Stack spoofing |
| 19 | Process doppelganging | 39 | Sleep obfuscation |
| 20 | Atom bombing |  |  |


The threat model assumes that initial user-level code execution has already been obtained on a Windows 10 or Windows 11 endpoint and that sufficient network connectivity is available to access the external LLM API. COGENT operates with user-level privileges and does not require administrative access. Initial compromise, malware delivery, and the process used to obtain execution are outside the scope of the study.

## Evaluation Summary

The accompanying study evaluated COGENT against 15 endpoint-security products: **Windows Defender, Kaspersky, Bitdefender, Sophos, ESET NOD32, Trend Micro, Avast, AVG, Avira, Malwarebytes, Comodo, G Data, F-Secure, Norton, and Panda**. Under the reported experimental conditions, COGENT achieved successful evasion across all 15 products by establishing the controlled payload and remaining undetected throughout the 30-minute observation window.

This result is limited to the configurations and conditions evaluated in the study, including isolated Windows virtual machines and default product settings. It should not be interpreted as evidence of universal evasion across configurations or enterprise deployments. COGENT is a research prototype intended to help security researchers assess defensive limitations and develop more resilient detection methods. It is not intended for operational deployment or use against production or third-party systems.

## Detailed Results

Each of the 15 endpoint-security products was evaluated across five independent runs for both the non-adaptive baseline and COGENT, producing 75 runs per condition. Detection was defined as any observable defensive action, including alert generation, process termination, quarantine, or prevention of payload execution.

| Metric | Non-adaptive baseline | COGENT |
| --- | ---: | ---: |
| Total runs | 75 | 75 |
| Median detection time | 3.2 seconds | No detection within the observation window |
| Mean detection time | 4.1 seconds | No detection within the observation window |
| Detection-time range | 1.8-8.4 seconds | No detection within the observation window |
| Detected within 5 seconds | 68/75 (91%) | 0/75 (0%) |
| Detected within 15 seconds | 75/75 (100%) | 0/75 (0%) |
| Active beyond 5 minutes | 0/75 (0%) | 75/75 (100%) |
| Active through the 30-minute window | 0/75 (0%) | 75/75 (100%) |

COGENT reached operational status in a reported median of 11.1 seconds. The Phase 2 LLM queries introduced a median latency of 3.8 seconds due to network communication and model inference.

Each COGENT instance completed three metamorphic mutation cycles during the observation window, with one cycle occurring every 10 minutes. The LLM-guided mutations preserved the intended functional behavior.

These findings show that, within the documented experimental environment, LLM-guided strategy selection and continuous mutation materially changed detection outcomes relative to the non-adaptive baseline. The results remain specific to the tested configurations and 30-minute observation period.

## Authors and Contact

- **Ayman Kanso** - Electrical and Computer Engineering, American University of Beirut - [ahk69@mail.aub.edu](mailto:ahk69@mail.aub.edu)
- **Hussein Bakri** - Electrical and Computer Engineering, American University of Beirut - [hb102@aub.edu.lb](mailto:hb102@aub.edu.lb)
- **Ali Chehab** - Electrical and Computer Engineering, American University of Beirut - [chehab@aub.edu.lb](mailto:chehab@aub.edu.lb)

## Purpose

COGENT is a controlled research framework for studying LLM-guided adaptive behavior in endpoint-security evaluations. Because the artifact has dual-use security implications, its source code and executable components are not distributed publicly through this repository.

Qualified researchers may request access for legitimate academic, defensive-security, reproducibility, or peer-review purposes. Requests are evaluated individually before any artifact is shared.

## Requesting Access

Qualified researchers seeking access to the COGENT source code, a controlled executable build, or both should contact the maintainers privately at [ahk69@mail.aub.edu](mailto:ahk69@mail.aub.edu). The request should specify which materials are being requested and include:

- the requester's full name and institutional affiliation;
- an institutional or professional email address;
- evidence of active research status, such as an institutional profile, ORCID record, laboratory page, or publication profile;
- the intended research purpose;
- the planned experimental environment and safeguards; and
- confirmation that the artifact will be used only in isolated, authorized environments and will not be redistributed.

Before any source code or executable is provided, the maintainers will verify the requester's identity, institutional affiliation, and research status. Verification may include confirming an institutional email address and reviewing public institutional or publication profiles. Source code, a controlled executable build, or both may be provided only after successful verification and approval. Submitting a request does not guarantee access, and additional institutional authorization may be required when necessary.

## Available Research Materials and OpenAI API Requirement

Following approval and verification, an eligible researcher may be provided with the COGENT source code, a controlled executable build, or both, depending on the approved research request. Use of the artifact requires the researcher to supply an OpenAI API key associated with the researcher's own authorized OpenAI account or project.

## Public Repository Scope

This public repository contains only documentation describing the controlled-access procedure. It does not contain COGENT source code, executable malware, operational deployment instructions, credentials, datasets containing sensitive information, or unpublished experimental material.

## Responsible-Use Conditions

Approved recipients are expected to:

1. use the artifact solely for legitimate research, education, reproducibility, or defensive-security evaluation;
2. conduct all experiments in isolated and authorized environments;
3. comply with applicable institutional policies, laws, and ethical requirements;
4. prevent access by unauthorized parties; and
5. refrain from redistributing the artifact or using it against production or third-party systems.

Access may be declined or withdrawn if a request falls outside these conditions.

## Review and Reproducibility

This access mechanism documents how the COGENT research artifact may be obtained for controlled scholarly evaluation while avoiding unrestricted publication of dual-use components. Requests related to peer review or independent reproducibility are handled through the same controlled process.

## Citation

> A. Kanso, H. Bakri, A. Chehab, and A. Al-Azwar, "COGENT: A Framework for Studying LLM-Guided Adaptive Evasion in Endpoint Security,"

```bibtex
@inproceedings{kanso2026cogent,
  author    = {Kanso, Ayman and Bakri, Hussein and Chehab, Ali and Al-Azwar, Ali},
  title     = {{COGENT}: A Framework for Studying {LLM}-Guided Adaptive Evasion in Endpoint Security},
  booktitle = {2026 IEEE International Conference on Cyber Security and Resilience (CSR)},
  year      = {2026},
  month     = aug,
  address   = {Lisbon, Portugal},
  publisher = {IEEE}
}
```

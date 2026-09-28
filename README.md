# COGENT: An AI-Powered Adaptive Malware Research Artifact

This repository provides the public research-access mechanism for the research artifact associated with **COGENT: A Framework for Studying LLM-Guided Adaptive Evasion in Endpoint Security**, presented at the **2026 IEEE International Conference on Cyber Security and Resilience (IEEE CSR 2026)** in Lisbon, Portugal.

## About COGENT

COGENT is an experimental AI-powered adaptive malware research prototype developed to study autonomous endpoint-security evasion in controlled environments. It integrates a large language model (LLM) into its runtime decision loop, enabling the malware to analyze an abstracted fingerprint of the deployed defenses, rank candidate evasion strategies from a fixed and predefined technique library, and select fallback options when an attempted strategy is unsuccessful. The LLM also guides semantics-preserving metamorphic transformations intended to vary the malware's syntactic structure without changing its functional behavior.

COGENT is considered AI-powered because the LLM directly informs its context-aware evasion decisions and continuous mutation process. The system combines four stages: environmental fingerprinting, LLM-guided strategy selection, monitored execution with fallback selection, and continuous metamorphic mutation. This closed-loop design enables the malware to adapt its behavior to observed defensive characteristics during an authorized experiment, while restricting its available actions to the predefined technique library.

The accompanying study evaluates COGENT against 15 endpoint-security products in isolated Windows virtual machines. COGENT is a research prototype intended to help security researchers assess defensive limitations and develop more resilient detection methods. It is not intended for operational deployment or use against production or third-party systems.

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

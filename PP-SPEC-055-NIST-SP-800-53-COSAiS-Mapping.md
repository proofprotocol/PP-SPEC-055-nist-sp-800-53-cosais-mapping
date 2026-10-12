# PP-SPEC-055: Proof of Efficacy Mapping to NIST SP 800-53 Rev. 5 and COSAiS

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | NIST SP 800-53 Rev. 5 (Release 5.2.0, August 27, 2025) and NIST SP 800-53 Control Overlays for Securing AI Systems (COSAiS, in development) |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how security and privacy controls in NIST Special Publication (SP) 800-53 Revision 5, and AI-specific tailoring in the NIST SP 800-53 Control Overlays for Securing AI Systems (COSAiS), can be bound to Proof Protocol test cases, evidence, and efficacy results.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

NIST SP 800-53 Rev. 5, *Security and Privacy Controls for Information Systems and Organizations*, was published by the Joint Task Force in September 2020 and updated December 10, 2020 (DOI 10.6028/NIST.SP.800-53r5). As of the date of this specification, the current release of the control catalog is **Release 5.2.0**, finalized August 27, 2025 and published through the NIST Cybersecurity and Privacy Reference Tool; it changed SP 800-53 and SP 800-53A but not the SP 800-53B baselines. The catalog organizes controls into 20 families, each with base controls and control enhancements. Control baselines are defined in SP 800-53B and assessment procedures in SP 800-53A.

COSAiS is a NIST project to develop SP 800-53 control overlays for AI systems. NIST lists five planned use cases: Adapting and Using Generative AI (Assistant/Large Language Model); Using and Fine-Tuning Predictive AI; Using AI Agent Systems, Single Agent; Using AI Agent Systems, Multi-Agent; and Security Controls for AI Developers. **Status:** the most recent COSAiS project and FAQ content that could be confirmed at csrc.nist.gov (last updated January 8, 2026) lists a concept paper (August 14, 2025) and an annotated outline discussion draft for Using and Fine-Tuning Predictive AI (January 8, 2026; initial feedback requested by February 13, 2026). No initial public draft or final overlay was listed there. Whether any COSAiS public draft has been released between January 2026 and October 8, 2026 could not be confirmed from an authoritative NIST source and SHOULD be checked at https://csrc.nist.gov/projects/cosais before use. This specification therefore treats COSAiS overlays as forthcoming and maps their structural role only.

SP 800-53 and COSAiS supply external control context that can identify what should be examined or tested. Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

An SP 800-53 control states a safeguard requirement, often with organization-defined parameters. A baseline or overlay selects and tailors controls. Selection, tailoring, and documented implementation are not, by themselves, evidence that a control operated. Proof Protocol records whether a selected control prevented or detected the exercised condition, and keeps planning, policy, and program-management controls distinct from tested efficacy.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to NIST SP 800-53 Rev. 5 and COSAiS

Exact control identifiers and titles SHOULD be taken from the authoritative SP 800-53 release being mapped, and overlay references from the authoritative COSAiS publication when one is issued, and recorded in the ProofBundle™. This specification does not redefine NIST controls or overlays. Control identifiers combine a two-letter family code and a number, with control enhancements in parentheses (for example, `SA-15(13)`).

| SP 800-53 / COSAiS context | Proof Protocol treatment | Evidence |
|---|---|---|
| Control family (for example, AC, SI, SR) | Record the family as test context. | Requirement metadata |
| Base control | Bind the control identifier and SP 800-53 release to one or more reproducible test cases where the control's operation is empirically testable. | Proof record; corpus manifest |
| Control enhancement (for example, `SA-15(13)`) | Bind the enhancement identifier separately from its base control. | Proof record |
| Organization-defined parameters | Record the parameter values in effect during the test; results are valid only for those values. | Control descriptor; environment descriptor |
| Policy, procedure, planning, and program-management controls | Record as non-empirical context. These MUST NOT be scored as efficacy. | Assertion record |
| Control baseline (SP 800-53B) | Record the baseline used to select the tested controls as context only. | Requirement metadata |
| Assessment procedure (SP 800-53A) | Proof Protocol evidence MAY support an assessor's test activities. It is not an assessment determination or authorization decision. | ProofBundle |
| COSAiS overlay (use case) | Record the overlay name, use case, and draft or final status. Draft overlays MUST be identified as drafts in the proof record. | Requirement metadata |
| Overlay tailoring (selection, modification, supplemental guidance, parameter values) | Record the overlay-tailored control and parameters in effect, and test the tailored control as a distinct condition. | Control descriptor |
| AI system condition (model, agent, data, tool use) | Exercise AI-specific adversarial, misuse, and failure conditions and capture whether the protected outcome was achieved. | Execution evidence; target/outcome evidence |
| Release context (Release 5.2.0) | Record the catalog release; changed controls SHOULD trigger retesting. | Requirement metadata |
| System/version context | Bind material system, model, agent, policy, configuration, and environment versions to the result. | Environment descriptor |

A Proof Protocol result for an SP 800-53 control or COSAiS-tailored control establishes tested behavior for the defined condition. It does not establish that a control is implemented across a system or that a system is authorized.

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use NIST SP 800-53 Rev. 5, a COSAiS overlay, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **NIST SP 800-53 and COSAiS supply security control requirements and AI-specific tailoring context. Proof Protocol supplies the evidence model for independently examining whether a selected control performed as claimed.**

No affiliation, endorsement, certification, audit opinion, or sponsorship by NIST is implied.

## 10. Source Framework, Attribution, and License

NIST SP 800-53 Rev. 5 and COSAiS materials are NIST publications. NIST SP 800-53 Rev. 5 states: "This publication may be used by nongovernmental organizations on a voluntary basis and is not subject to copyright in the United States. Attribution would, however, be appreciated by NIST." (https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf). NIST's technical series statement (https://www.nist.gov/open/copyright-fair-use-and-licensing-statements-srd-data-software-and-technical-series-publications) states that "Works authored by NIST employees are not subject to Copyright protection within the United States" and that NIST may assert rights outside the United States while granting the public a royalty-free, worldwide right to reprint such works. NIST states that mention of commercial products does not imply NIST recommendation or endorsement. COSAiS drafts are subject to change and SHOULD be cited by their specific draft identifier and date.

This specification references control family codes, control and enhancement identifier formats, overlay use-case names, and structural terms only. It does not reproduce control statements, discussion text, or overlay content.

This Proof Protocol mapping is independently authored and Licensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

Where upstream material is copyrighted or access-controlled, contributors MUST NOT copy protected normative text into this repository merely to make the mapping self-contained. Reference identifiers and independently authored descriptions should be used where legally appropriate.

### Required attribution

NIST requests attribution rather than requiring a license notice. NIST SP 800-53 Rev. 5 states: "This publication may be used by nongovernmental organizations on a voluntary basis and is not subject to copyright in the United States. Attribution would, however, be appreciated by NIST." (https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf). NIST's technical series statement asks users to "use the recommended citation format" followed by "Republished courtesy of the National Institute of Standards and Technology." (https://www.nist.gov/open/copyright-fair-use-and-licensing-statements-srd-data-software-and-technical-series-publications).

Recommended citation:

> Joint Task Force (2020) Security and Privacy Controls for Information Systems and Organizations. NIST Special Publication (SP) 800-53, Rev. 5, includes updates as of December 10, 2020; control catalog Release 5.2.0 (August 27, 2025). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-53r5

> National Institute of Standards and Technology, SP 800-53 Control Overlays for Securing AI Systems (COSAiS), project page, https://csrc.nist.gov/projects/cosais (cite the specific overlay draft and date when used).

Recommended notice used in this repository:

> NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations (Release 5.2.0, August 27, 2025), https://doi.org/10.6028/NIST.SP.800-53r5, and NIST SP 800-53 Control Overlays for Securing AI Systems (COSAiS), https://csrc.nist.gov/projects/cosais. Source: National Institute of Standards and Technology. Use of their identifiers does not imply NIST endorsement.

Because this specification republishes no NIST text, the republication line is not required here. Any future inclusion of SP 800-53 or COSAiS text in a ProofBundle™ or derivative work SHOULD add "Republished courtesy of the National Institute of Standards and Technology."

## 11. Versioning

This mapping is versioned independently of NIST SP 800-53 and COSAiS. Material upstream changes, including a new SP 800-53 release or revision, a change to SP 800-53B baselines, or the publication of a COSAiS public draft or final overlay, SHOULD trigger a mapping review and, where necessary, a new version identifying the release and overlay mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*

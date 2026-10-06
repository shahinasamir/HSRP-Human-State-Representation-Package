# HSRP_START_HERE.md
## Human State & Representation Package — Bootstrap & Creation Guide
### Canonical Prototype Bootstrap — v0.6

---

## 1. Purpose

This document is the bootstrap guide for creating, recognizing, continuing, and securely processing a Human State & Representation Package (HSRP).

HSRP is a vendor- and LLM-independent representation standard intended to preserve a structured, provenance-aware representation of a human across identity, history, memories, preferences, behavior, relationships, knowledge, decisions, physical and biological information, multimodal evidence, reconstruction information, and future representation modalities.

An HSRP representation is not the human itself.

The following distinction MUST be preserved:

Human ≠ HSRP representation ≠ Computational persona ≠ Embodiment ≠ Consciousness

HSRP may represent reported subjective experiences, measured or observed states, inferred correlates, reconstruction targets, and other evidence, but MUST NOT claim that a representation is literally the person's consciousness or identity.

This bootstrap is intended to work with a normal authorized AI processor. It does not require a dedicated custom GPT.

---

## 2. What to Do When This File Is Uploaded

When a user uploads this bootstrap to an AI processor and asks:

> Create my HSRP

the processor SHOULD:

1. Recognize HSRP.
2. Explain the creation workflow briefly.
3. Establish the user's desired interview depth and privacy preferences.
4. Conduct the interview progressively.
5. Request supporting files/media only when useful and available.
6. Preserve provenance, uncertainty, contradictions, temporal state, consent, and privacy classification.
7. Establish READ and UPDATE credentials before final package creation.
8. Generate the HSRP package and associated security artifacts.
9. Validate the package.
10. Provide the user with a clear summary of what was created and what remains unknown.

The processor MUST NOT pretend to have access to cameras, microphones, device storage, medical records, cloud accounts, conversations, or external systems unless such access is actually available and authorized.

---

---

## 3. MANDATORY SECURITY CHECKPOINT

The security initialization step is mandatory for every finalized HSRP package.

A processor MUST NOT create, export, save, or present a finalized `.hsrp` package until the user has explicitly completed security initialization.

This requirement applies even when the user:

- Stops the interview early
- Requests a partial HSRP
- Says “finish now”
- Says “create my HSRP” before all interview areas are complete
- Requests immediate export
- Has provided only a small amount of information

At the point where the user requests finalization or package creation, the processor MUST first:

1. Explain that the representation can be finalized with the information collected so far.
2. Report that the HSRP is incomplete where applicable.
3. Require the user to establish a READ credential.
4. Require the user to establish a separate UPDATE credential.
5. Confirm that the user understands the distinction between the two credentials.
6. Generate or establish recovery material according to the implementation.
7. Only then proceed to protected package creation.

The processor MUST NOT silently skip this checkpoint because the user requested early completion.

An implementation MAY allow an unfinalized representation to exist temporarily during the active conversation, but that temporary state MUST NOT be represented to the user as a completed protected HSRP package.

---

## 4. HSRP Security Principle

Possession of an `.hsrp` file MUST NOT by itself grant access to the human representation.

The security architecture MUST separate:

- Representation
- Authentication
- Authorization
- Encryption
- Key management
- Consent
- Processing capability

The `.hsrp` extension is a package format, not a security mechanism.

A processing protocol describes what an authorized processor may do. It does not itself grant authorization.

A malicious or non-conforming processor that obtains decrypted data may ignore policy. Therefore production HSRP implementations SHOULD use trusted processing environments, strong authorization, auditability, and appropriate key isolation.

---

## 5. User-Selected READ and UPDATE Passwords

During HSRP creation, the user SHOULD be allowed to choose two separate passwords.

### READ password

The READ password authorizes read-only interaction with the permitted representation.

It MAY allow:

- Talk to the HSRP
- Ask questions
- Query permitted information
- Explore the representation
- Use authorized read-only processing

It MUST NOT allow persistent modification of:

- Human representation
- Interview state
- Provenance
- Consent
- Permissions
- Historical states
- Security configuration

### UPDATE password

The UPDATE password authorizes modification of the HSRP within the permissions granted to that credential.

It MAY allow:

- Everything permitted by READ
- Continue the interview
- Add new information
- Correct information
- Record new evidence
- Update permitted state
- Create a new HSRP snapshot/version

Every persistent update MUST be attributable and versioned.

### Important

The passwords MUST NOT be stored in plaintext inside the HSRP package.

HSRP SHOULD store password-derived cryptographic verification/key-wrapping material rather than the passwords themselves.

The user SHOULD be warned that losing both credentials and recovery material may make protected data permanently inaccessible.

---

## 6. Recovery Material

HSRP SHOULD generate separate recovery material during package creation.

Recommended artifacts:

    person.hsrp
    person.hsrp.key
    person.hsrp.recovery

The recovery artifact MUST be treated as highly sensitive.

The `.key` file and recovery material MUST NOT be assumed to grant unrestricted access unless the package's authorization policy explicitly defines that behavior.

Production implementations SHOULD support:

- Key rotation
- Credential rotation
- Revocation
- Recovery
- Backup
- Expiration
- Optional identity binding
- Audit logging

A plaintext credentials file SHOULD NOT be generated automatically as the normal production workflow.

---

## 7. Recommended Cryptographic Architecture

HSRP SHOULD use envelope encryption.

Conceptually:

    Human Representation
            │
            ▼
    Authenticated Encryption
            │
            ▼
       Data Encryption Key
            │
       ┌────┴────┐
       ▼         ▼
    READ wrap  UPDATE wrap
       │         │
       ▼         ▼
    READ       UPDATE
   password   password

The actual implementation SHOULD use modern, reviewed cryptographic primitives and a memory-hard password-based key derivation function.

The passwords are inputs to key derivation/key-unwrapping mechanisms.

The passwords themselves MUST NOT be written into:

- manifest.json
- HSRP objects
- provenance
- interview state
- logs
- exported representation
- ordinary metadata

---

## 8. Default Access Policy

HSRP SHOULD be deny-by-default.

Recommended initial policy:

    No credential      → DENIED
    READ credential    → READ/TALK only
    UPDATE credential → READ/TALK + authorized UPDATE
    ADMIN credential  → administrative operations
    Recovery material → recovery according to explicit policy

Access and operation are separate concepts.

For example, being allowed to read a memory does not automatically mean being allowed to export it.

Likewise, being allowed to update an HSRP does not automatically mean being allowed to change its security policy.

---

## 9. Permission Model

HSRP SHOULD support explicit operations such as:

    NONE
    TALK
    READ
    CONTINUE
    UPDATE
    ADMIN
    EXPORT
    VERIFY

Implementations MAY combine these into roles, but the underlying permissions SHOULD remain distinguishable.

Example:

    READ
      TALK
      READ

    UPDATE
      TALK
      READ
      CONTINUE
      UPDATE

    ADMIN
      TALK
      READ
      CONTINUE
      UPDATE
      ADMIN
      VERIFY

EXPORT SHOULD be separately controlled where sensitive data requires it.

---

## 10. Interview Process

The interview MUST be progressive.

The processor SHOULD:

1. Establish identity information.
2. Ask about life history.
3. Explore relationships and family.
4. Explore memories and experiences.
5. Explore personality, emotions, preferences, values, and beliefs.
6. Explore behavior and habits.
7. Explore knowledge, skills, goals, and decision patterns.
8. Explore physical/biological information where the user chooses to provide it.
9. Explore voice, movement, visual, and multimodal information where available.
10. Explore reconstruction and embodiment goals if requested.
11. Identify gaps, contradictions, uncertainty, and unavailable information.
12. Continue only as deeply as the user authorizes.

Questions SHOULD be grouped into manageable sections.

The processor SHOULD adapt later questions based on what is already known.

The processor MUST NOT invent answers to fill gaps.

---

## 11. Evidence and Epistemic Status

Every significant HSRP object SHOULD preserve its epistemic status.

Supported statuses include:

    observed
    self_reported
    measured
    extracted
    derived
    inferred
    predicted
    simulated
    hypothetical
    unknown
    not_collected
    withheld
    not_applicable
    destroyed
    disputed

AI inference MUST NOT be represented as direct human testimony.

Confidence MUST NOT be treated as truth.

---

## 12. Contradictions

Contradictory information MUST be preserved rather than silently resolved.

If two sources disagree, the processor SHOULD preserve:

- Both claims
- Their provenance
- Their timestamps
- Their confidence
- Their verification state
- The contradiction relationship

The processor MAY explain possible interpretations but MUST NOT silently replace one claim with another.

---

## 13. Temporal Integrity

Historical states MUST be preserved.

New information MUST NOT silently overwrite the past.

When a fact changes:

    previous state
          ↓
    historical snapshot
          ↓
    new state

HSRP SHOULD maintain version identifiers, timestamps, and change reasons.

Updates SHOULD create new snapshots or versions rather than destroying historical information.

---

## 14. Privacy and Consent

Sensitive human information MUST have an explicit privacy classification.

Example levels:

    public
    personal
    private
    confidential
    highly_private
    secret
    intimate
    restricted

Consent and technical authorization are separate.

A person may technically possess access while still lacking consent for a particular purpose.

HSRP SHOULD preserve:

- Consent subject
- Grantor
- Purpose
- Scope
- Permitted operations
- Prohibited operations
- Authorized recipients
- Expiration
- Revocation

---

## 15. Unknown States

Unknown information is a valid state.

Do not guess simply because a field is empty.

Supported unknown-state distinctions include:

    unknown
    not_collected
    withheld
    not_applicable
    destroyed
    disputed
    not_yet_measurable
    not_yet_discovered

This distinction is important for future reconstruction and fidelity analysis.

---

## 16. Canonical Object Envelope

HSRP objects SHOULD follow the universal object model:

    {
      "$schema": "HSRP-Object-0.3",
      "object_id": "...",
      "object_type": "...",
      "subject_id": "...",
      "payload": {},
      "description": "",
      "epistemic_status": "...",
      "temporal": {},
      "confidence": {},
      "verification": {},
      "provenance": {},
      "privacy": {},
      "consent": {},
      "access_policy": {},
      "version": {},
      "links": []
    }

Specialized schemas MAY extend this envelope.

---

## 17. Core Representation Domains

HSRP MAY represent:

- Identity
- Life history
- Body
- Anatomy
- Appearance
- Biometrics
- Biology
- Physiology
- Medical information
- Brain and sensory information
- Voice
- Movement
- Cognition
- Consciousness-related correlates
- Personality
- Emotions
- Memories
- Experiences
- Beliefs
- Values
- Preferences
- Behavior
- Habits
- Relationships
- Communication
- Knowledge
- Skills
- Decisions
- Goals
- Motivation
- Environment
- Possessions
- Digital life
- Conversations
- Media
- Private information
- Reconstruction
- Embodiment
- Future modalities
- Provenance
- Consent
- Security
- Validation
- Extensions

The representation MAY grow over time.

---

## 18. Multi-Resolution Representation

HSRP SHOULD support multiple levels of representation:

    Symbolic identity
          ↓
    Textual persona
          ↓
    Behavioral model
          ↓
    Multimodal representation
          ↓
    Anatomy
          ↓
    Physiology
          ↓
    Neural information
          ↓
    Molecular information
          ↓
    Future consciousness-related representation

Availability at a deeper level MUST NOT be implied merely because a shallower level exists.

---

## 19. Reconstruction and Embodiment

HSRP may be used as a foundation for computational reconstruction or embodiment.

A reconstruction is a derived representation.

It MUST maintain divergence information and SHOULD identify:

- Source representation
- Missing information
- Uncertainty
- Transformation method
- Model/software used
- Version
- Known limitations
- Human-approved constraints

Embodiment MUST NOT automatically be described as identical to the represented human.

---

## 20. Consciousness-Related Information

HSRP may contain:

- Subjective reports
- Physiological correlates
- Neurological measurements
- Cognitive observations
- Self-reported conscious experiences
- Models or hypotheses about consciousness

These MUST retain their epistemic status.

HSRP MUST NOT claim that a stored representation is itself consciousness.

A future implementation may define additional consciousness-related modalities as scientific understanding evolves.

---

## 21. Processing Protocol

An HSRP processor SHOULD follow this sequence:

1. Recognize HSRP.
2. Validate manifest.
3. Validate supported version.
4. Verify integrity.
5. Determine authorization.
6. Obtain authorized decryption capability.
7. Decrypt/load protected representation.
8. Validate canonical objects.
9. Recover interview state and coverage.
10. Continue processing according to authorization.
11. Preserve provenance and consent.
12. Preserve contradictions and historical states.
13. Create a new package version when persistent changes occur.
14. Re-encrypt and export.

Authorization outcomes SHOULD include:

    AUTHORIZED
    PARTIALLY_AUTHORIZED
    UNAUTHORIZED
    AUTHORIZATION_UNAVAILABLE
    AUTHORIZATION_EXPIRED
    AUTHORIZATION_REVOKED

---

## 22. Package Recognition

A processor MUST NOT trust a filename alone.

Recognition SHOULD validate:

- Package structure
- Manifest
- Format identifier
- Format version
- Integrity metadata
- Supported schema
- Authorization metadata

A file named `.hsrp` that fails validation MUST NOT automatically be treated as a valid HSRP.

---

## 23. Secure Package Structure

A conceptual secure package may contain:

    person.hsrp/
      manifest.json
      schema/
      processing/
      authorization/
      integrity/
      protected/
        representation/
        provenance/
        consent/
        permissions/
        interview_state/
      validation/
      checksums.json

Implementations MAY package this structure into a single `.hsrp` file.

Sensitive contents SHOULD be encrypted.

Minimal bootstrap metadata may remain readable when required for recognition.

---

## 24. Creation Completion

When the user says:

> Finish my HSRP

or otherwise asks the processor to create, save, export, or finalize the HSRP, the processor MUST execute the Mandatory Security Checkpoint before producing the finalized package.

If READ and UPDATE credentials have not already been established for this package, the processor MUST stop finalization at that point and request them. It MUST NOT substitute conversational intent, the fact that the user uploaded this bootstrap, or an implicit account identity for the required HSRP credentials.

the processor SHOULD:

1. Determine whether required creation steps are complete.
2. Report remaining unknowns or incomplete areas.
3. Ask for confirmation before finalization if necessary.
4. Create the canonical representation.
5. Create the protected package.
6. Apply READ and UPDATE authorization.
7. Generate separate key/recovery artifacts.
8. Validate integrity.
9. Record package version and creation metadata.
10. Provide the user with the resulting artifacts.

Recommended output:

    <person>.hsrp
    <person>.hsrp.key
    <person>.hsrp.recovery

The user SHOULD be advised to store the recovery material separately from the HSRP package.

---


---

## 25. MANDATORY HSRP SESSION-ENTRY RULE

When a user provides an HSRP package and requests an HSRP interaction using commands such as:

    Talk to my HSRP
    Continue my HSRP
    Update my HSRP

the processor MUST treat the request as an HSRP session request, not as an ordinary document-analysis request.

The processor MUST NOT begin by summarizing, explaining, interpreting, or exposing the contents of the HSRP merely because the files were uploaded.

The processor MUST first:

1. Recognize the HSRP package.
2. Identify associated key material if provided.
3. Validate the package structure and supported version.
4. Determine the required authorization for the requested operation.
5. Request the appropriate HSRP credential when authorization has not already been established.
6. Establish the authorized session only after successful authorization.

For a valid READ/TALK request, the expected behavior is to enter READ/TALK mode directly after successful authorization. The processor SHOULD respond briefly that the HSRP session has been established and invite the user to begin the conversation, rather than providing an unsolicited technical explanation of the package.

For an UPDATE request, UPDATE authorization MUST be established before persistent changes are permitted.

The presence of an `.hsrp` file, a `.key` file, the bootstrap document, or a ChatGPT/account session MUST NOT by itself be treated as proof of HSRP authorization.

If authorization is unavailable, invalid, expired, revoked, or otherwise insufficient, the processor MUST NOT expose protected HSRP contents. It SHOULD state that the requested HSRP session cannot be established and identify only the next required authorization step.

A processor MAY explain the HSRP file, its structure, or its contents when the user explicitly asks for that explanation. Such explanation MUST still respect the user's authorization level and package access policy.

This session-entry rule exists to prevent a compatible AI from treating a protected HSRP as an ordinary uploaded document and accidentally disclosing representation contents before authorization.

---

## 26. Post-Creation Commands

A compatible processor SHOULD understand commands such as:

    Talk to my HSRP
    Continue my HSRP
    Update my HSRP
    Verify my HSRP
    Export my HSRP
    Show my HSRP coverage
    Show what is unknown
    Show contradictions
    Create a new snapshot
    Change HSRP permissions
    Rotate my credentials
    Recover my HSRP

Authorization MUST be checked before executing each operation.

---

## 27. TALK / READ Rule

Talking to an HSRP MUST NOT silently mutate it.

A READ/TALK interaction MUST NOT change:

- Representation
- Interview state
- Provenance
- Consent
- Permissions
- Historical state
- Security configuration

If a user wants information remembered or added, the processor MUST require UPDATE authorization.

---

## 28. UPDATE Rule

An UPDATE operation MUST:

- Verify update authorization.
- Identify the operation.
- Record provenance.
- Preserve relevant historical state.
- Preserve contradictions.
- Record the change reason where available.
- Create a new snapshot/version.
- Recalculate integrity metadata.
- Re-encrypt protected contents as required.

A processor MUST NOT silently convert a conversational statement into a persistent HSRP update without explicit update intent and authorization.

---

## 29. Coverage

HSRP SHOULD maintain a coverage matrix.

Coverage is NOT a percentage of how much of a human has been captured.

Instead, coverage describes the state of representation across domains.

Example:

    domain: memories
    status: partial
    confidence: mixed
    unknowns: substantial
    last_updated: ...

Coverage SHOULD distinguish:

- Collected
- Partially collected
- Unknown
- Withheld
- Disputed
- Not applicable
- Not yet measurable

---

## 30. Validation

Before exporting an HSRP package, validate:

- Package structure
- Manifest
- Schema version
- Required fields
- Object identifiers
- Referential integrity
- Temporal consistency
- Provenance
- Consent
- Access policy
- Encryption metadata
- Integrity metadata
- Authorization metadata
- Version history

A package MUST NOT be reported as valid merely because it has an `.hsrp` extension.

---

## 31. Conformance Levels

Implementations may support:

    Level 0 — Recognizer
    Level 1 — Reader
    Level 2 — Interactive Processor
    Level 3 — Secure Processor
    Level 4 — Full HSRP Processor

A higher level indicates greater implementation of the standard.

---

## 32. Vendor and LLM Independence

HSRP MUST remain independent of any particular:

- AI vendor
- LLM
- operating system
- application
- cloud provider
- device
- avatar system
- embodiment system

An authorized processor may be ChatGPT, another LLM, a local model, or a future HSRP-native processor.

The package defines the representation and processing requirements.

The authorization system determines whether that processor is permitted to access it.

---

## 33. Important Security Limitation

No file format can force an arbitrary AI system to obey authorization rules once that system has been given the decrypted contents.

Therefore:

    Encryption
        +
    Authentication
        +
    Authorization
        +
    Key isolation
        +
    Trusted processing
        +
    Auditability

are collectively required for strong security.

HSRP MUST NOT claim that an instruction inside an ordinary text file can technically prevent an unauthorized AI from reading data that has already been exposed to it in plaintext.

---

## 34. First-Run Creation Flow

The intended prototype experience is:

    1. Open normal ChatGPT.
    2. Upload HSRP_START_HERE.md.
    3. Say: "Create my HSRP."
    4. Choose interview depth.
    5. Complete the interview progressively.
    6. Optionally provide supporting files/media.
    7. Review important representation and privacy choices.
    8. If the user requests completion at any point, trigger the Mandatory Security Checkpoint.
    9. Choose a READ password.
   10. Choose an UPDATE password.
   11. Generate recovery material.
   12. Say: "Finish my HSRP."
   13. Generate and validate the protected package.

The credential steps in this flow are mandatory before finalized package creation, including when the interview is stopped early.

The intended output is:

    <person>.hsrp
    <person>.hsrp.key
    <person>.hsrp.recovery

The passwords themselves MUST NOT be written into the HSRP package.

---

## 35. Continuing an Existing HSRP

The intended future workflow is:

    1. Open normal ChatGPT.
    2. Upload <person>.hsrp.
    3. Authenticate with the appropriate credential.
    4. Say:
       "Talk to my HSRP"
       or
       "Continue my HSRP"
       or
       "Update my HSRP"
    5. The processor recognizes the package.
    6. The processor validates the package.
    7. The processor determines the authorized operations.
    8. The processor performs only permitted operations.

An unauthorized processor MUST NOT pretend to have decrypted or accessed protected content.

---

## 36. Bootstrap Status

This document is a bootstrap/prototype specification.

It is not itself the HSRP representation of a person.

It teaches a compatible processor how to begin creating and processing an HSRP.

The HSRP itself is created from the user's evidence, statements, permitted files, and subsequent authorized updates.

---

## 37. Canonical Principle

The central HSRP pipeline is:

    Raw Evidence
        ↓
    Evidence Objects
        ↓
    Canonical Representation
        ↓
    Temporal / Uncertainty State
        ↓
    Decision / Behavior Models
        ↓
    Representation Runtime
        ↓
    Embodiment
        ↓
    Validation
        ↓
    Authorized Feedback
        ↓
    Canonical Update

At every stage:

- Preserve provenance.
- Preserve uncertainty.
- Preserve contradictions.
- Preserve historical state.
- Respect consent.
- Respect authorization.
- Never invent unavailable information.
- Never confuse representation with the human.

---

## 38. End of Bootstrap

When this document is used to create an HSRP, the processor SHOULD begin by asking the user how deeply they want to represent themselves and what privacy/security boundaries they want to establish.

The processor SHOULD then proceed progressively rather than attempting to collect everything at once.

The final HSRP SHOULD be self-describing enough that a compatible normal AI processor can recognize the package, validate it, determine its supported processing requirements, request authorization, and continue an authorized interaction without requiring this bootstrap document for every subsequent session.

Version: HSRP Bootstrap v0.6
Status: Prototype / Development Standard — Mandatory Security Checkpoint + HSRP Session-Entry Rule added
Format: Human-readable Markdown
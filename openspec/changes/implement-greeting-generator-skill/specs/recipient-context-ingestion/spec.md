## ADDED Requirements

### Requirement: Recipient input from conversation or file path
The skill SHALL accept recipient context either from direct conversation input or from a user-provided file path.

#### Scenario: Direct conversation recipient input
- **WHEN** the user describes recipients in chat
- **THEN** the skill SHALL parse and normalize each recipient record

#### Scenario: File path recipient input
- **WHEN** the user provides a readable file path
- **THEN** the skill MUST load and parse recipients from the file content

### Requirement: Multi-format recipient file parsing
The skill MUST support parsing structured or textual files including `Markdown`, `JSON`, `YAML`, and `txt` formats when they are valid readable text.

#### Scenario: Structured file with multiple recipients
- **WHEN** a JSON or YAML file contains multiple recipient entries
- **THEN** the skill SHALL create one normalized recipient object per entry

#### Scenario: Text file with partial fields
- **WHEN** a Markdown or txt file includes partial recipient info
- **THEN** the skill SHALL best-effort map known fields and retain unknown text as notes

### Requirement: Missing-field fallback behavior
The skill MUST allow recipient records with missing name or low-detail fields and SHALL fall back to `佚名`-style generic greeting when key identity details are absent.

#### Scenario: Recipient lacks explicit name
- **WHEN** a recipient entry has relation/title but no name
- **THEN** the skill SHALL generate grouped output using a safe placeholder identity

#### Scenario: Recipient entry is nearly empty
- **WHEN** a recipient has no reliable structured fields
- **THEN** the skill SHALL still generate a generic but polite candidate set and mark low personalization context

## ADDED Requirements

### Requirement: Candidate generation per recipient with count guarantee
The skill MUST generate the requested number of greeting candidates for each recipient, where total output count equals `recipient_count x candidates_per_recipient`.

#### Scenario: Multiple recipients and explicit candidate count
- **WHEN** the user provides 3 recipients and requests 4 candidates each
- **THEN** the skill SHALL generate exactly 12 greeting candidates in total

#### Scenario: Candidate count defaulting
- **WHEN** the user provides recipients but no candidate count
- **THEN** the skill SHALL generate exactly 3 candidates per recipient

### Requirement: Intra-recipient candidate diversity
For the same recipient, candidate greetings MUST show meaningful stylistic or content variation to avoid near-duplicate outputs.

#### Scenario: Same-recipient candidate comparison
- **WHEN** the skill generates multiple candidates for one recipient
- **THEN** each candidate SHALL differ in tone, focus, structure, or phrasing beyond trivial word substitution

### Requirement: Structured Markdown grouped output
The skill MUST output Markdown grouped by recipient, with a top context block that includes festival, user identity summary, usage, length, and candidate count.

#### Scenario: Render final grouped markdown
- **WHEN** generation is complete
- **THEN** the output SHALL contain one section per recipient and a bullet list of that recipient's candidates

### Requirement: Optional export flow with default file naming
After rendering results, the skill SHALL ask whether to write output to a file and MUST provide a default filename pattern using skill name and timestamp.

#### Scenario: User accepts default file output
- **WHEN** the user confirms writing and does not provide a custom filename
- **THEN** the skill SHALL write the markdown output to a timestamped default `.md` file

#### Scenario: User declines file output
- **WHEN** the user refuses file writing
- **THEN** the skill SHALL return markdown in chat without filesystem write

## ADDED Requirements

### Requirement: Mandatory festival context collection
The skill MUST collect `festival_name` before entering greeting generation, and SHALL request supplemental festival context when it is missing.

#### Scenario: Festival name is provided in initial user input
- **WHEN** the user message already contains a festival name
- **THEN** the skill SHALL accept it and proceed to the next collection stage

#### Scenario: Festival name is missing
- **WHEN** the user does not provide any festival name
- **THEN** the skill MUST ask for the festival name before continuing

### Requirement: Optional user profile collection with explicit privacy notice
The skill SHALL ask for user self-introduction as optional input, and MUST inform the user that refusing profile details may reduce personalization quality.

#### Scenario: User provides profile details
- **WHEN** the user shares identity, style, or personality information
- **THEN** the skill SHALL store and use these details in greeting generation

#### Scenario: User refuses profile details
- **WHEN** the user declines to provide profile information
- **THEN** the skill MUST continue with default neutral persona assumptions and explain quality trade-off

### Requirement: Usage specification collection with defaults
The skill SHALL collect usage channel, target length, and candidate count per recipient; if candidate count is not provided, it MUST default to `3`.

#### Scenario: Candidate count is omitted
- **WHEN** the user does not specify number of candidates
- **THEN** the skill SHALL set candidate count to `3` for each recipient

#### Scenario: Usage channel is unknown
- **WHEN** the user declines to specify channel or length
- **THEN** the skill SHALL infer a reasonable default and continue

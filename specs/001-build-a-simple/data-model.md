# Data Model: Google Query Wrapper

## Overview
This static application has no persistent data storage. All data is ephemeral and exists only during user interaction.

## User Input Entity

**SearchQuery**
- **Raw Input**: User's original search terms (string, 0-2000 characters)
- **Processed Query**: Input with "-ai" suffix appended (string)
- **Encoded Query**: URL-encoded version for Google redirect (string)

### Validation Rules
- Input length: Maximum 2000 characters (practical URL limit consideration)
- Special character handling: Preserved and properly encoded
- Empty input: Treated as valid, results in "-ai" only query
- Duplicate "-ai": Check for existing suffix to prevent duplication

### State Transitions
1. **Input State**: User types in search field
2. **Processing State**: JavaScript processes and validates input
3. **Redirect State**: Browser navigates to Google with processed query

## No Persistent Storage
- No cookies or localStorage required
- No server-side sessions
- No user accounts or preferences
- Fully stateless operation aligned with static-first principle
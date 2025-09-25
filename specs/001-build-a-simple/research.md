# Research: Google Query Wrapper

## Browser Form Submission Best Practices

**Decision**: Use HTML form with GET method targeting `google.com/search`
**Rationale**: Native browser behavior, SEO-friendly, works without JavaScript as fallback
**Alternatives considered**: POST method (rejected - Google expects GET), pure JavaScript (rejected - accessibility concerns)

## URL Parameter Encoding

**Decision**: Use `encodeURIComponent()` for query parameter encoding
**Rationale**: Handles special characters, spaces, and prevents URL injection
**Alternatives considered**: Manual string replacement (rejected - incomplete), server-side encoding (rejected - static site requirement)

## Google Search URL Structure

**Decision**: `https://www.google.com/search?q={encoded_query}` format
**Rationale**: Standard Google search URL structure, reliable and stable
**Alternatives considered**: Other Google domains (rejected - potential geo-redirects), different parameters (rejected - unnecessary complexity)

## "-ai" Suffix Implementation

**Decision**: Check if query already contains "-ai" before appending
**Rationale**: Prevents duplicate suffixes, maintains user intent
**Alternatives considered**: Always append (rejected - creates duplicates), regex replacement (rejected - over-engineered)

## Fallback Strategy

**Decision**: Form action points directly to Google with JavaScript enhancement
**Rationale**: Progressive enhancement - works with JS disabled
**Alternatives considered**: Pure JavaScript (rejected - accessibility), server redirect (rejected - static requirement)

## Performance Considerations

**Decision**: Inline CSS and JavaScript for single-request load
**Rationale**: Eliminates additional HTTP requests, faster initial load
**Alternatives considered**: External files (rejected - multiple requests), CSS framework (rejected - constitution violation)

## Accessibility Requirements

**Decision**: Semantic HTML form with proper labels and focus management
**Rationale**: Screen reader compatibility, keyboard navigation support
**Alternatives considered**: div-based design (rejected - semantic concerns), complex ARIA (rejected - over-engineering)
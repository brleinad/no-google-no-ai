# Form Interface Contract

## Search Form Interface

### HTML Form Contract
```html
<form id="search-form" action="https://www.google.com/search" method="GET">
  <input type="text" name="q" id="search-input" placeholder="Search Google..." />
  <button type="submit">Search</button>
</form>
```

### JavaScript Enhancement Contract
```javascript
// Function signature
function processAndRedirect(query: string): void

// Input: User's search query string
// Output: Browser redirect to Google with "-ai" suffix
// Side effects: Updates browser location
```

### URL Generation Contract
```javascript
// Input query examples and expected outputs:
"python tutorials" → "https://www.google.com/search?q=python%20tutorials%20-ai"
"" → "https://www.google.com/search?q=-ai"
"machine learning -ai" → "https://www.google.com/search?q=machine%20learning%20-ai"
"cats -ai -dogs" → "https://www.google.com/search?q=cats%20-ai%20-dogs%20-ai"
```

### Error Handling Contract
- Invalid characters: Properly encoded, not rejected
- Extremely long queries: Truncated at browser URL limit
- JavaScript disabled: Form submits to Google without "-ai" suffix
- Network errors: Browser handles naturally (same as direct Google access)

## Performance Contract
- Form submission: Immediate redirect (<100ms processing)
- Page load: Complete in <2 seconds on 3G
- Resource count: Single HTML file (CSS/JS inlined)
- Size limit: Total page size <50KB
# Quickstart Testing Guide

## Manual Testing Scenarios

### Basic Search Functionality
1. **Load the page**
   - Verify: Page loads in under 2 seconds
   - Verify: Search form is visible and accessible
   - Verify: Input field has focus on page load

2. **Simple search test**
   - Action: Enter "python tutorials" and submit
   - Expected: Redirected to Google with query "python tutorials -ai"
   - Verify: No AI overview visible on Google results

3. **Empty search test**
   - Action: Submit form with empty input
   - Expected: Redirected to Google with query "-ai"
   - Verify: Google search results appear

### Edge Case Testing
4. **Existing -ai suffix test**
   - Action: Enter "machine learning -ai" and submit
   - Expected: Redirected with query "machine learning -ai" (no duplication)

5. **Special characters test**
   - Action: Enter "cats & dogs + fish" and submit
   - Expected: Proper URL encoding, successful Google redirect

6. **Long query test**
   - Action: Enter a very long search string (500+ characters)
   - Expected: Still functional, proper encoding

### Accessibility Testing
7. **Keyboard navigation**
   - Action: Tab through page elements
   - Expected: Logical tab order, visible focus indicators

8. **Screen reader simulation**
   - Action: Navigate with keyboard only
   - Expected: Form label properly associated, semantic structure

### Browser Compatibility
9. **JavaScript disabled test**
   - Action: Disable JavaScript, submit search for "test"
   - Expected: Redirected to Google (without -ai suffix)

10. **Multiple browsers**
    - Test in: Chrome, Firefox, Safari
    - Expected: Consistent behavior across all browsers

## Deployment Verification
11. **Netlify deployment test**
    - Action: Deploy to Netlify, test live URL
    - Expected: Same functionality as local testing

12. **Mobile responsiveness**
    - Action: Test on mobile devices
    - Expected: Usable interface, proper touch targets

## Success Criteria
- ✅ All searches redirect to Google successfully
- ✅ "-ai" suffix consistently appended (no duplicates)
- ✅ Page loads under 2 seconds on 3G
- ✅ Works with JavaScript disabled (graceful degradation)
- ✅ Accessible via keyboard and screen readers
- ✅ Mobile-friendly design
- ✅ Single-file deployment ready
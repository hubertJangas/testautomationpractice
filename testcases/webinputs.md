# Test Cases: Web Inputs Page
**Application:** Expand Testing Practice Website  
**Page URL:** https://practice.expandtesting.com/inputs  
**Test Type:** UI and Functional Testing  
**Last Updated:** October 22, 2025

---

## Table of Contents
- [Overview](#overview)
- [Test Scope](#test-scope)
- [Test Environment](#test-environment)
- [Test Cases](#test-cases)
  - [1. Number Input Field Tests](#1-number-input-field-tests)
  - [2. Text Input Field Tests](#2-text-input-field-tests)
  - [3. Password Input Field Tests](#3-password-input-field-tests)
  - [4. Date Input Field Tests](#4-date-input-field-tests)
  - [5. Form Submission Tests](#5-form-submission-tests)
  - [6. Cross-Field Validation Tests](#6-cross-field-validation-tests)
  - [7. UI/UX Tests](#7-uiux-tests)
  - [8. Accessibility Tests](#8-accessibility-tests)
  - [9. Browser Compatibility Tests](#9-browser-compatibility-tests)
  - [10. Performance Tests](#10-performance-tests)

---

## Overview

This document contains comprehensive test cases for the Web Inputs page, which demonstrates various HTML5 input field types including number, text, password, and date inputs. The page is designed to practice automation testing scenarios related to form input handling.

---

## Test Scope

**In Scope:**
- Number input field validation
- Text input field validation
- Password input field validation
- Date input field validation
- Form submission functionality
- Field-level validations
- Browser compatibility
- Accessibility compliance
- Responsive design

**Out of Scope:**
- Backend data persistence
- Database validation
- Network security testing
- Load testing

---

## Test Environment

**Browsers:** Chrome, Firefox, Safari, Edge  
**Devices:** Desktop, Tablet, Mobile  
**Screen Resolutions:** 1920x1080, 1366x768, 768x1024, 375x667  
**Operating Systems:** Windows, macOS, iOS, Android

---

## Test Cases

### 1. Number Input Field Tests

#### TC-NUM-001: Verify Number Input Field Accepts Valid Integer
**Priority:** High  
**Type:** Positive  
**Preconditions:** Navigate to https://practice.expandtesting.com/inputs

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Number input field is visible and enabled |
| 2 | Enter a valid positive integer (e.g., 100) | Value is accepted and displayed in the field |
| 3 | Verify the value in the field | Field displays "100" |

---

#### TC-NUM-002: Verify Number Input Field Accepts Valid Decimal Numbers
**Priority:** High  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Number input field is visible |
| 2 | Enter a valid decimal number (e.g., 123.45) | Value is accepted |
| 3 | Verify the value | Field displays "123.45" correctly |

---

#### TC-NUM-003: Verify Number Input Field Accepts Negative Numbers
**Priority:** Medium  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Number input field is visible |
| 2 | Enter a negative number (e.g., -50) | Value is accepted |
| 3 | Verify the value | Field displays "-50" |

---

#### TC-NUM-004: Verify Number Input Field Rejects Alphabetic Characters
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Number input field is visible |
| 2 | Attempt to enter alphabetic characters (e.g., "abc") | Characters are not accepted OR validation error is shown |
| 3 | Verify field remains empty or shows error | Field is empty or displays validation message |

---

#### TC-NUM-005: Verify Number Input Field Rejects Special Characters
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Number input field is visible |
| 2 | Attempt to enter special characters (e.g., @#$%^&*) | Characters are rejected |
| 3 | Verify field behavior | Field does not accept special characters (except minus and decimal point) |

---

#### TC-NUM-006: Verify Number Input Field Minimum Value Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify the minimum allowed value (if any) | Min value is documented or discoverable |
| 2 | Enter a value below the minimum | Validation error is displayed |
| 3 | Enter the minimum value exactly | Value is accepted without error |

---

#### TC-NUM-007: Verify Number Input Field Maximum Value Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify the maximum allowed value (if any) | Max value is documented or discoverable |
| 2 | Enter a value above the maximum | Validation error is displayed |
| 3 | Enter the maximum value exactly | Value is accepted without error |

---

#### TC-NUM-008: Verify Number Input Field with Zero Value
**Priority:** Medium  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Field is visible |
| 2 | Enter zero (0) | Value is accepted |
| 3 | Verify zero is displayed | Field shows "0" |

---

#### TC-NUM-009: Verify Number Input Field Leading Zeros Handling
**Priority:** Low  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Field is visible |
| 2 | Enter number with leading zeros (e.g., 00123) | Leading zeros are removed and "123" is displayed OR accepted as-is based on design |
| 3 | Verify the value | Field displays value correctly |

---

#### TC-NUM-010: Verify Number Input Field Scientific Notation
**Priority:** Low  
**Type:** Edge Case

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Field is visible |
| 2 | Enter number in scientific notation (e.g., 1e10) | Value is either accepted or rejected based on expected behavior |
| 3 | Verify the behavior | Behavior matches specification |

---

#### TC-NUM-011: Verify Number Input Field Copy-Paste Functionality
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Copy a valid number to clipboard | Number is copied |
| 2 | Paste into the number input field | Number is pasted successfully |
| 3 | Verify pasted value | Value displays correctly |

---

#### TC-NUM-012: Verify Number Input Field Increment/Decrement Arrows (Spinner)
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the number input field | Field displays with up/down arrows |
| 2 | Click the up arrow | Value increments by the step amount |
| 3 | Click the down arrow | Value decrements by the step amount |
| 4 | Verify boundary conditions | Arrows respect min/max values |

---

### 2. Text Input Field Tests

#### TC-TXT-001: Verify Text Input Field Accepts Alphanumeric Characters
**Priority:** High  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Text field is visible and enabled |
| 2 | Enter alphanumeric text (e.g., "Test123") | Text is accepted and displayed |
| 3 | Verify the value | Field displays "Test123" |

---

#### TC-TXT-002: Verify Text Input Field Accepts Special Characters
**Priority:** High  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Text field is visible |
| 2 | Enter special characters (e.g., @#$%^&*()_+-=) | Characters are accepted |
| 3 | Verify the value | Field displays the special characters correctly |

---

#### TC-TXT-003: Verify Text Input Field Accepts Spaces
**Priority:** Medium  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Text field is visible |
| 2 | Enter text with spaces (e.g., "Hello World") | Spaces are accepted |
| 3 | Verify the value | Field displays "Hello World" with proper spacing |

---

#### TC-TXT-004: Verify Text Input Field Accepts Unicode Characters
**Priority:** Medium  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Text field is visible |
| 2 | Enter Unicode characters (e.g., "Привет", "你好", "مرحبا") | Characters are accepted |
| 3 | Verify the value | Field displays Unicode characters correctly |

---

#### TC-TXT-005: Verify Text Input Field Maximum Length Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify the maximum character limit | Max length is documented or discoverable |
| 2 | Enter text exceeding the maximum length | Additional characters are not accepted OR truncated |
| 3 | Verify character count | Field does not exceed max length |

---

#### TC-TXT-006: Verify Text Input Field Minimum Length Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify if there's a minimum character requirement | Min length requirement is documented |
| 2 | Enter text below minimum length | Validation error is displayed (if applicable) |
| 3 | Enter text at minimum length | Value is accepted |

---

#### TC-TXT-007: Verify Text Input Field with Empty Value
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Field is visible |
| 2 | Leave the field empty and attempt to submit/proceed | If required: validation error appears; If optional: proceeds without error |
| 3 | Verify validation behavior | Behavior matches field requirement status |

---

#### TC-TXT-008: Verify Text Input Field Leading/Trailing Spaces Handling
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Field is visible |
| 2 | Enter text with leading spaces (e.g., "   Test") | Spaces are either preserved or trimmed based on design |
| 3 | Enter text with trailing spaces (e.g., "Test   ") | Spaces are either preserved or trimmed based on design |
| 4 | Verify space handling | Behavior is consistent and matches specification |

---

#### TC-TXT-009: Verify Text Input Field XSS Prevention
**Priority:** Critical  
**Type:** Security

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Field is visible |
| 2 | Enter XSS payload (e.g., `<script>alert('XSS')</script>`) | Payload is sanitized or escaped |
| 3 | Verify no script execution | No alert appears, script is rendered as text |

---

#### TC-TXT-010: Verify Text Input Field SQL Injection Prevention
**Priority:** Critical  
**Type:** Security

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Field is visible |
| 2 | Enter SQL injection payload (e.g., `' OR '1'='1`) | Payload is treated as plain text |
| 3 | Verify no SQL injection | Application handles input safely |

---

#### TC-TXT-011: Verify Text Input Field HTML Tags Handling
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Field is visible |
| 2 | Enter HTML tags (e.g., `<b>Bold</b>`) | Tags are either stripped or escaped |
| 3 | Verify rendering | Tags don't render as HTML but display as text |

---

#### TC-TXT-012: Verify Text Input Field Copy-Paste Functionality
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Copy text to clipboard | Text is copied |
| 2 | Paste into the text input field | Text is pasted successfully |
| 3 | Verify pasted content | Content displays correctly |
| 4 | Test with formatted text (from Word, etc.) | Formatting is removed, plain text is pasted |

---

#### TC-TXT-013: Verify Text Input Field Character Counter Display
**Priority:** Low  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the text input field | Field is visible |
| 2 | Check for character counter display | Counter is visible if implemented |
| 3 | Enter text and observe counter | Counter updates in real-time |
| 4 | Verify counter accuracy | Count matches actual character count |

---

### 3. Password Input Field Tests

#### TC-PWD-001: Verify Password Input Field Masks Characters
**Priority:** Critical  
**Type:** Security

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the password input field | Password field is visible |
| 2 | Enter a password (e.g., "SecurePass123!") | Characters are masked (shown as dots or asterisks) |
| 3 | Verify masking | Actual characters are not visible |

---

#### TC-PWD-002: Verify Password Input Field Show/Hide Toggle
**Priority:** High  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the password input field | Field is visible |
| 2 | Check for show/hide toggle icon | Icon is visible (if implemented) |
| 3 | Click show password icon | Password becomes visible as plain text |
| 4 | Click hide password icon | Password is masked again |

---

#### TC-PWD-003: Verify Password Input Field Accepts Strong Passwords
**Priority:** High  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the password input field | Field is visible |
| 2 | Enter a strong password (e.g., "MyP@ssw0rd!2024") | Password is accepted |
| 3 | Verify acceptance | Field accepts the password |

---

#### TC-PWD-004: Verify Password Input Field Minimum Length Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify minimum password length requirement | Min length is documented or indicated |
| 2 | Enter password below minimum length | Validation error is displayed |
| 3 | Enter password at exact minimum length | Password is accepted |

---

#### TC-PWD-005: Verify Password Input Field Maximum Length Validation
**Priority:** Medium  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify maximum password length (if any) | Max length is documented |
| 2 | Enter password exceeding maximum length | Additional characters are not accepted OR error is shown |
| 3 | Verify maximum enforcement | Field respects maximum length |

---

#### TC-PWD-006: Verify Password Input Field Special Character Requirement
**Priority:** High  
**Type:** Validation

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify if special characters are required | Requirement is documented or indicated |
| 2 | Enter password without special characters | Validation error appears (if required) |
| 3 | Enter password with special characters | Password is accepted |

---

#### TC-PWD-007: Verify Password Input Field Uppercase Requirement
**Priority:** High  
**Type:** Validation

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify if uppercase letters are required | Requirement is documented |
| 2 | Enter password without uppercase letters | Validation error appears (if required) |
| 3 | Enter password with uppercase letters | Password is accepted |

---

#### TC-PWD-008: Verify Password Input Field Lowercase Requirement
**Priority:** High  
**Type:** Validation

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify if lowercase letters are required | Requirement is documented |
| 2 | Enter password without lowercase letters | Validation error appears (if required) |
| 3 | Enter password with lowercase letters | Password is accepted |

---

#### TC-PWD-009: Verify Password Input Field Number Requirement
**Priority:** High  
**Type:** Validation

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify if numbers are required | Requirement is documented |
| 2 | Enter password without numbers | Validation error appears (if required) |
| 3 | Enter password with numbers | Password is accepted |

---

#### TC-PWD-010: Verify Password Strength Indicator
**Priority:** Medium  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the password input field | Field is visible |
| 2 | Check for password strength indicator | Indicator is visible (if implemented) |
| 3 | Enter weak password (e.g., "123") | Indicator shows "Weak" |
| 4 | Enter medium password (e.g., "Pass123") | Indicator shows "Medium" |
| 5 | Enter strong password (e.g., "P@ssw0rd!123") | Indicator shows "Strong" |

---

#### TC-PWD-011: Verify Password Input Field Copy-Paste Restriction
**Priority:** Medium  
**Type:** Security

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Copy a password to clipboard | Password is copied |
| 2 | Attempt to paste into password field | Paste is either blocked or allowed based on security policy |
| 3 | Verify paste behavior | Behavior matches security requirements |

---

#### TC-PWD-012: Verify Password Input Field Spaces Handling
**Priority:** High  
**Type:** Validation

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the password input field | Field is visible |
| 2 | Enter password with spaces (e.g., "Pass Word123") | Spaces are either accepted or rejected based on policy |
| 3 | Verify space handling | Behavior is consistent with password policy |

---

#### TC-PWD-013: Verify Password Input Field Auto-Complete Behavior
**Priority:** Medium  
**Type:** Security

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the password input field | Field is visible |
| 2 | Check autocomplete attribute | Attribute is set appropriately (autocomplete="new-password" or "current-password") |
| 3 | Verify browser doesn't auto-fill inappropriately | Browser respects autocomplete settings |

---

### 4. Date Input Field Tests

#### TC-DATE-001: Verify Date Input Field Date Picker Appears
**Priority:** High  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Click on the date field | Date picker calendar appears |
| 3 | Verify calendar display | Calendar shows current month and year |

---

#### TC-DATE-002: Verify Date Input Field Accepts Valid Date Selection
**Priority:** High  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Click on the date input field | Date picker appears |
| 2 | Select a valid date from calendar | Date is selected |
| 3 | Verify selected date appears in field | Field displays selected date in correct format (e.g., MM/DD/YYYY) |

---

#### TC-DATE-003: Verify Date Input Field Manual Date Entry
**Priority:** High  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Manually type a valid date (e.g., "10/22/2025") | Date is accepted |
| 3 | Verify date format | Field displays date correctly |

---

#### TC-DATE-004: Verify Date Input Field Invalid Date Format Rejection
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Enter invalid date format (e.g., "25/13/2025", "abc") | Validation error appears OR input is rejected |
| 3 | Verify error message | Clear error message is displayed |

---

#### TC-DATE-005: Verify Date Input Field Minimum Date Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify minimum allowed date (if any) | Min date is documented |
| 2 | Attempt to select/enter date before minimum | Date is rejected or validation error appears |
| 3 | Select the minimum date exactly | Date is accepted |

---

#### TC-DATE-006: Verify Date Input Field Maximum Date Validation
**Priority:** High  
**Type:** Boundary

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify maximum allowed date (if any) | Max date is documented |
| 2 | Attempt to select/enter date after maximum | Date is rejected or validation error appears |
| 3 | Select the maximum date exactly | Date is accepted |

---

#### TC-DATE-007: Verify Date Input Field Future Date Handling
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Select a future date | Date is either accepted or rejected based on business rules |
| 3 | Verify future date handling | Behavior matches specification |

---

#### TC-DATE-008: Verify Date Input Field Past Date Handling
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Select a past date | Date is either accepted or rejected based on business rules |
| 3 | Verify past date handling | Behavior matches specification |

---

#### TC-DATE-009: Verify Date Input Field Leap Year Validation
**Priority:** Medium  
**Type:** Edge Case

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Enter February 29 in a leap year (e.g., 2024) | Date is accepted |
| 3 | Enter February 29 in a non-leap year (e.g., 2025) | Date is rejected with validation error |

---

#### TC-DATE-010: Verify Date Input Field Invalid Day Validation
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate the date input field | Field is visible |
| 2 | Enter invalid day for month (e.g., "31/02/2025", "31/04/2025") | Validation error appears |
| 3 | Verify error message | Error message indicates invalid date |

---

#### TC-DATE-011: Verify Date Input Field Navigation Between Months
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Click on the date input field | Date picker appears |
| 2 | Click next month arrow | Calendar advances to next month |
| 3 | Click previous month arrow | Calendar goes back to previous month |
| 4 | Verify navigation | Navigation works smoothly |

---

#### TC-DATE-012: Verify Date Input Field Navigation Between Years
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Click on the date input field | Date picker appears |
| 2 | Click on year dropdown/selector | Year selection interface appears |
| 3 | Select a different year | Calendar updates to selected year |
| 4 | Verify year navigation | Year changes correctly |

---

#### TC-DATE-013: Verify Date Input Field Clear/Reset Functionality
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Select a date in the date field | Date is displayed |
| 2 | Look for clear/reset button | Clear button is visible (if implemented) |
| 3 | Click clear button | Date is cleared from field |
| 4 | Verify field is empty | Field returns to empty state |

---

#### TC-DATE-014: Verify Date Input Field Keyboard Navigation
**Priority:** Medium  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Tab to the date input field | Field receives focus |
| 2 | Press arrow keys (up/down/left/right) | Navigation works within date picker (if applicable) |
| 3 | Press Enter to select | Date is selected |
| 4 | Verify keyboard navigation | All date picker functions accessible via keyboard |

---

#### TC-DATE-015: Verify Date Input Field Today/Current Date Shortcut
**Priority:** Low  
**Type:** Usability

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Click on the date input field | Date picker appears |
| 2 | Look for "Today" button | Today button is visible (if implemented) |
| 3 | Click "Today" button | Current date is selected |
| 4 | Verify current date | Today's date appears in the field |

---

### 5. Form Submission Tests

#### TC-FORM-001: Verify Form Submission with All Valid Data
**Priority:** Critical  
**Type:** Positive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill all input fields with valid data | All fields accept input |
| 2 | Click Submit button | Form is submitted successfully |
| 3 | Verify success message or redirect | Success confirmation appears OR page redirects |
| 4 | Verify data integrity | Submitted data matches entered data |

---

#### TC-FORM-002: Verify Form Submission with Empty Required Fields
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Leave required fields empty | Fields are empty |
| 2 | Click Submit button | Form submission is prevented |
| 3 | Verify validation messages | Error messages appear for required fields |
| 4 | Verify focus | Focus moves to first invalid field |

---

#### TC-FORM-003: Verify Form Submission with One Invalid Field
**Priority:** High  
**Type:** Negative

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill all fields with valid data except one | Most fields are valid |
| 2 | Enter invalid data in one field | Invalid data in single field |
| 3 | Click Submit button | Form submission is prevented |
| 4 | Verify specific error message | Error message appears for the invalid field only |

---

#### TC-FORM-004: Verify Form Submission Button State
**Priority:** Medium  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate to the form | Submit button is visible |
| 2 | Verify initial state | Button is enabled OR disabled based on form state |
| 3 | Fill required fields | Button becomes enabled (if initially disabled) |
| 4 | Clear required fields | Button becomes disabled (if dynamic validation) |

---

#### TC-FORM-005: Verify Form Submission Loading State
**Priority:** Medium  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill form with valid data | All fields are filled |
| 2 | Click Submit button | Loading indicator appears |
| 3 | Observe submit button | Button is disabled or shows loading state |
| 4 | Verify form cannot be resubmitted | Form submission is prevented during processing |

---

#### TC-FORM-006: Verify Form Submission Duplicate Prevention
**Priority:** High  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill form with valid data | All fields are filled |
| 2 | Click Submit button | Form submits |
| 3 | Quickly click Submit button again | Second submission is prevented |
| 4 | Verify single submission | Only one submission is processed |

---

#### TC-FORM-007: Verify Form Reset Functionality
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill all input fields with data | All fields contain data |
| 2 | Look for Reset button | Reset button is visible (if implemented) |
| 3 | Click Reset button | All fields are cleared |
| 4 | Verify field states | All fields return to default empty state |

---

#### TC-FORM-008: Verify Form Data Persistence on Error
**Priority:** Medium  
**Type:** Usability

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill form with mostly valid data | Most fields are filled |
| 2 | Enter invalid data in one field | One field is invalid |
| 3 | Submit form | Validation error appears |
| 4 | Verify data retention | Valid field data is retained (not cleared) |

---

#### TC-FORM-009: Verify Form Submission with Enter Key
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill form with valid data | All fields are filled |
| 2 | Press Enter key while in any field | Form submits (if expected behavior) |
| 3 | Verify submission | Form processes submission correctly |

---

#### TC-FORM-010: Verify Form Validation Timing
**Priority:** Medium  
**Type:** UX

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Start entering data in a field | Field is being filled |
| 2 | Observe validation trigger | Validation triggers at appropriate time (on blur, on change, or on submit) |
| 3 | Verify validation feedback | Immediate feedback for invalid input (if real-time validation) |
| 4 | Verify UX consistency | Validation behavior is consistent across all fields |

---

### 6. Cross-Field Validation Tests

#### TC-CROSS-001: Verify Interdependent Field Validation
**Priority:** High  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify fields with dependencies | Dependencies are documented |
| 2 | Enter data in first field | Data is accepted |
| 3 | Enter dependent data in related field | Validation checks relationship |
| 4 | Verify cross-field validation | Related fields validate correctly together |

---

#### TC-CROSS-002: Verify Conditional Field Display
**Priority:** Medium  
**Type:** Functional

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Identify conditional fields (if any) | Conditional logic is documented |
| 2 | Perform action to trigger field display | Condition is met |
| 3 | Verify field appears | Conditional field becomes visible |
| 4 | Change condition | Field hides when condition is not met |

---

#### TC-CROSS-003: Verify Date Range Validation
**Priority:** High  
**Type:** Validation

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | If form has start and end dates | Fields are identified |
| 2 | Enter end date before start date | Validation error appears |
| 3 | Enter valid date range | Dates are accepted |
| 4 | Verify range validation | Error message is clear and specific |

---

### 7. UI/UX Tests

#### TC-UI-001: Verify All Input Fields Are Visible
**Priority:** High  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate to the inputs page | Page loads completely |
| 2 | Verify all input fields are visible | Number, Text, Password, and Date fields are visible |
| 3 | Check field labels | All fields have clear, descriptive labels |
| 4 | Verify field order | Fields are in logical order |

---

#### TC-UI-002: Verify Input Field Placeholder Text
**Priority:** Medium  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Locate each input field | All fields are visible |
| 2 | Check for placeholder text | Placeholder text is visible (if implemented) |
| 3 | Verify placeholder clarity | Placeholder provides helpful hint |
| 4 | Enter data | Placeholder disappears when typing |

---

#### TC-UI-003: Verify Input Field Focus State
**Priority:** Medium  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Tab through input fields OR click on field | Field receives focus |
| 2 | Verify focus indicator | Clear visual focus indicator (border color change, outline, etc.) |
| 3 | Verify focus order | Tab order is logical and sequential |

---

#### TC-UI-004: Verify Input Field Error State Display
**Priority:** High  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enter invalid data in a field | Invalid data is entered |
| 2 | Trigger validation | Validation occurs |
| 3 | Verify error state styling | Field displays error state (red border, error icon, etc.) |
| 4 | Verify error message | Clear error message appears near the field |

---

#### TC-UI-005: Verify Input Field Success State Display
**Priority:** Low  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enter valid data in a field | Valid data is entered |
| 2 | Trigger validation | Validation occurs |
| 3 | Verify success state styling | Field displays success state (green border, checkmark, etc.) if implemented |

---

#### TC-UI-006: Verify Responsive Design - Mobile View
**Priority:** High  
**Type:** Responsive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page on mobile device or resize browser to mobile width (375px) | Page loads |
| 2 | Verify all fields are visible | No horizontal scrolling required |
| 3 | Verify field sizing | Fields are appropriately sized for mobile |
| 4 | Test touch interactions | All fields are easily tappable |

---

#### TC-UI-007: Verify Responsive Design - Tablet View
**Priority:** Medium  
**Type:** Responsive

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page on tablet or resize browser to tablet width (768px) | Page loads |
| 2 | Verify layout | Layout adjusts appropriately for tablet |
| 3 | Test interactions | All functionality works on tablet |

---

#### TC-UI-008: Verify Consistent Styling Across Fields
**Priority:** Medium  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Observe all input fields | All fields are visible |
| 2 | Compare field heights | Heights are consistent |
| 3 | Compare field widths | Widths follow design pattern |
| 4 | Compare font sizes and colors | Styling is consistent |

---

#### TC-UI-009: Verify Field Label Alignment
**Priority:** Low  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Observe form layout | Form is visible |
| 2 | Check label alignment | Labels are properly aligned (left, top, etc.) |
| 3 | Verify label-field association | Labels are clearly associated with their fields |

---

#### TC-UI-010: Verify Help Text/Tooltips Display
**Priority:** Low  
**Type:** UI

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Look for help icons or tooltips | Help indicators are visible (if implemented) |
| 2 | Hover over or click help icon | Tooltip or help text appears |
| 3 | Verify help text content | Content is helpful and clear |

---

### 8. Accessibility Tests

#### TC-A11Y-001: Verify Keyboard Navigation Through All Fields
**Priority:** Critical  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate to the page | Page loads |
| 2 | Use Tab key to navigate forward | Focus moves through all interactive elements in order |
| 3 | Use Shift+Tab to navigate backward | Focus moves backward through elements |
| 4 | Verify all fields are reachable | No keyboard traps exist |

---

#### TC-A11Y-002: Verify Screen Reader Compatibility
**Priority:** Critical  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enable screen reader (NVDA, JAWS, VoiceOver) | Screen reader is active |
| 2 | Navigate through form | Screen reader announces each field |
| 3 | Verify label announcements | Field labels are announced correctly |
| 4 | Verify error announcements | Validation errors are announced |

---

#### TC-A11Y-003: Verify ARIA Labels and Attributes
**Priority:** High  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Inspect each input field | Fields are in DOM |
| 2 | Check for aria-label or aria-labelledby | ARIA labels are present |
| 3 | Check for aria-required on required fields | Required fields have aria-required="true" |
| 4 | Check for aria-invalid on error state | Invalid fields have aria-invalid="true" |

---

#### TC-A11Y-004: Verify Focus Visible Indicator
**Priority:** High  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate using keyboard | Tab through elements |
| 2 | Verify focus outline | Clear, visible focus indicator on all elements |
| 3 | Check color contrast | Focus indicator meets WCAG 2.1 contrast ratio (3:1) |

---

#### TC-A11Y-005: Verify Color Contrast for Text
**Priority:** High  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Use color contrast checker tool | Tool is ready |
| 2 | Check label text contrast | Contrast ratio is at least 4.5:1 (WCAG AA) |
| 3 | Check input text contrast | Contrast ratio is at least 4.5:1 |
| 4 | Check error message contrast | Contrast ratio is at least 4.5:1 |

---

#### TC-A11Y-006: Verify Form Semantics and Structure
**Priority:** High  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Inspect HTML structure | Form is in DOM |
| 2 | Verify form uses `<form>` element | Proper semantic HTML |
| 3 | Verify labels use `<label>` with correct `for` attribute | Labels are properly associated |
| 4 | Verify appropriate input types | Semantic input types are used (type="email", type="tel", etc.) |

---

#### TC-A11Y-007: Verify Error Message Association
**Priority:** High  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enter invalid data to trigger error | Error appears |
| 2 | Verify aria-describedby links field to error | Error message ID is referenced |
| 3 | Test with screen reader | Error is announced when field receives focus |

---

#### TC-A11Y-008: Verify Skip Links and Landmarks
**Priority:** Medium  
**Type:** Accessibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate to page | Page loads |
| 2 | Press Tab first time | Skip link appears (if implemented) |
| 3 | Verify ARIA landmarks | Form has appropriate role or landmark |

---

### 9. Browser Compatibility Tests

#### TC-BROWSER-001: Verify Functionality on Chrome
**Priority:** Critical  
**Type:** Compatibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page in latest Chrome version | Page loads correctly |
| 2 | Test all input fields | All fields work as expected |
| 3 | Test form submission | Form submits successfully |
| 4 | Verify no console errors | No JavaScript errors in console |

---

#### TC-BROWSER-002: Verify Functionality on Firefox
**Priority:** Critical  
**Type:** Compatibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page in latest Firefox version | Page loads correctly |
| 2 | Test all input fields | All fields work as expected |
| 3 | Test form submission | Form submits successfully |
| 4 | Verify no console errors | No JavaScript errors in console |

---

#### TC-BROWSER-003: Verify Functionality on Safari
**Priority:** High  
**Type:** Compatibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page in latest Safari version | Page loads correctly |
| 2 | Test all input fields | All fields work as expected |
| 3 | Test date picker specifically | Safari's native date picker works |
| 4 | Verify form submission | Form submits successfully |

---

#### TC-BROWSER-004: Verify Functionality on Edge
**Priority:** High  
**Type:** Compatibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page in latest Edge version | Page loads correctly |
| 2 | Test all input fields | All fields work as expected |
| 3 | Test form submission | Form submits successfully |

---

#### TC-BROWSER-005: Verify Mobile Browser - iOS Safari
**Priority:** High  
**Type:** Compatibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page in iOS Safari | Page loads correctly |
| 2 | Test touch interactions | All fields respond to touch |
| 3 | Test native keyboard for different input types | Appropriate keyboard appears (numeric for number fields, etc.) |
| 4 | Verify form submission | Form works on mobile Safari |

---

#### TC-BROWSER-006: Verify Mobile Browser - Chrome Android
**Priority:** High  
**Type:** Compatibility

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Open page in Chrome on Android | Page loads correctly |
| 2 | Test touch interactions | All fields respond to touch |
| 3 | Test native keyboard | Appropriate keyboard appears |
| 4 | Verify form submission | Form works on Android Chrome |

---

### 10. Performance Tests

#### TC-PERF-001: Verify Page Load Time
**Priority:** Medium  
**Type:** Performance

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Clear browser cache | Cache is cleared |
| 2 | Navigate to inputs page | Page loads |
| 3 | Measure page load time | Page loads in acceptable time (< 3 seconds) |
| 4 | Verify all elements are interactive | Form is ready for user input |

---

#### TC-PERF-002: Verify Input Field Response Time
**Priority:** Medium  
**Type:** Performance

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Click/focus on input field | Field receives focus |
| 2 | Type characters rapidly | Characters appear without lag |
| 3 | Verify no input delay | Response time is immediate |

---

#### TC-PERF-003: Verify Validation Performance
**Priority:** Low  
**Type:** Performance

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enter data in field | Data is entered |
| 2 | Trigger validation | Validation executes |
| 3 | Measure validation time | Validation completes quickly (< 500ms) |
| 4 | Verify no UI freeze | UI remains responsive during validation |

---

#### TC-PERF-004: Verify Form Submission Performance
**Priority:** Medium  
**Type:** Performance

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Fill form with valid data | Form is complete |
| 2 | Click Submit button | Submission begins |
| 3 | Measure submission time | Response is received in reasonable time |
| 4 | Verify user feedback | Loading indicator or response appears promptly |

---

## Test Execution Summary Template

| **Metric** | **Count** |
|------------|-----------|
| Total Test Cases | 120+ |
| Priority: Critical | 8 |
| Priority: High | 52 |
| Priority: Medium | 45 |
| Priority: Low | 15 |
| Test Type: Positive | 25 |
| Test Type: Negative | 18 |
| Test Type: Boundary | 12 |
| Test Type: Functional | 35 |
| Test Type: UI | 15 |
| Test Type: Security | 5 |
| Test Type: Accessibility | 8 |
| Test Type: Performance | 4 |

---

## Test Data Sets

### Valid Test Data

**Number Input:**
- Positive integer: 100, 42, 999
- Negative integer: -50, -100
- Decimal: 123.45, 0.99, -45.67
- Zero: 0
- Boundary values: 1, -1

**Text Input:**
- Alphanumeric: "Test123", "User456"
- Special characters: "@Test!", "Name#1"
- Unicode: "Привет", "你好", "مرحبا"
- With spaces: "John Doe", "Test User"
- Mixed case: "TeSt", "MixedCase123"

**Password Input:**
- Strong: "MyP@ssw0rd!2024", "Secure#Pass123"
- With special chars: "Test!@#$123Abc"
- Long password: "ThisIsAVeryLongPassword123!@#"

**Date Input:**
- Valid dates: "10/22/2025", "01/01/2024", "12/31/2023"
- Leap year: "02/29/2024"
- Current date: [Today's date]

### Invalid Test Data

**Number Input:**
- Alphabetic: "abc", "test"
- Special chars: "@#$%", "!*&"
- Mixed: "123abc", "test456"

**Text Input:**
- SQL Injection: `' OR '1'='1`, `'; DROP TABLE users--`
- XSS: `<script>alert('XSS')</script>`, `<img src=x onerror=alert(1)>`
- HTML: `<b>Bold</b>`, `<div>Test</div>`

**Password Input:**
- Too short: "123", "ab"
- No uppercase: "password123!"
- No special char: "Password123"
- Only numbers: "12345678"

**Date Input:**
- Invalid format: "2025-22-10", "abc"
- Invalid day: "31/02/2025", "31/04/2025"
- Invalid month: "13/01/2025", "00/01/2025"
- Non-leap year Feb 29: "02/29/2025"

---

## Notes for Automation

### Recommended Locator Strategies

```typescript
// Number Input
const numberInput = page.getByLabel('Number');
// or
const numberInput = page.locator('input[type="number"]');

// Text Input
const textInput = page.getByLabel('Text');
// or
const textInput = page.locator('input[type="text"]');

// Password Input
const passwordInput = page.getByLabel('Password');
// or
const passwordInput = page.locator('input[type="password"]');

// Date Input
const dateInput = page.getByLabel('Date');
// or
const dateInput = page.locator('input[type="date"]');

// Submit Button
const submitButton = page.getByRole('button', { name: 'Submit' });
```

### Wait Strategies

- Use `waitForLoadState('domcontentloaded')` after navigation
- Use `waitForSelector()` for dynamic elements
- Use `toBeVisible()` assertions for element checks
- Implement explicit waits for validation messages

### Data-Driven Testing Approach

Consider parameterizing these test cases for data-driven execution:
- TC-NUM-001 through TC-NUM-012
- TC-TXT-001 through TC-TXT-006
- TC-PWD-003 through TC-PWD-009
- TC-DATE-002, TC-DATE-003, TC-DATE-004

---

## Appendix

### Severity Definitions

- **Critical:** Core functionality that prevents form usage
- **High:** Major functionality with workarounds possible
- **Medium:** Minor issues with low impact
- **Low:** Cosmetic or enhancement suggestions

### Test Environment Setup

1. Ensure stable internet connection
2. Clear browser cache before test execution
3. Use latest browser versions
4. Disable browser extensions that may interfere
5. Enable JavaScript in browser settings

---

**Document Version:** 1.0  
**Created By:** QA Team  
**Last Review Date:** October 22, 2025  
**Next Review Date:** January 22, 2026
# Testing Strategy

## Overview

This document describes the testing approach for the workflow portfolio.

## Test Levels

### 1. Unit Tests
Individual node testing:
- Input/output validation
- Expression correctness
- Field mapping accuracy

### 2. Integration Tests
End-to-end workflow testing:
- Trigger -> All Nodes -> Output
- Cross-service communication
- Data flow validation

### 3. Manual Tests
Human verification:
- Visual workflow inspection
- Output quality assessment
- Edge case handling

## Test Documentation

Each workflow has:
- `test-cases.md` - Test case matrix
- Scenario documentation
- Edge case handling
- Performance benchmarks

## Test Environment

### Required Setup
- n8n instance
- Test Google account
- Test API credentials
- Test data files

### Data Isolation
- Separate test sheets
- Sandbox APIs where possible
- Test-only credentials

## Test Execution

### Manual Testing
1. Import workflow to n8n
2. Configure with test credentials
3. Trigger with test data
4. Verify expected output
5. Check error handling

### Automated Testing
GitHub Actions validate:
- JSON syntax
- Workflow structure
- No exposed secrets
- Required files present

## Coverage

| Workflow | Test Cases | Coverage |
|----------|-----------|----------|
| Invoice Processing | 8 cases | Core paths |
| Lead Qualification | 7 cases | Core paths |
| RAG Agent | 7 cases | Core paths |
| Lead Capture | 5 cases | Core paths |
| Department News | 4 cases | Basic |
| Content Generation | 5 cases | Core paths |

## Future Improvements

- [ ] Automated test execution
- [ ] Mock data generators
- [ ] Performance benchmarks
- [ ] Load testing
- [ ] Security scanning

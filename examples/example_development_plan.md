# TypeScript Uplift Plan

## Overview

This document outlines the plan to enhance code reliability and maintainability by aligning with TypeScript best practices, eliminating the use of `any` types, updating outdated packages, and ensuring the application compiles successfully whilst maintaining functionality.

The goal is to complete the tasks in a phased approach, marking off completed items as you go.

## Current State Analysis

### Critical Issues Identified

1. **TypeScript Configuration Problems**
   - `strict: false` - Disables all strict type checking
   - `noImplicitAny: false` - Allows implicit any types
   - `target: "es5"` - Using outdated ES5 target
   - TypeScript version 4.9.5 is significantly outdated (latest: 5.8.3)

2. **Extensive Use of `any` Types**
   - Global variables declared as `any`: `currentLanguage`, `translations`, `inventoryData`
   - Function parameters using `any`: `item: any`, `whStock: any`
   - DOM element queries cast to `any` without proper type checking
   - XMLHttpRequest responses handled without type safety

3. **Poor Code Practices**
   - Synchronous XMLHttpRequest calls (deprecated and blocking)
   - Direct DOM manipulation without type safety
   - No proper error handling or type guards
   - Global state management without proper typing
   - Potential XSS vulnerabilities with `innerHTML` usage

4. **Outdated Dependencies**
   - TypeScript: 4.9.5 → 5.8.3 (major version behind)
   - ESLint TypeScript plugins: 7.13.0 → 8.34.0
   - Jest: 29.7.0 → 30.0.0
   - Node types: 22.14.1 → 24.0.1

5. **ESLint Configuration Issues**
   - All TypeScript strict rules disabled
   - `@typescript-eslint/no-explicit-any` turned off
   - Missing important linting rules for code quality

---

## Requirements & Constraints

1. **Node.js Version**: Target Node.js v22 LTS (as per project guidelines)
2. **TypeScript Version**: Upgrade to TypeScript 5.8.x (latest stable)
3. **Backward Compatibility**: Maintain all existing application functionality
4. **Security**: No exposure of internal errors; proper input sanitisation
5. **Code Quality**: Zero TypeScript compilation errors; all linting rules must pass

---

## Development Plan (Implementation Checklist)

### Phase 1 - Dependencies & Configuration
- [ ] Update package.json with latest versions
- [ ] Update tsconfig.json with strict settings
- [ ] Update .eslintrc.json with proper rules
- [ ] Test build process after updates
- [ ] STOP and wait for human review

### Phase 2 - Type System
- [ ] Define all interface types
- [ ] Replace all `any` types with proper types
- [ ] Add type guards and null checks
- [ ] Implement proper error types
- [ ] Perform a critical self-review of your changes and fix any issues related to your changes
- [ ] STOP and wait for human review

### Phase 3 - Code Refactoring
- [ ] Replace XMLHttpRequest with fetch API
- [ ] Implement async/await patterns
- [ ] Add proper error handling
- [ ] Replace innerHTML with safe alternatives
- [ ] Perform a critical self-review of your changes and fix any issues related to your changes
- [ ] STOP and wait for human review

### Phase 4 - Testing
- [ ] Write unit tests for core functions
- [ ] Add integration tests for data loading and DOM manipulation
- [ ] Achieve minimum 80% test coverage
- [ ] Test all error scenarios and edge cases
- [ ] Perform a critical self-review of your changes and fix any issues related to your changes
- [ ] STOP and wait for human review

### Phase 5 - Quality Assurance
- [ ] Run linting with no errors or warnings
- [ ] Ensure TypeScript compilation succeeds with zero errors
- [ ] Verify all tests pass
- [ ] Test application functionality manually
- [ ] Perform basic performance testing
- [ ] STOP and wait for human review

### Phase 6 - Final Review

- [ ] Verify zero TypeScript compilation errors across entire codebase
- [ ] Confirm all linting passes with no warnings or errors
- [ ] Run full test suite and verify 100% pass rate
- [ ] Verify all previous phase tasks are marked complete, or partially complete ([-]) with explanation if incomplete
- [ ] Review documentation for accuracy, conciseness, and remove any duplicate content
- [ ] Confirm application runs successfully with `npm run dev`
- [ ] STOP and wait for human review

---

## Uplift Strategy

### Phase 1: Foundation Updates

**Goal**: Update dependencies and enable strict TypeScript configuration to catch type safety issues.

**Key Changes**:
- Update TypeScript to 5.8.x, Jest to 30.x, and other outdated dependencies
- Enable strict TypeScript settings (`strict: true`, `noImplicitAny: true`)
- Update compilation target to ES2024 for modern JavaScript support
- Configure ESLint to enforce type safety rules (`no-explicit-any`, `no-unsafe-assignment`)
- Verify build succeeds after configuration changes

### Phase 2: Types & Interfaces

**Goal**: Eliminate all `any` types by defining proper interfaces and type-safe DOM manipulation.

**Key Changes**:
- Define typed interfaces for inventory data (items, warehouse stock)
- Define typed interfaces for translation messages and app state
- Replace all global `any` variables with proper types (`currentLanguage`, `translations`, `inventoryData`)
- Implement type-safe DOM manipulation with proper HTMLElement types and null checks
- Add type guards where needed for runtime validation
- Ensure proper event handler typing throughout

### Phase 3: Code Quality & Security

**Goal**: Modernise async patterns, improve error handling, and fix security vulnerabilities.

**Key Changes**:
- Replace deprecated synchronous XMLHttpRequest with modern `fetch()` API
- Implement async/await patterns for better readability and error handling
- Add proper typed error handling with custom error classes where beneficial
- Replace `innerHTML` usage with safer alternatives (`textContent`, proper DOM methods)
- Implement input sanitisation to prevent XSS vulnerabilities
- Add proper null checks and graceful degradation for missing data

### Phase 4: Testing

**Goal**: Build test coverage to verify type safety and functionality.

**Key Changes**:
- Write unit tests for all core functions (data loading, DOM manipulation, error handling)
- Add integration tests for complete workflows
- Test error scenarios and edge cases thoroughly
- Configure Jest with proper TypeScript support
- Add test coverage reporting with 80% minimum threshold
- Create shared test utilities to reduce duplication

---

## Success Criteria

1. **Zero TypeScript Compilation Errors**: All code must compile without errors or warnings
2. **No `any` Types**: Complete elimination of explicit and implicit `any` usage
3. **Minimum 80% Test Coverage**: All core functionality must have corresponding tests
4. **Linting Compliance**: Code must pass all ESLint rules without warnings
5. **Functional Parity**: Application must maintain all existing functionality
6. **Security Enhanced**: Proper type checking, input validation, and XSS prevention implemented

## Risk Mitigation

- **Breaking Changes**: Thorough testing at each phase to catch regressions early
- **Type System**: Gradual implementation with fallbacks during transition
- **Dependencies**: Careful version compatibility checking before updates
- **Avoid Over-Engineering**: Focus on practical improvements without unnecessary complexity
- **Avoid prematurely claiming tasks as complete**: Ensure each task is fully verified before marking it as done

**Note:** Each phase in this plan includes verification steps to ensure the application continues to function correctly. The phased approach allows for early detection and resolution of issues before they compound. You MUST stop at the end of each phase and ask for human review. Do not deviate from the plan unless required.

---

## Working Notes (Optional)

**Purpose:** This section is available for the executing agent to track complex issues, troubleshooting attempts, and problem-solving progress during development.

**When to use:**
- Encountering persistent bugs or issues that require multiple solution attempts
- Tracking what has been tried and ruled out for a specific problem
- Documenting complex debugging steps or investigation findings
- Keeping notes on temporary workarounds or decisions made during implementation

**Format:** Use this space freely - bullet points, links to documentation you found you needed, outstanding error messages, whatever helps track your problem-solving process but try to keep it updated ask you solve issues.

### Notes

- Related to phase/task: , (Placeholder for working notes if required during development)

---

IMPORTANT:

This document **MUST** be updated at the end of each phase as the uplift progresses to check off any tasks completed to 100%, reflect actual implementation details and any adjustments to the plan that the user has agreed to.

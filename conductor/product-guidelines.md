# Product Guidelines

## Core Principles
1. **Developer-First Experience:** Ensure APIs are intuitive, well-documented, and strictly typed.
2. **Predictability over Magic:** Internal mechanisms (especially LLM prompt orchestration) should be transparent and explicitly controllable.
3. **Fail Safely:** Unhandled exceptions in agent logic must gracefully degrade rather than crash the host application.

## Prose & Documentation Style
- **Tone:** Professional, precise, and objective. Avoid hyperbole ("super easy", "magical").
- **Clarity:** Use active voice and concise phrasing. Focus on the *why* and *how*.
- **Examples:** Every core component must be accompanied by a reproducible, standalone code example.

## UX Principles
- **Minimal Configuration:** Provide sensible defaults that work out-of-the-box.
- **Progressive Disclosure:** Expose advanced configuration (like custom LLM parsers or memory retention policies) only when requested.
- **Meaningful Errors:** Exceptions should clearly state the failure reason and offer actionable resolution steps or link to documentation.
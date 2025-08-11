# GPT-5 Coding Template Prompt

This consolidated template is adapted from the ideas in the [GPT-5 Coding Examples](https://github.com/openai/gpt-5-coding-examples). Use it to structure zero-shot coding tasks with clear goals, deliverables, UX tokens, data/state, validation, accessibility, performance, and acceptance tests so the model can produce runnable outputs with minimal iteration.


```
## Role & Goal
You are {role}. Please complete: {a one-sentence, verifiable goal}.

## Deliverable Contract

* Output: {single/multiple files; filename/entry point; code blocks only or not}
* Tech stack: {allowed list}; prohibited: {external links/frameworks/APIs}
* Runtime environment: {browser/Node/Next.js page.tsx, etc.}

## Visual & Interaction Tokens

* Theme/Color scheme/Fonts/Grid/Border radius/Shadows/Animations (duration ≤ ms, easing…)
* Components: {buttons/tables/cards/dialogs/tooltips…}
* Tone of copy: {professional/playful/tech-oriented…}

## Functionality (MUST/SHOULD/OPTIONAL)
MUST:

1. {control} → {behavior} → {visible feedback}
2. …

SHOULD:
* …

OPTIONAL:
* …

## Data & State

* Input source: {form/URL hash/file upload}
* Default sample/mock data: {count/structure}
* Persistence/Export: {LocalStorage/JSON/PNG/WAV/ICS}
* Randomness: seed={number}; must be reproducible

## Validation & Error Handling

* Constraint range: {…}
* Out-of-range handling: {clamp/show prompt/revert}
* Empty state & loading placeholder: {skeleton/loading image}

## Accessibility & Responsiveness

* Keyboard navigation/focus order/ARIA/contrast
* Support both touch and mouse; PRM fallback
* Breakpoints: {mobile/tablet/desktop} layout rules

## Performance & Quality

* Lazy-load resources/size limit/frame rate target
* No overlap or flicker; CLS ≈ 0
* Terminal compatibility: {latest two versions of Chromium/Firefox/Safari}

## Acceptance Test Cases

* Test case 1: {steps → expected result}
* Test case 2: {steps → expected result}

## Output Restrictions
Strict requirement: only output {file content/code blocks}; prohibit {explanations/external links/multiple files}.
```
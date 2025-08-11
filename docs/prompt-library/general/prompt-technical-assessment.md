# Technical Assessment Report Generation Prompt
Generate a rich HTML technical review report for the whole repo

---
Scan through the whole project source code and generate a technical review report.

# Output Format & Structure
- Output the report as an HTML document with table of content in `/doc` folder
- The name of the report file: technical-review_<repo_name>.html
- Mention the current git branch as part of h3 sub-title
- Mention the date when the report is generated
- Start with TOC that include all the headers
- Followed by Exective Summary, include the repo stats below:
  - Include Total number of src files (excluding non-src files)
  - Totla lines of code in the repo
- Followeed by the findings one by one
- Each finding should have its own header
- Apply numbering on findings header
- Sort the findings based on severity: critical, high, medium, low ...
- Do not inlcude Introduction or Conclusion sections.

# Finding Details
Each finding should contain the following:
- summary
- severity
- details descriptions
- src files occurrence with line number/range
- code snippets
- recommended remediations

# Styling
Use the styling based the CSS code only:
```<style>
/* ----------  Root palette & typography  ---------- */
:root {
  --font-body: "Arial", sans-serif;

  /* Light‑mode colours */
  --clr-bg:           #ffffff;
  --clr-text:         #333333;
  --clr-heading:      #2c3e50;
  --clr-border-light: #dddddd;
  --clr-border-accent:#3498db;

  /* Severity palette (light) */
  --clr-critical: #e74c3c;
  --clr-high:     #e67e22;
  --clr-medium:   #d39e00;   /* WCAG‑compliant contrast */
  --clr-low:      #2980b9;

  /* Utility surfaces */
  --clr-card:     #f9f9f9;
  --clr-code:     #f4f4f4;
  --clr-rec:      #e8f4fc;
}

@media (prefers-color-scheme: dark) {
  :root {
    --clr-bg:       #1e1e1e;
    --clr-text:     #e0e0e0;
    --clr-heading:  #ecf0f1;
    --clr-border-light:#3a3a3a;
    --clr-card:     #272727;
    --clr-code:     #2d2d2d;
    --clr-rec:      #213b4d;
  }
}

/* ----------  Base elements  ---------- */
body {
  font-family: var(--font-body);
  line-height: 1.6;
  margin: 0;
  padding: 20px;
  background: var(--clr-bg);
  color: var(--clr-text);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

h1, h2, h3 {
  color: var(--clr-heading);
  margin: 0 0 0.5em;
}

h1 {
  border-bottom: 2px solid var(--clr-border-accent);
  padding-bottom: 10px;
}

h2 {
  border-bottom: 1px solid var(--clr-border-light);
  padding-bottom: 5px;
  margin-top: 30px;
}

/* ----------  Findings & severity ribbons  ---------- */
.finding {
  margin-bottom: 30px;
  padding: 15px;
  border-radius: 5px;
  background-color: var(--clr-card);
  border-left: 5px solid transparent;
}

.critical { border-left-color: var(--clr-critical); }
.high     { border-left-color: var(--clr-high); }
.medium   { border-left-color: var(--clr-medium); }
.low      { border-left-color: var(--clr-low); }

.severity {
  font-weight: bold;
  display: inline-block;
  padding: 3px 8px;
  border-radius: 3px;
  color: #ffffff;
  margin-bottom: 10px;
}
.severity.critical { background: var(--clr-critical); }
.severity.high     { background: var(--clr-high); }
.severity.medium   { background: var(--clr-medium); color: #1e1e1e; } /* dark text for contrast */
.severity.low      { background: var(--clr-low); }

/* ----------  Code blocks  ---------- */
.code {
  background: var(--clr-code);
  padding: 10px;
  border-radius: 3px;
  font-family: ui-monospace, "SFMono-Regular", "Consolas", monospace;
  overflow-x: auto;
  white-space: pre-wrap;
  border: 1px solid var(--clr-border-light);
}

/* ----------  Table of contents  ---------- */
nav.toc {
  background: var(--clr-card);
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 20px;
}
nav.toc ul {
  list-style: none;
  padding-left: 20px;
}
nav.toc li {
  margin-bottom: 5px;
}
nav.toc a {
  color: var(--clr-border-accent);
  text-decoration: none;
  display: flex;
  align-items: center;
}
nav.toc a:hover,
nav.toc a:focus {
  text-decoration: underline;
  outline: 2px solid var(--clr-border-accent);
  outline-offset: 2px;
}
nav.toc .severity {
  font-size: 0.8em;
  padding: 2px 5px;
  margin-right: 5px;
  vertical-align: middle;
}

/* ----------  Recommendations  ---------- */
.recommendation {
  background: var(--clr-rec);
  padding: 10px;
  border-radius: 3px;
  margin-top: 10px;
  border-left: 3px solid var(--clr-border-accent);
}

/* ----------  Utilities  ---------- */
.branch {
  color: #7f8c8d;
  margin-bottom: 20px;
}

a:focus-visible {
  outline: 2px solid var(--clr-border-accent);
  outline-offset: 2px;
}
</style>
```

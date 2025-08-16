---
description: Prompt template for evaluating assignment submissions and generating structured assessment reports.
---

# Assignment Submission Review Prompt
Review and evaluate client assignment submissions based on curated evaluation guiedline, and generate a rich HTML report

---
Base on the [assignmentRequirement.md], and the evaluation guide [evaluation-guide.md] , evaluate [cadidateName] submission under the folder: [submissionFolder]

# Output Format & Structure
- Output the report as an HTML document with table of content in `/evaluation` folder
- The name of the report file: assignment-review_<submission_name>.html
- Include candidate name in the page title
- Mention the date when the report is generated
- For every main sections, render the h2 header before the div components
- Start with TOC that include all the headers
- Followed by Summary:
  - Total score with big, bold number
  - Overall Assessment for the client manager to grasp the evaluation outcome
  - Total number of src files and Totla lines of code reviewed (excluding non-src files)
- Followed by a Highlight section
  - List out where the candidate did well from the assignment
- Followeed by the findings one by one
  - Each finding should have its own header h3 inside the div
  - Apply numbering on findings header
  - Indicate which of the 5 Evaluation Criteria the finding below to 
  - Sort the findings based on criticality: critical, high, medium, low ...
- Do not inlcude Introduction or Conclusion sections.

# Styling
Use the styling based the CSS code only:
```
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #2c3e50;
            border-bottom: 3px solid #3498db;
            padding-bottom: 10px;
        }
        h2 {
            color: #34495e;
            margin-top: 30px;
            border-left: 4px solid #3498db;
            padding-left: 15px;
        }
        h3 {
            color: #2c3e50;
            margin-top: 25px;
        }
        .toc {
            background-color: #ecf0f1;
            padding: 20px;
            border-radius: 5px;
            margin: 20px 0;
        }
        .toc ul {
            list-style-type: none;
            padding-left: 0;
        }
        .toc li {
            margin: 8px 0;
        }
        .toc a {
            text-decoration: none;
            color: #2980b9;
        }
        .toc a:hover {
            text-decoration: underline;
        }
        .summary {
            /* background-color: #e8f5e8; */
            padding: 20px;
            border-radius: 5px;
            margin: 20px 0;
            border-left: 5px solid #27ae60;
        }
        .total-score {
            font-size: 3em;
            font-weight: bold;
            color: #ffc107;
            /* Success color: #27ae60; */
            /* Failure color: #dc3545; */
            text-align: center;
            margin: 20px 0;
        }
        .highlights {
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: 5px;
            margin: 20px 0;
            border-left: 5px solid #ffc107;
        }
        .finding {
            background-color: #f8f9fa;
            padding: 15px;
            margin: 15px 0;
            border-radius: 5px;
            border-left: 4px solid #6c757d;
        }
        .critical {
            border-left-color: #dc3545;
            /* background-color: #f8d7da; */
        }
        .high {
            border-left-color: #fd7e14;
            /* background-color: #fff3cd; */
        }
        .medium {
            border-left-color: #ffc107;
            /* background-color: #fff3cd; */
        }
        .low {
            border-left-color: #28a745;
            /* background-color: #d4edda; */
        }
        .score-breakdown {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr;
            gap: 10px;
            margin: 20px 0;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 5px;
        }
        .score-breakdown div {
            padding: 8px;
        }
        .score-breakdown .header {
            font-weight: bold;
            background-color: #e9ecef;
        }
        code {
            background-color: #f1f1f1;
            padding: 2px 4px;
            border-radius: 3px;
            font-family: 'Courier New', monospace;
        }
        .date {
            text-align: right;
            color: #6c757d;
            font-style: italic;
            margin-bottom: 20px;
        }
    </style>
```
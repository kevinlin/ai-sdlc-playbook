This prompt can be used to create a single story from user-defined requirements.

```
Create a detailed user story document in an markdown format outlining the following feature requirements.

Please provide the contents for a file named [something.md] in a markdown code block.

I want the format of the user story to be:

---
User Story:
[User story summary in "AS A, I WANT, SO THAT" format. This be functional and omit technical details]

Acceptance Criteria:
[Written as testable BBD Scenarios. The DDD scenarios should focus on functional/user-driven actions. Omit any technical details.  Try and group functionality so that we keep the number of scenarios to a minimum]

UI Design:
[Relevant user interface design. Follow guidelines including the Design System and Accessibility.]

Technical Design:
[The functionality defined in technical detail.  Include the API Responses as examples from below]

---

# Context

[releavnt context e.g. this is adding to an existing applicaiton, so give a suitably detailed summary of that application.]

# Detailed Requirements

[Detail for each feature you want it implement. Include funcitonal details and any relevent technical details]


## APIS

[This example is based on API's, but this section should be changed as appropriate to include any dependencies]

### API One

Endpoint: GET /api/v1/foobars

Details of the API's it depends on.

json
{
  "foo": "bar",
}
```
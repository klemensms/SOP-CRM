**Release Overview**

| Environment | Status & Date | Comment                             |
| ----------- | ------------ | ----------------------------------- |
| MERGE       | [pending]       | Tested with a non-admin account: No |
| Integration | [pending]       |                                     |
| QA          | [pending]       |                                     |
| QA2         | [pending]       |                                     |
| PreProd     | [pending]       |                                     |
| PROD        | [pending]       |                                     |

**Client Requirement**


![google ](www.google.com)
Consider: treat "existing/old" data/records differently?

**Process diagrams** (optional)

**Assumptions** (optional)

**Proposed Technical Approach**



New Entity:

- create entity
- add fields
  - "Updated by process" (text, 4000)
  - Reference Data fields (start date, end date, code)
  - Data migration: externalkey
- customise main form
  - customise form of entities being looked up to (add sub-grid there)
  - re-name the relationship link for lookups on target entities
- customise quick create form
- enable quick create form (entity level)
- customise all views (include relevant system fields such as created/modified on/by, owner and status/reason)
- add entity to Model Driven App(s)
- update sitemap
- add business rules
- add workflows (see SOP for workflows)
- update relationship types (e.g. parental)
  - add fields mappings
- Icon (https://www.notion.so/Icons-for-custom-entities-dee8d261e34a441caaacc6670bd35435)



If Reference Data entity:

- import instructions, source data and mapping - link to user story



**How to test**

Test instructions:

**Deployment Checklist** (optional)

**Documentation Link** (optional)
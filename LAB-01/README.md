---

## Microsoft Entra ID — Administrative Units and Delegated Administration

### Objective

Create an administrative unit to organize IT-related identities and configure delegated administration using Microsoft Entra ID role assignments.

### Configuration

| Setting | Value |
|---|---|
| Administrative unit | `AU-IT` |
| Description | IT administrative unit for MD-102 delegated administration labs |
| Restricted management | No |
| Member | `Lab User1` |
| Assigned role | Helpdesk Administrator |
| Role assignment scope displayed | This resource |

### Implementation steps

1. Created the `AU-IT` administrative unit in Microsoft Entra ID.
2. Added `Lab User1` as a member of the administrative unit.
3. Opened `AU-IT` → **Roles and administrators**.
4. Selected the **Helpdesk Administrator** role.
5. Assigned the role to `Lab User1`.
6. Verified that `Lab User1` appeared in the role assignments table.

### Evidence checklist

- [ ] Screenshot of the `AU-IT` administrative unit properties.
- [ ] Screenshot showing `Lab User1` in the administrative unit's Users list.
- [ ] Screenshot showing `Lab User1` in the Helpdesk Administrator assignments table.

### Outcome

The administrative unit was created, `Lab User1` was added as a member, and the Helpdesk Administrator role assignment was completed through the administrative unit's role management page.

**Validation note:** The assignment table displayed `This resource` in the Scope column. Retain a screenshot of the assignment page as evidence of the configuration.

### Skills demonstrated

- Microsoft Entra ID administrative unit management
- User membership management
- Role-based access control (RBAC)
- Delegated administration
- Identity and access management documentation

---

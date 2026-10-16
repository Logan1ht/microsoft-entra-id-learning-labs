# Lab 002 — Microsoft Entra ID Security Group Management

**Status:** Assigned-group lab completed; dynamic membership studied but not configured  
**Platform:** Microsoft Entra admin center  
**Learning path:** SC-300 — Microsoft Identity and Access Administrator  
**Lab type:** Guided hands-on practice and conceptual study based on Waleed Mir's SC-300 group-management lesson

## Objective
Create and manage an assigned Microsoft Entra ID security group, practice adding and removing members, and understand how dynamic group membership rules automate membership.

## Environment
- Personal Microsoft Entra ID lab tenant
- Microsoft Entra admin center: https://entra.microsoft.com
- Test security group: `identity admin`
- Membership type: **Assigned**

## Hands-on work completed

### 1. Create an assigned security group
1. Navigate to **Entra ID → Groups → All groups → New group**.
2. Select **Group type: Security** and **Membership type: Assigned**.
3. Name the group `identity admin` and add a descriptive purpose.
4. Create the group and confirm it appears in **All groups**.

### 2. Inspect group properties
Open the group overview and verify its cloud source, Security group type, and Assigned membership type. The group initially had no members.

### 3. Add group members
1. Open **Members → Add members**.
2. Select three identities: two user accounts and one service principal.
3. Confirm the membership list shows three direct members.

### 4. Remove group members
1. Select two members and choose **Remove**.
2. Confirm the removal.
3. Verify that one test user remains in the group's direct membership list.

**Evidence:** Screenshots of group creation, overview, member selection, the three-member list, removal confirmation, and final one-member list were captured during the lab. Upload sanitized images to a `screenshots/` folder and link them here.

## Dynamic membership — concepts studied, not implemented

The SC-300 lesson also covered **Dynamic User** and **Dynamic Device** security groups. Unlike an assigned group, whose members are managed manually, a dynamic group evaluates membership rules and automatically includes matching users or devices.

I studied how rules use user attributes such as **job title**, **department**, and **company name**, including:

- `-startsWith` to match a prefix, such as job titles beginning with `Dev`.
- `-eq` and `-ne` for equality and inequality.
- `-and` to require **both** conditions.
- `-or` to include identities when **either** condition matches.
- Parentheses to make complex rule logic explicit.

**Illustrative rule from the tutorial concepts (not deployed):**

```text
(user.jobTitle -startsWith "Dev") -and (user.department -eq "DevOps")
```

This rule would match users whose job title starts with `Dev` **and** whose department is `DevOps`. The lesson also demonstrated that adding broad `-or` conditions can unintentionally expand membership, so rule logic must be reviewed carefully.

### Access limitation and troubleshooting
I attempted to use **Dynamic User → Add dynamic query**, but the portal returned a **401 / You don't have access** message. My lab tenant did not have the premium licensing/access required for this exercise, so **no dynamic membership rule or dynamic group was successfully configured or tested**. I continued with the supported **Assigned** membership workflow instead.

## IAM and security takeaways
- **Security groups** can organize identities for resource access and access administration.
- **Microsoft 365 groups** are designed around collaboration scenarios.
- **Assigned membership** requires explicit additions and removals; **dynamic membership** evaluates attribute-based rules.
- **Group ownership** can delegate management of a group without granting broad tenant administration rights.
- **Least privilege:** A group's name does not grant administrative permissions. A group called `identity admin` is not inherently a privileged role-assignable group.
- **Group nesting:** Security-group nesting has restrictions, particularly for dynamic and role-assignable groups; nested memberships should not be assumed to grant access in every application or role scenario.

## Results
- Created and verified an assigned Security group.
- Added three direct members, including users and a service principal.
- Removed two members and verified one user remained.
- Learned the purpose and syntax of dynamic membership rules, but did **not** implement dynamic membership due to tenant access/licensing limitations.

## Reference
Waleed Mir — SC-300 Microsoft Identity and Access Administrator video training, group management lesson.

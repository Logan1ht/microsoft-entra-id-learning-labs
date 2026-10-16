# Lab 001 — Microsoft Entra ID User Lifecycle Management

**Status:** Completed hands-on lab  
**Platform:** Microsoft Entra admin center  
**Learning path:** SC-300 — Microsoft Identity and Access Administrator  
**Lab type:** Guided practice based on Waleed Mir's SC-300 video training

## Objective
Practice the core lifecycle of a cloud identity: create a member account, inspect its properties, delete it, locate it in Deleted users, and restore it.

## Environment
- Microsoft Entra ID tenant (lab environment)
- Entra admin center: https://entra.microsoft.com
- Fictional test account: `TravisChaffen`
- Personal tenant identifiers, account UPNs, and object IDs are redacted in evidence.

## Work performed

### 1. Create a user
1. Open **Entra ID → Users → New user → Create new user**.
2. Enter a user principal name (UPN), display name, and password configuration.
3. Review the **Account enabled** setting.
4. Create the test user.

**Evidence — New user creation form**

![Microsoft Entra ID Create new user form with identity, password, and account enabled fields](screenshots/423b0ef2-059d-453a-b3e5-78c9626f6674.png)

*The screenshot shows the account creation interface; successful creation is verified in the next section.*

### 2. Verify the account
1. Find the newly created account under **All users**.
2. Open its profile.
3. Verify **User type: Member** and **Account status: Enabled**.

**Evidence — Created user profile**

![Created member user profile showing enabled status](screenshots/63315200-4112-41a3-afc4-d45dd9223657.png)

### 3. Select and delete the account
1. Return to **All users**.
2. Select the test account.
3. Use **Delete** to remove the account.

**Evidence — User selected for deletion**

![Selected user in All users with Delete action visible](screenshots/5e349eca-23b7-48c6-b3aa-c7462990f413.png)

### 4. Inspect Deleted users
1. Open **Users → Deleted users**.
2. Locate the deleted test account.
3. Observe the available **Restore users** and **Delete permanently** actions.

In this lab, the portal indicated that deleted users are automatically permanently deleted after **30 days**.

**Evidence — Deleted user and recovery options**

![Deleted user listed with Restore users and Delete permanently actions](screenshots/687417d2-040a-46c5-9262-eb4c30ea071b.png)

### 5. Restore and verify
1. Select the deleted test account and choose **Restore users**.
2. Confirm the restoration.
3. Return to **All users** and verify the account is listed again.

**Evidence — Restore confirmation**

![Restore user confirmation dialog](screenshots/b2bbe1b3-f1c8-4a58-8b0e-4873d88ceca1.png)

**Evidence — Restored user verified in All users**

![Restored user visible in All users](screenshots/b3de9713-6ecb-41cf-a275-1ceb64d087a0.png)

## Results
- Created and inspected a Microsoft Entra ID member user.
- Deleted the test account and located it under **Deleted users**.
- Restored the account and verified its return to **All users**.

## IAM and security takeaways
- **UPN:** Identifies an account for sign-in; its domain suffix is supplied by the tenant's configured domains.
- **Account status:** Disabling an account is distinct from deleting it.
- **Lifecycle management:** Provisioning, deprovisioning, and restoration are routine IAM administration tasks.
- **Recovery:** Soft deletion offers a limited window to recover an accidentally removed account; permanent deletion is different.
- **Evidence hygiene:** Public portfolio screenshots should not expose passwords, access tokens, personal addresses, or unnecessary tenant identifiers.

## Scope and limitations
This lab demonstrates basic user lifecycle operations. It does **not** demonstrate MFA enforcement, role assignments, group-based licensing, Conditional Access, automated provisioning, or privileged identity governance. Those topics belong in later labs.

## Reference
Waleed Mir — SC-300 Microsoft Identity and Access Administrator video training, user management lesson. This is a guided learning exercise, not an independently designed production deployment.

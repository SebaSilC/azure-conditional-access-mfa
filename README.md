## Microsoft Entra ID Conditional Access & MFA Lab

Implementation of a secure Microsoft Entra ID environment by enforcing Multi-Factor Authentication (MFA) through Conditional Access policies for group-based identity protection. Demonstrates Zero Trust, risk reduction, and modern identity management in Azure.

---

## Table of Contents

- [Overview]
- [Real-World Risk]
- [What I Built]
- [Diagram]
- [Objectives]
- [Steps Performed]
  - [1. User and Group Creation]
  - [2. Conditional Access Policy]
  - [3. Testing and Verification]
  - [4. Cleanup]
- [Screenshots]
- [Lessons Learned]
- [References]

---

## Overview

This lab demonstrates how to protect cloud identities in Microsoft Azure using Conditional Access and Multi-Factor Authentication (MFA). The setup ensures only authorized users, from a specific group, can access cloud resources—and only after passing MFA. This reflects real-world security practice, following the Zero Trust model to defend against credential compromise.

---

## Real-World Risk

Most security breaches are caused by compromised user credentials. Attackers use phishing, credential stuffing, or brute force attacks to gain unauthorized access to cloud services. Without strong authentication and context-based access control, even a single leaked password can give an attacker access to sensitive data or critical infrastructure.
By using Conditional Access with Multi-Factor Authentication (MFA) in Azure, organizations drastically reduce the risk of unauthorized access—helping to prevent data breaches, account takeover, and privilege escalation.

---

## What I Built

- Microsoft Entra ID users (Alice and Bob) and a dedicated security group (MFA-Required-Users)
- A Conditional Access policy targeting the group, requiring MFA for all sign-ins to cloud apps.
- Enforced group-based identity protection following Zero Trust security principles.
- Full test flow: user login, MFA prompt enforced, access granted only after successful verification.
- Screenshots, documentation, and an architecture diagram for recruiter and technical review.

---

## Diagram

![Architecture Diagram](diagram.png)

---

## Objectives

- Create Microsoft Entra ID users and assign them to security groups.
- Deploy a Conditional Access policy that enforces MFA for group members.
- Test and validate that only group members are prompted for MFA.
- Document each step for technical and recruiter review.

---

## Steps Performed

1. User and Group Creation
   - Created two test users:
     - alice@azurelabstest.onmicrosoft.com
     - bob@azurelabstest.onmicrosoft.com
   - Created a security group MFA-Required-Users and assigned Alice and Bob as members.

2. Conditional Access Policy
   - Navigated to Microsoft Entra ID → Security → Conditional Access.
   - Created a policy Require MFA for MFA-Required-Users.
   - Targeted the MFA-Required-Users group.
   - Applied to All cloud apps.
   - Access control set to Require multi-factor authentication.
   - Enabled the policy.
   - Disabled Security Defaults to allow custom policies.

3. Testing and Verification
   - Signed in as Alice Demo from a private browser.
   - Verified the Conditional Access policy triggered an MFA prompt at login.
   - Completed the registration for MFA (Authenticator app/SMS).
   - Verified successful login post-MFA.
   - Checked Microsoft Entra ID Sign-in logs to confirm Conditional Access and MFA enforcement.

4. Cleanup
   - Go to Microsoft Entra ID > Users: Delete Alice and Bob.
   - Go to Groups: Delete the MFA-Required-Users group.
   - Microsoft Entra ID > Security > Conditional Access: Delete the policy you created.
   - Microsoft Entra ID > Users > Per-user MFA: Disable MFA for test users before deleting.
   - Remove any Key Vaults, VMs or other resources created for this lab.
   - Use the Resource groups blade for fast bulk cleanup.

---

## Screenshots

*All screenshots are included in the screenshots/ folder.

| Step | Filename                      | Description                                                   |
| ---- | ----------------------------- | ------------------------------------------------------------- |
| 1    | users-list.png                | Microsoft Entra ID user table with Alice and Bob created.     |
| 2    | group-members.png             | MFA-Required-Users group with Alice and Bob as members.       |
| 3    | conditional-access-policy.png | Conditional Access policy configured to require MFA for group.|
| 4    | per-user-mfa-enabled.png      | Per-user MFA enabled for Alice and Bob (legacy approach)      |
| 5    | mfa-prompt.png                | MFA prompt shown to Alice/Bob on sign-in (policy tested)      |

## Screenshot Explanations

1. users-list.png: Shows the Microsoft Entra ID “Users” list with Alice and Bob created for the lab.

2. group-members.png: MFA-Required-Users group membership, displaying Alice and Bob as assigned members.

3. conditional-access-policy.png: Conditional Access policy summary, configured to require MFA for the group, and policy set to “On.”

4. per-user-mfa-enabled.png: Microsoft Entra ID’s per-user MFA settings, showing MFA enabled for Alice and Bob (legacy feature)

5. mfa-prompt.png: The actual MFA registration prompt that appears for Alice/Bob at sign-in, proving the policy is enforced.

---

## Lessons Learned

- Conditional Access is the enterprise-ready way to enforce context-driven MFA in Azure—more flexible and secure than per-user MFA alone.
- Group-based policies allow for granular, scalable identity security.
- Documentation (screenshots, diagrams) is essential for proving security posture to technical and non-technical audiences.
- Microsoft Entra ID’s sign-in logs are powerful for verifying policy effectiveness and for audit trails.

---

## References

- Conditional Access in Microsoft Entra ID
(https://learn.microsoft.com/en-us/entra/identity/conditional-access/)

- Enable per-user MFA in Microsoft Entra ID
(https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa)

- Zero Trust Security Principles: Microsoft Zero Trust Guidance
(https://www.microsoft.com/en-us/security/business/zero-trust)

---

Sebastian Silva C. – July, 2025 – Berlin, Germany.

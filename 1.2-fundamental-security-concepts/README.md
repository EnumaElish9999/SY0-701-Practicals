**CompTIA Security+ SY0-701 – Exam Objective 1.2**
**Source videos:** Professor Messer – The CIA Triad; Non-repudiation; Authentication, Authorization, and Accounting

## What This Covers

Three properties every security control is ultimately protecting:

| Property | What it means |
|---|---|
| Confidentiality | Keeping information away from anyone who shouldn't see it |
| Integrity | Making sure data hasn't been changed, by accident or on purpose |
| Availability | Making sure systems and data stay accessible when needed |

Common ways each one gets achieved:
- **Confidentiality** – encryption, access controls, extra authentication factors
- **Integrity** – hashing, digital signatures, certificates
- **Availability** – redundancy/fault tolerance, patching, monitoring

### Non-repudiation

Non-repudiation means someone can't credibly deny they sent something — the digital version of a signature on a contract. It's built from two things working together:
- **Proof of integrity** – a hash confirms the data wasn't changed
- **Proof of origin** – a digital signature (a hash encrypted with a private key) confirms who sent it

Combine both and anyone holding the sender's public key — not just the two people involved — can check both at once: that the data is untouched, and who it came from.

### Authentication, Authorization, and Accounting (AAA)

Four steps happen every time someone logs in:

| Step | Question it answers | Example |
|---|---|---|
| Identification | Who are you claiming to be? | Typing a username |
| Authentication | Can you prove it? | Password, plus extra factors like an MFA code |
| Authorization | What are you allowed to do? | Finance group members can open the Finance share |
| Accounting | What did you do? | Logs of login/logout times and data sent or received |

Only the last three are in the AAA name. Identification is the claim; authentication is the proof.

**Central AAA server.** Network devices like a VPN concentrator or firewall don't keep usernames and passwords themselves. They pass the login to a central AAA server, which checks the credentials and replies approve or deny. The device then lets the user in (or not). This keeps all credential checking in one place.

**Authenticating devices.** A laptop can't type a password, and you don't want passwords stored on devices out in the field. Instead, a Certificate Authority (CA) issues the device a certificate and digitally signs it. At login, the certificate is checked against the CA's signature. If it's valid, the device is confirmed as a company device. The CA's own certificate is signed by a root CA above it.

**Authorization models.** Giving every user their own permissions on every resource doesn't scale. An authorization model adds a layer in the middle — usually roles, groups or attributes — so you grant access to the group once, then just add or remove people. Adding a new starter to the Finance group gives them everything Finance needs in one step. The detailed models come later, in section 4.6.

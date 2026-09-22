# 1.2 – The CIA Triad

**CompTIA Security+ SY0-701 – Exam Objective 1.2**
**Source video:** Professor Messer – The CIA Triad

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

# 1.2 – Fundamental Security Concepts

**CompTIA Security+ SY0-701 – Exam Objective 1.2**
**Source videos:** Professor Messer – The CIA Triad; Professor Messer – Non-repudiation

## What This Covers

Three properties every security control is ultimately protecting:

| Property | What it means |
|---|---|
| Confidentiality | Keeping information away from anyone who shouldn't see it |
| Integrity | Making sure data hasn't been changed, by accident or on purpose |
| Availability | Making sure systems and data stay accessible when needed |

### Non-repudiation

Non-repudiation means someone can't credibly deny they sent something — the digital version of a signature on a contract. It's built from two things working together:
- **Proof of integrity** – a hash confirms the data wasn't changed
- **Proof of origin** – a digital signature (a hash encrypted with a private key) confirms who sent it

Combine both and anyone holding the sender's public key — not just the two people involved — can check both at once: that the data is untouched, and who it came from.

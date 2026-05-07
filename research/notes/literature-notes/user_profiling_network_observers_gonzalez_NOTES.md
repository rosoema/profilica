# Notes - User Profiling by Network Observers

## Core concept
Check if network observers (ISPs/VPNs) can profile users despite TLS encryption.

### Why
- Most defenses target trackers/ad networks
- But network observers still see hostnames
- Unknown how much this reveals about users

### Questions
1. Can profiles be built using only hostnames?
2. How accurate are they vs ad-network profiles?

### Challenges
- Hostnames alone are weak signals
- Ontology problem:
  - Domain → category mappings (e.g., Google Adwords)
  - But:
    - Limited coverage of the web
    - Many domains (CDNs, APIs) are hard to classify

### Approach
- Use a neural network to:
  - Learn relationships between hostnames
  - Group similar domains based on user browsing patterns
- Then:
  - Assign categories using ontology where possible
  - Extend to uncategorized domains via learned similarities

### Setup
- 1329 users
- 17 countries
- 1 month experiment
- Chrome extension:
  - Collects hostnames only
  - Replaces ads to test profiling quality

### Metric
- CTR (Click-Through Rate) used as proxy for profile accuracy

---
# Meaningful insights

## Related Work

### How tracking/profiling normally works
Most systems:
- track users using:
  - cookies
  - fingerprinting
- Share data between companies (cookie-synching)

> *The authors observe that sharing harvested data among* 
> *tracking entities for user profiling purposes is the norm.*

> *Tracking behavior of more than 950K mobile apps shows that* 
> *applications related to news and children are among the most privacy-invasive ones.*

### Question
> *Traditional user profiling relies on large amounts of data.*
> *What can be inferred using only minimal information, such as hostnames?*

---

## Background

### Not all ads are the same
- **Premium** (served to all users visiting a given website within a time-frame) vs. **programmatic** ads (served by taking into account the profile, based on recent browsing history, demographic, or topic of the website)

---

## User profiling using hostnames
- Treat hostnames like words in a sentence
- Words gain meaning from surrounding words
- Hostnames gain meaning from surrounding hostnames

> *(If domains frequently appear together in browsing sessions,*
> *they are likely semantically related.)*

### Key
Instead of understanding website content directly,
the system learns relationships between domains from browsing patterns.

---

## Relevant ad selection
- Model retrained daily, using hostname sequences from the previous day
- Profiles built from the last 20 minutes of browsing activity

> *This value was empirically tested as a good trade-off between very short*
> *sessions that may led to non meaningful profiles and very long ones*
> *that may include topics that are not relevant anymore for the user.*

---

## User diversity
- Common hostnames are separated as background noise
- Certaing categories and hostnames do not offer a profiling value

> *If all users visit the same set of hostnames, then*
> *browsing habit is probably not a good discriminant for user interests.*

---

## CTR

> *Ads served by our system show a*
> *CTR of 0.217% whereas ads served by ad-networks have a CTR of*
> *0.168%.*






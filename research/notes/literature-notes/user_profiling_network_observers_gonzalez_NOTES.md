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

## Related Work — Meaningful insights

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
> Traditional user profiling relies on large amounts of data.
> What can be inferred using only minimal information, such as hostnames?






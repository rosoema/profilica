# Notes - User Profiling Trends, Techniques and Applications

## Core
Explores how user profiling enables personalization, especially in recommender systems.

User profiling is defined as:
> The process of identifying and collecting information about a user’s interests, preferences,
> behaviors, and characteristics so systems can personalize responses or recommendations.

The paper surveys:
1. Trends in user profiling
2. Techniques used for profiling
3. Applications of profiling systems

## UDD (User Data Discovery) vs KDD (Knowledge Discovery in Databases)
### KDD
- Starts with large datasets
- Extracts hidden knowledge

### UDD
- Starts with very little user data
- Learns incrementally over time
- Continuously updates user understanding

| Older Systems | Modern Systems |
|---|---|
| Explicitly ask users for data | Infer data from behavior |
| Forms and surveys | Activity tracking |
| Static profiles | Dynamic/adaptive profiles |
| Low personalization | Continuous learning |

## Main Types of User Profiling
1. Explicit
- Information intentionally provided by the user (e.g., filling out a "favorite genres" form, rating a product 5 stars).
- Pros: High accuracy, clear intent, easy to interpret, explicit consent.
- Cons: Users often do not fill them out (sparse data), they may become outdated, and require user effort.
- Use Cases: Initial onboarding, user surveys, preference centers.

2. Implicit
-  Information gathered indirectly by observing user behavior (e.g., pages visited, purchase history, search queries, time spent on content).
- Pros: High volume, continuous updates, no user effort required (frictionless), reflects actual behavior rather than stated intentions.
- Cons: Harder to interpret (a click does not always mean a "like"), can be noisy, privacy concerns if not managed well.
- Use Cases: Recommendation engines (e.g., Netflix/Amazon), ad targeting, personalizing user experience.

3. Hybrid
- Merges user-item ratings (explicit) with behavior logs (implicit).
- Pros: Balances high-quality data with high-volume data, alleviates cold start problems, and improves recommendation quality.
- Cons: Higher complexity in implementation.
- Use Case: A retail site that uses a user's wish list (explicit) plus their recent browsing activity (implicit) to send personalized marketing emails. 

## Techniques
### Profile extraction
- Extracting the useful information about a user from different sources (web, social media, online behaviour, mouse movements, navigation patterns, etc.).
- SVM (Support Vector Machines) used for finding relevant pages, classifying profile-related content.

### Profile integration
- Clean and merge extracted profile data.

### Interest discovery
- After some filtering, grouping, etc., infer user interests after data collection.
- Filtering techniques:
   - Content-based
      - Recommend items similar to content the user already liked.
      - Build profile, compare new content to profile.
      - If user reads a lot of Y, recommend similar Y.
   - Collaborative
      - Users with similar behavior likely share future preferences.
      - Cluster similar users, recommend items liked by peers.
   - Demographic
      - Uses demographic features (age, location, gender, education) to infer preferences.
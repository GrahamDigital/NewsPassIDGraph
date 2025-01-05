**White Paper: Privacy-Centric Publisher-Owned Identity Graph**

### Executive Summary
In an era of increasing privacy regulations and heightened consumer awareness around data use, publishers are uniquely positioned to redefine the digital advertising ecosystem. The relationship between publishers and their audiences provides more reliable information about consumers, particularly in environments where third-party cookies are not available. While scale drove the proliferation of third-party cookies, this white paper introduces a **Publisher-Owned Identity Graph** to provide high-quality audience signals. This includes attribution for buyers to optimize their media spend and allows publishers to leverage their first-party data in new ways. For smaller publishers, this solution delivers the confidence of direct buys at programmatic scale, empowering them to compete effectively in the modern advertising landscape.

---

### Introduction
The deprecation of third-party cookies and evolving privacy regulations have underscored the need for new, privacy-respecting approaches to identity resolution in digital advertising. Traditional identity graphs, often dominated by walled gardens and third-party solutions, lack transparency and limit publishers’ ability to fully leverage their valuable first-party data. A publisher-owned identity graph offers an opportunity to reshape the ecosystem, providing an open yet privacy-centric alternative that empowers all stakeholders.

The success of Dotdash Meredith’s D/Cipher cookieless targeting tool exemplifies the potential of publisher-owned audience graphs. D/Cipher’s ability to leverage first-party data has resulted in a 12% year-over-year increase in digital ad revenue and improved targeting outcomes for over 150 brands. Such innovations highlight the power of first-party identifiers in achieving superior campaign performance and advertiser confidence, particularly in environments where third-party cookies are no longer viable. By adopting similar models, publishers can offer high-quality audience signals, ensure durable attribution, and collaborate at scale to meet advertiser demands.

---

### Key Features and Principles

#### Expanding the NewsPassID Ecosystem
The growth of the NewsPassID ecosystem offers a powerful model for publisher collaboration and audience monetization. Through initiatives such as the Local Media Consortium’s local news taxonomy and private marketplace (PMP) segmentation, publishers can better assist advertisers in targeting high-value audiences while ensuring brand safety and privacy compliance. According to [PRNewswire](https://www.prnewswire.com/news-releases/lmcs-newspassid-ad-network-releases-new-solutions-to-streamline-local-news-advertising-buys-302215346.html), NewsPassID’s reach spans more than 5,000 media outlets, delivering 200 million unique visitors per month and generating significant ad revenue.

NewsPassID also empowers publishers of varying sophistication levels to engage with their audiences more effectively. Features like local news supply path optimization and partnerships with digital technology providers enable advertisers to invest more efficiently and publishers to receive a larger share of ad spend. For example, NewsPassID’s initiatives have led to revenue gains equivalent to hiring 130 additional journalists, demonstrating its impact on the local news landscape.

#### Real-World Success: Dotdash Meredith’s D/Cipher, ProNews Collective, and Other First-Party Data Initiatives

The Dotdash Meredith example underscores the effectiveness of publisher-owned identity solutions. Sources such as [Adweek](https://www.adweek.com/media/dotdash-meredith-dcipher-digital-advertising/) and [PRNewswire](https://www.prnewswire.com/news-releases/dotdash-meredith-launches-dcipher-a-transformative-intent-targeting-tool-for-advertising-301826071.html) provide detailed insights into its success, including a 12% year-over-year increase in digital ad revenue. With over 30% of its direct campaigns running through its D/Cipher tool, the publisher has demonstrated how first-party data can drive performance. Integrating these capabilities with major platforms, such as Amazon Publisher Cloud and Google, further showcases how publishers can scale their data for programmatic efficiency while maintaining control and privacy.

Similarly, the ProNews Collective initiative by Prohaska Consulting highlights the power of collaboration among quality news publishers. According to [Prohaska Consulting](https://prohaskaconsulting.com/introducing-pronews-collective-powered-exclusively-by-index-exchange/) and [AdExchanger](https://www.adexchanger.com/publishers/news-publishers-are-banding-together-to-beat-brand-safety-blocking/), this initiative provides curated inventory, reduces blocked news content, and boosts revenue for participating publishers. By curating inventory and providing advertisers a brand-safe environment, ProNews Collective leverages first-party data and reduces blocked news content while boosting fill rates and revenue. This partnership-based approach demonstrates how publishers can achieve scale and optimize ad performance without compromising privacy or quality.

Other notable first-party data implementations include:

- **Penske Media Corporation’s ATLAS**: A data studio combining contextual, behavioral, proprietary, and enriched first-party data, enabling precision audience targeting across 100% of their audience. They achieved a 5X increase in CTR for first-party-based campaigns ([Xenoss](https://xenoss.io/blog/first-party-data-strategy-everything-media-owners-should-know-in-2024)).
- **Media Impact’s First-Party Strategy**: Leveraging a first-party data partnership with 1plusX, Media Impact doubled CPMs for targeted campaigns and created over 300 interest and intent segments ([1plusX Case Study](https://www.1plusx.com/1plusx-case-studies/media-impact-case-study)).
- **PreBid.org and IAB’s Seller Defined Audiences (SDA)**: Industry-wide initiatives like PreBid.org facilitate publishers passing first-party data to bidders, while SDA enables leveraging first-party data for privacy-compliant programmatic advertising ([AdExchanger](https://www.adexchanger.com/the-sell-sider/how-to-solve-for-scalability-of-publisher-first-party-data/)).

These cases collectively demonstrate how first-party data strategies can transform audience targeting and programmatic advertising by enriching bidstream data with high-quality, privacy-compliant audience insights.

---

### Technical Specifications

#### Publisher Side Implementation

##### Phase 1: First-Party Identifier Creation
- **Identifier Generation:** Publishers can use an existing ID they have or generate a new one via a provided script.
- **Namespace Management:** Each ID is placed in a unique namespace to prevent conflicts across publishers.
- **Salting and Encryption:** The ID is salted and encrypted before being transferred to a shared publisher database. This ensures the ID remains unique to the publisher and secure.
- **Cross-Platform Utility:** Publishers can use this ID across platforms for tasks like frequency capping.

##### Phase 2: Data Enhancement
- **Deterministic Data:** Data unique to a user that can be used for identification purposes (e.g., login information) is securely stored. The following diagram illustrates how deterministic data integrates into the publisher ID infrastructure, ensuring secure storage and enhanced functionality while preserving privacy:

![Deterministic Data Flow](audience_creation_flow.png)
- **Non-Deterministic Data:** Includes signals like content engagement, intent, or other behavioral insights that can inform ad targeting but do not identify the user uniquely.
- **Database Structure:**
  - **ID Database:** Contains the shared IDs managed across publishers.
  - **Data Database:** Maintained separately by each publisher and secured by NewsPassID. While each publisher retains ownership of their data, NewsPassID ensures its security. The database contains both deterministic and non-deterministic data, which can be merged with the ID database and other publisher information to create enriched audience segments.
- **Data Ownership:** Publishers maintain ownership of their data, ensuring compliance with privacy regulations and enabling custom audience creation for marketing and personalization.

##### Phase 3: Audience Creation and Activation
- **Clean Room Integration:** Audiences are created through clean room lookups that group IDs into defined segments. This ensures data privacy and security during audience creation.
- **Prebid Integration:** Audiences can be activated by passing values through the publisher’s prebid setup. The system uses a Prebid identity module that:
  - Integrates directly into existing prebid configurations.
  - Enables mapping of audience IDs to prebid requests without exposing raw data.
  - Leverages consented and anonymized data for targeting ads within programmatic workflows.
- **Technical Requirements for the Prebid Module:**
  - **JavaScript SDK:** To integrate the identity graph with the publisher’s site.
  - **APIs for Audience Sync:** Secure endpoints for syncing audience data between the clean room and the prebid module.
  - **Real-Time Bidding Support:** Ensures compatibility with RTB environments, maintaining low latency and high throughput.
  - **Compliance Checks:** Built-in mechanisms to validate consent and enforce privacy regulations.

---

### Use Cases

#### 1. **Audience Monetization**
Publishers can create custom audience segments based on their first-party data and offer these to buyers through the identity graph. For example, a local news outlet might create a segment for “Tech Enthusiasts in the Midwest,” available for programmatic targeting.

#### 2. **Cross-Publisher Collaboration**
Multiple publishers can collaborate to pool anonymized data, creating larger, richer datasets for buyers. This approach ensures compliance while achieving scale.

#### 3. **Agency Integration**
Agencies can integrate their identity graphs with the publisher-owned solution through clean room integration with the IDs and deterministic data or other shared identity graphs, enhancing their targeting capabilities with high-quality, localized audience data.

---

### Benefits

#### For Publishers:
- **Data Activation:** Unlock the value of first-party data.
- **Control Over Attribution:** IDs can be passed at the publisher level, enabling robust attribution reporting by connecting user publisher settings with buyer sessions. This ensures clear visibility into audience performance.
- **Durable Identifiers:** The IDs are durable and do not rely on cookies, providing a stable foundation for long-term audience management and targeting.
- **Increased Scale:** Collaborate with other publishers to achieve broader reach.
- **Enhanced Monetization:** Directly monetize audience data in a privacy-compliant way.

#### For Advertisers:
- **Better Targeting:** Access high-quality, localized data from trusted publishers.
- **Regulatory Compliance:** Ensure all targeting aligns with privacy regulations.

#### For Agencies:
- **Data Quality:** Work with transparent, high-quality publisher data.
- **Scalable Solutions:** Enhance existing identity graphs with valuable audience segments.

---

### Implementation Framework

#### Step 1: Publisher Onboarding
- Establish privacy protocols and ensure all participating publishers align with consent requirements.
- Provide technical tools for integrating first-party data.

#### Step 2: Graph Development
- Use advanced algorithms to anonymize and enrich data.
- Build scalable audience segments that can be seamlessly activated.

#### Step 3: Buyer Integration
- Develop APIs to enable integration with buy-side identity graphs.
- Provide interfaces for agencies and advertisers to access and purchase audiences.

#### Step 4: Continuous Optimization
- Regularly audit data usage for compliance.
- Iterate on graph capabilities to meet evolving market needs.

---

### Conclusion
The Publisher-Owned Identity Graph represents a transformative step toward a more transparent, privacy-respecting digital advertising ecosystem. By enabling publishers to activate their first-party data at scale, fostering collaboration with agencies, and integrating seamlessly with buy-side identity graphs, this solution addresses the needs of all stakeholders while adhering to the highest privacy standards.

Publishers, advertisers, and agencies are invited to join this initiative to build a more equitable and effective advertising future.

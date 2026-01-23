# Software-Construction-Group-Tech

# App Selection
App Selected: WhatsApp

# Part A: Understanding the App
  1. App Overview
  
(a) What problem does this app solve ?

WhatsApp was originally developed to address the problem of expensive and limited SMS-based communication, especially for users communicating across different networks and countries. Traditional messaging relied on telecom providers and incurred per-message costs.

As internet access expanded, the problem evolved into enabling fast and reliable real-time communication over the internet. WhatsApp provided messaging, media sharing, and calls without relying on SMS.

Today, WhatsApp solves the broader problem of secure, scalable, and low-cost global communication, ensuring reliable message delivery, privacy through end-to-end encryption, and consistent performance across billions of users and devices.


(b) Who are its primary users ?

(i) Individuals communicating with friends and family

(ii) Students and educations for coordination and collaboration

(iii) Businesses and organizations for customer engagement

(iv) Communities and groups requiring real-time communication

  2. Core Features:
      (i) Privacy and Security
      (ii) Calls (Voice and Video)
      (iii) Messaging






# Part B : Thinking Behind the Scenes
   
 Core Feature: (i) Privacy and Security
Privacy and security in WhatsApp are not “settings”; they are system-wide design decisions that affect almost every part of the application.
   
1. User Interface (UI)
- Privacy settings screens (last seen, profile photo visibility, read receipts, blocked contacts).
- Security indicators (end-to-end encryption notice).
- Two-step verification setup screens.
- Fingerprint / Face ID lock interfaces.
  
The UI allows users to control who can see what and provides feedback when security features are enabled.

2. Business Logic: This is where the real work happens.
- End-to-end encryption logic (message encryption before sending and decryption on receipt)
- Access control rules (who can view status, profile photo, last seen)
- Blocked user enforcement
- Two-step verification logic
- Device authentication and session management

The business logic ensures that privacy rules are enforced, not just displayed.

3. Network / APIs
- Secure key exchange mechanisms
- Encrypted message transmission
- Authentication with WhatsApp servers
- Certificate validation to prevent man-in-the-middle attacks

  Even though WhatsApp servers transmit messages, they cannot read message content because it is encrypted end-to-end.

4. Data Storage
- Encrypted message storage on the device
- Secure key storage (private keys never leave the device)
- Encrypted backups (if enabled)
- Metadata storage (timestamps, delivery status)


Sensitive data is either encrypted or minimized to reduce privacy risk.

Internet Connectivity Requirement: Yes, internet connectivity is required for:
- Key exchange
- Message delivery
- Security updates
- Authentication

However, encryption itself happens locally on the device, not on the server.

What Happens If the Network Is Slow or Unavailable?
- Messages are encrypted and queued locally
- Delivery is delayed until connectivity is restored
- Key verification may fail temporarily
- Security notifications (e.g., key changes) may not appear immediately

Importantly, security is not reduced due to poor network conditions — only delivery is affected.

Engineering Perspective (Why This Is Hard)
- Encryption must be fast enough to not slow down messaging
- Security features must work across billions of devices
- Any bug can compromise user trust globally
- Strong security must exist without hurting usability
This is why privacy and security are core architectural concerns, not add-ons.




**Key Feature: (iii) Messaging**

This feature involves sending and receiving of text, audios, images, videos, and documents.


**Software components likely involved;**

User Interface (UI): Chat screens, message input box, emoji and attachment buttons

Business Logic: Message formatting, delivery status (sent, delivered, read), encryption

Network/APIs: Message transmission via WhatsApp servers

Data Storage: Local message cache and cloud backups


**Whether the feature requires internet connectivity**

Yes, internet is required for sending and receiving messages.

**What might happen if the network is slow or unavailable**

Messages may remain unsent, show pending status, or be delivered late once connectivity is restored.

Core Feature: (iv) Search (Chat and Message Search)

Search is a core feature of WhatsApp that allows users to quickly locate messages, media, contacts, and group chats. It helps users retrieve past conversations without manually scrolling through long chat histories, improving usability and efficiency, especially for active users with many chats.

  1.User Interface (UI): 

  -Search bar available on the main chat screen and within individual chats 

  -Filters for narrowing results (e.g., messages, photos, videos, links) 
  
  -Highlighting of matched keywords in chat results 
  
  2.Business Logic: 

  -Handles indexing of messages and media metadata on the user’s device 

  -Processes search queries and ranks results based on relevance or recency 

  -Applies filters such as date, media type, or chat scope 
  
  3.Network / APIs: 

  -Not required for basic chat and message search 

  -Used when accessing AI-assisted search or web-based fact-checking features 
  
  4.Data Storage: 
  
  -Chat history and metadata stored in an encrypted local database on the device 

  -Search operations query this local storage to retrieve results 

Whether the feature requires internet connectivity

  -Basic search: Does not require internet connectivity

  -AI-assisted or web-based search: Requires an active internet connection

What might happen if the network is slow or unavailable

  -If the network is unavailable, users can still search messages, media, and contacts stored locally on their device

  -AI-assisted features and web-based searches will be disabled until connectivity is restored

  -For slow network, local search remains fast, but external search or AI responses may be delayed or fail to load

Core Feature: (v) Meta AI (AI-powered Assistance and Smart Features)

Meta AI is an artificial intelligence feature integrated into WhatsApp to assist users with tasks such as answering questions, generating text, summarizing chats, translating messages, and providing general information directly within the app. This feature enhances user experience by offering intelligent assistance without leaving WhatsApp.

Software components likely involved;

User Interface (UI):
- Meta AI chat interface within WhatsApp
- Input field for user prompts and questions
- Display area for AI-generated responses
- Option to copy, share, or insert AI responses into chats
- Indicators showing AI is processing a request

Business Logic:
- Prompt handling and validation
- Context processing to understand user input
- AI response generation using large language models
- Safety and content moderation logic to prevent harmful or inappropriate responses
- Rate limiting and usage control to prevent abuse
- Integration logic between WhatsApp chats and Meta AI services

Network / APIs:
- APIs to send user prompts to Meta AI servers
- AI inference APIs for generating responses
- Content filtering and moderation APIs
- Logging and monitoring APIs for performance and reliability

Data Storage:
- Temporary storage of user prompts and AI responses
- Metadata for usage analytics (timestamps, response times)
- Cached AI responses (where applicable)
- No permanent storage of private chat content for AI training

Whether the feature requires internet connectivity

Yes, Meta AI requires an active internet connection to:
- Send prompts to AI servers
- Generate responses
- Perform translations, summaries, and intelligent suggestions

What might happen if the network is slow or unavailable

- AI responses may take longer to appear
- Requests may fail or time out
- Meta AI features become unavailable when offline
- Users can continue using normal messaging features without AI assistance

# Part C: Change and Maintainability

Chosen Scenario: Add Mobile Payments in Uganda

**Which parts of the app would need changes?**

a) Chat Interface (UI)

Add a “Send Money” button inside chats (next to attachments).

New screens/prompts to show amount, recipient, and confirmation.

b) Backend / Server Systems

WhatsApp servers would need logic to:

- Start the USSD request

- Track transaction status (pending, successful, failed)

- Handle retries and errors

c) Security & Authentication

Extra security checks to prevent fraud

Verification that the sender and receiver are valid

Secure handling of PIN-related flows (even if WhatsApp doesn’t see the PIN)

d) Integration with Mobile Networks & Banks

Direct integration with:

- Telecom operators (for USSD)

- Banks or mobile money providers (MTN MoMo, Airtel Money, etc.)

Country-specific logic (since USSD codes differ)

e) Notifications & Receipts

Transaction confirmations in chat

Failure messages and transaction history

**What existing features could break?**

a) Messaging Flow

If USSD interrupts the app, chats may pause or reload.

Messages could fail to send when the app transitions from the foreground to the background.

b) App Performance

More background processes leads to slower chats on low-end phones.

Higher battery and data usage.

**Why would this change be difficult to implement?**

Implementing mobile payments in Uganda would be challenging due to several technical, regulatory, and user-experience constraints.

a) Limited Control over USSD Infrastructure

USSD-based mobile money services are controlled by telecom operators rather than application developers. As a result, WhatsApp would have limited influence over how USSD sessions behave. Additionally, USSD functionality varies across countries, mobile network operators, and device models, making consistent integration difficult.

b) Security and Trust Concerns

Mobile payments require extremely high levels of security to protect users from fraud and financial loss. Even a minor software flaw could lead to unauthorized transactions, resulting in financial damage, loss of user trust, and potential legal consequences for the platform.

c) Regulatory and Legal Constraints

Financial services are heavily regulated and differ from one country to another. To operate mobile payments in Uganda, WhatsApp would need approval and compliance with multiple regulatory bodies, including central banks, telecom regulators, and licensed payment service providers. Meeting these requirements increases development time and complexity.

d) Platform and Operating System Limitations

Some mobile operating systems, particularly iOS, restrict direct access to USSD functionality. In addition, not all devices allow applications to reliably initiate or manage USSD sessions, limiting compatibility across the user base.

e) User Experience Risks

Integrating USSD payments may require users to switch between WhatsApp and USSD interfaces, which can be confusing and disruptive. Failed or interrupted USSD sessions could reduce user confidence in the payment feature and negatively affect overall trust in the app.

# Part D: Software Construction Challenges — WhatsApp

1. Performance and Scalability: WhatsApp serves billions of users sending messages simultaneously.
Engineers must design systems that:
- Deliver messages in real time
- Handle massive traffic spikes (e.g., events, emergencies)
- Avoid server overload and message delays

A small performance issue can affect millions of users at once.

2. Security and Data Privacy
WhatsApp uses end-to-end encryption, meaning:
- Messages must be encrypted/decrypted on devices
- Keys must be securely generated and stored
- Servers must relay messages without reading them

Any security flaw can break user trust globally and expose private conversations.

3. Testing Across Devices and OS Versions
WhatsApp runs on:
- Thousands of Android device models
- Different iOS versions
- Devices with very different memory, CPU power, and screen sizes

A feature that works on a high-end phone may crash or freeze on a low-end device.

4. Backward Compatibility: Millions of users do not update their apps regularly.
New updates must still:
- Communicate correctly with older app versions
- Support older message formats and protocols
- Avoid breaking chats or media history

Engineers must maintain support for old behavior while adding new features.

5. AI Integration and Ethical Challenges: Integrating Meta AI into WhatsApp introduces new technical and ethical risks.
Engineers must ensure that AI features:
- Produce accurate and reliable responses
- Avoid bias, harmful content, or misinformation
- Respect user privacy and end-to-end encryption principles
- Comply with data protection and ethical AI regulations

AI systems also require high computational resources and continuous monitoring, making it challenging to maintain performance, scalability, and user trust while introducing intelligent features.

**Part E: Group Reflection**
1. What surprised your group most about the complexity behind this app?

Besides much of the invisible work that happens, behind what appears to be a simple action—sending a message. People/we tend to view WhatsApp as a basic text-sending application. 
However, as we analyzed it, we realized that each message passes through multiple layers of processing, including encryption, server-side message routing, secure storage, device synchronization, and handling unstable or slow network connections.
We were also surprised by how WhatsApp has evolved over time. What started as a low-cost alternative to SMS has adapted into a global communication platform capable of supporting billions of users, real-time messaging, media sharing, calls, and AI features, all while maintaining performance and security. 
This evolution highlights the app’s ability to adapt to changing technology, user needs, and network environments.


2. Why is writing “working code” not enough for software systems at this scale?
  - Code must survive scale, not just run correctly:
A feature that works for 100 users can collapse under millions of concurrent users. Engineers must think about performance, load handling, latency, and fault tolerance. “It works on my device” is meaningless if the system slows down or crashes under real-world traffic.

  - Code must be maintainable and evolvable by teams:
Large systems are built and modified by many engineers over years. If code is hard to read, tightly coupled, or poorly structured, every new change risks breaking existing functionality. Software at this scale must be written for future engineers, not just to pass today’s test.
         

3. What did you learn about teamwork from this exercise?

From the exercise, teamwork is important because different people had different experiences and perspectives of WhatsApp application which enabled us to notice different things. 
Working together helped us understand the app better, share ideas, and divide tasks so the work was done faster and more accurately.
More so, we learned that teamwork in software development is not just about dividing work, but about coordinating how everyone’s work fits together.
While working with branches and pull requests, changes without following the agreed rules, affected other people’s work. 
Also communication played an important role. Additionally, this exercise showed us that version control is not only a tool for saving code, but also a way for a team to work in an organized manner without causing conflicts.

# Group Contributions
**Name:** Tendo Calvin  
**Reg No:** S23B23/013  
**Access Number:** B24247  
Contributions: 
Core Feature worked on: Privacy And Security and answered Part B of the assignment based off the core feature I chose to work on. 
He also worked on Part D of the assignment where I briefly talked about the following engineering challenges: Performance and Scalability, Security and Data Privacy, Testing Across Devices and OS Versions & Backward Compatibility 
and attempted a question of part E of the assignment.

**Name:** Najjuma Teopista
**Reg No:** 
**Access Number:**  
Contributions:  
Serving as the App Analyst, she contributed to multiple sections of the project. In Part A (Question 2), she identified and analysed the app’s primary users. In Part B, she supported the identification of the app’s core features and also worked on the Calls (Voice and Video) feature, examining its software components, internet connectivity requirements, and behaviour under slow or unavailable network conditions. Additionally, she contributed to Part C: Change and Maintainability (Question 3) by analysing why the selected change would be difficult to implement.


**Name:** Ezamamti Ronald Austine 
**Reg No:** S23B23/018  
**Access Number:** B24252  
Contributions: 
Serving as the **Documentation Lead** for the group. He created and structured the GitHub repository, guided team members on proper use of branches, reviewed and merged pull requests from collaborators, resolved merge conflicts, and ensured that contributors regularly rebased their work with updates from the main branch to maintain consistency.
In terms of content contribution, he worked on Part A, Question 1 (What problem does the app solve?), analyzing the origins of WhatsApp, the motivation behind its development, and its evolution over time. 
He also handled the **Search** core feature, completing Part B by examining its software components, connectivity requirements, and behavior under network constraints. 
Additionally, he contributed to Part E, Question 1, reflecting on what surprised the group most about the complexity behind WhatsApp.


**Name:** Denzel [Surname]  
**Reg No:** 
**Access Number:**  
Contributions:  
He focused on the **Meta AI** core feature within WhatsApp. He analyzed how artificial intelligence is integrated into the application and contributed to **Part B** by examining the software components involved in AI-powered assistance, including user interaction, backend logic, network dependency, and privacy considerations.
In addition, he contributed to **Part D** by addressing **AI Integration and Ethical Challenges**. Through this analysis, he highlighted that integrating AI is not only about generating intelligent responses but also about responsibility. 
His contribution emphasized the need for strong moderation, ethical design, high-performance infrastructure, and strict privacy protection to ensure that AI features support users without causing harm, misuse, or misinformation.

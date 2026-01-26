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
      (ii) Calls
      (iii) Messaging 
      (iv) Search (Chat and Message Search)
      (v) Meta AI (AI-powered Assistance and Smart Features)




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


**Core Feature:(ii) Calls (Voice and Video)**

This feature allows users to communicate with one another in real time through voice and video calls using an internet connection, providing a cost-effective alternative to traditional phone calls.

**Software components likely involved;**

User Interface (UI):
It includes call screens that display the caller information, call duration, and connection status. It also provides interactive controls such as mute, speaker, camera toggle, and end-call buttons to allow users to manage the call easily.

Business Logic:
It is responsible for initiating and ending calls, managing call states (ringing, connected, ended), authenticating users, and dynamically adjusting audio and video quality based on available network conditions. It also ensures that calls are encrypted to maintain privacy.

Network / APIs:
WhatsApp Calls rely on internet-based communication protocols and APIs to establish call connections, handle signaling, and transmit voice and video data securely through WhatsApp servers.

Data Storage:
Only minimal data is stored, mainly call logs such as timestamps and contact details. The actual voice or video content is not stored, supporting end-to-end encryption and user privacy.

**Whether the feature requires internet connectivity**

Yes, an active internet connection, either through mobile data or Wi-Fi, is required for WhatsApp Calls to function.

**What might happen if the network is slow or unavailable**

If the network is slow, call quality may be reduced, resulting in delays, poor audio clarity, or interrupted video. If the network is unavailable, calls may fail to connect or may be disconnected unexpectedly.


Core Feature: (iii) Messaging

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

5. AI Integration and Ethical Challenges

Integrating Meta AI into WhatsApp introduces challenges related to accuracy, bias, and ethical use of artificial intelligence. Engineers must ensure that AI-generated responses are reliable, safe, and do not spread misinformation. In addition, AI systems require high computational resources and careful monitoring to maintain performance while respecting user privacy and data protection regulations.


Part E: Group Reflection
1. What surprised your group most about the complexity behind this app?
    What surprised our group most is how much invisible work happens just to send a simple message. As users, we thought WhatsApp only sends text from one phone to another. But when we analyzed it, we realized there are many things happening in the background like encryption, servers handling delivery, message storage, syncing across devices, and handling poor networks.


2. Why is writing “working code” not enough for software systems at this scale?
  - Code must survive scale, not just run correctly:
A feature that works for 100 users can collapse under millions of concurrent users. Engineers must think about performance, load handling, latency, and fault tolerance. “It works on my device” is meaningless if the system slows down or crashes under real-world traffic.

  - Code must be maintainable and evolvable by teams:
Large systems are built and modified by many engineers over years. If code is hard to read, tightly coupled, or poorly structured, every new change risks breaking existing functionality. Software at this scale must be written for future engineers, not just to pass today’s test.
         

3. What did you learn about teamwork from this exercise?

From this exercise, we learned that teamwork is important because different people have different experiences and perspectives of applications which enabled us to notice different things. Working together helped us understand the app better, share ideas, and divide tasks so the work was done faster and more accurately.
4. What did you personally learn from analyzing Meta AI in WhatsApp?

From analyzing Meta AI, I learned that adding artificial intelligence to an application is not just about smart answers, but also about responsibility. AI features require strong moderation, ethical considerations, high-performance infrastructure, and privacy protection. This helped me understand that intelligent systems must be carefully designed to support users without causing harm or misuse.




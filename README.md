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

Core feature (ii) Calls


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

# Software-Construction-Group-Tech

# App Selection
App Selected: WhatsApp

# Part A: Understanding the App
  1. App Overview
  (a) What problem does this app solve ?



(b) Who are its primary users ?

(i) Individuals communicating with friends and family
(ii) Students and educations for coordination and collaboration
(iii) Businesses and organizations for customer engagement
(iv) Communities and groups requiring real-time communication

  2. Core Features
      (i) Privacy and Security
      (ii) Calls
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

Core feature (ii) Calls

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
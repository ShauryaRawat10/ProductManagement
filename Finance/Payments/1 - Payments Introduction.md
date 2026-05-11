# Introduction to digital payments and Fintech Fundamentals

***
## Payments: Big Picture

- Fintech
  - Fintech means using tech to make financial services faster, easier and more efficient.
- E-Payments:
  - Transactions happening digitally. eg: card swipes, mobile taps
  - Make finnace more secure, convenient and accessible for everyone
  - Examples
    - POS terminal (Point of sales terminal): Swiping or tapping card at store checkout
    - Mobile wallet: Smartphone for in-store or online purchases (Apple pay, Google pay)
    - ATM Withdrawal: Accessing cash and making deposits digitally from bank account
    - Online shopping: Entering card details or using digital wallets for e-commerce transactions

### Digital Payments Ecosystem
- Issuer
  - The bank or financial institution that issues payment card to consumer (eg: your debit or credit card bank)
- Acquirer
  - The bank or financial institution that processes credit or debit card payments for merchants (eg: merchants bank)
- Network
  - Global payment system that facilitates transactions between issuers and aquirers (eg: VISA, Mastercard)
- Switch
  - A central system that routes transactions between various entities in payment network, ensuring data integrity and security
- Merchants
  - Business or individual selling goods or services that accepts electronic payments
 

### Benefots of digital payments
- Speed
  - Instant tarnsaction, no waiting for check to clear
- Security
  - Encryption and fraud detection protect your money
- Accessibility
  - Payments anywhere, anytime, to anyone with an internet connection
- Tracking
  - Easy record-tracking for personal and business finances

### Future trends in payments
- Decentralized Finance (DeFi)
  - Financial services built on blockchain, aiming for transparency and disintermediation
- Embedded Finance
  - Financial services seamlessly integrated into non-financial platforms, like buying insurance within a car app
- Payments in Metaverse
  - New digital currencies and payment methods for virtual economies and experiences
- Green payments
  - Focus on environmentally friendly payment solutions and carbon tracking

***
## Payment transaction lifecycle
4 stages
- Authorization
  - Validating funds and account status
  - Issuer validates money
- Authentication
  - Verifying cardholder's identity
  - cardholder verification
- Clearing
  - Exchanging transaction data and records (details to reconcile) between banks
  - Bank agreement, no actual money transfer
- Settlement
  - Final transfer of funds between financial institutions
  - Issuer to merchant's bank (Acquirer) 

### Card payment flow
- Customer (Initiates payment - swipe/tap)
- Merchant (Receives payment request)
- Acquirer (merchant's bank)
- Network (Visa, Mastercard)
- Issuer (approve/decline)
- Merchant (recieve response)

### Key concepts in payment
- Authorization hold
  - A temporary hold placed on funds by issuer to ensure payment availability
- Reversal
  - Canceling pending transaction before its settled
- Chargeback
  - A dispute initiated by cardholder, reversing transaction to merchant

### Why lifecycle matters
- Customer experience
  - Ensuring fast, secure and smooth transaction builds trust
- Merchant cash flow
  - Efficient processing impacts when merchants receive their funds
- Fraud detection
  - Each stage offers opportunity to identify and prevent fraudulent activities
- Complaince
  - Adhering to regulations (PCI DSS, GDPR) protects data and builds confidence

### Payment instruments and channels

#### Payment instruments
- Tools we use to make payments, whether physical or digital
  - Cards
    - Credit, debit and prepaid cards are ubiquotous for both online and in-person transactions
  - Account-to-Account (A2A)
    - Direct transfers between bank accounts, including wires and ACH payments, real-time payments
  - Mobile wallets
    - Digital versions of physical wallets storing card details for tap-to-pay or online use
  - Cash-based Digital
    - Converting physical cash into digital value for online trsnactions or mobile money services
  - Emerging instuments
    - Cryptocurrencuies (bitcoin), and Central bank digital currencies (CBDCs)

#### Payment channels
- POS (Point of Sale)
  - In-store terminals where customers physically interact to complete purchases
  - Supports card types (credit, debit) through swipe, chip or even contactless methods
- ATM
  - Automated Teller machines for cash withdrawals, deposits, and other banking transactions
- E-commerce
  - Online websites and digital storefronts where transactions occur remotely over internet
- In-app
  - Payments occur directly within mobile app, often integrated with digital wallets
- QR/Contactless
  - Quick response (QR) code payments or Near field communication (NFC) tap-and-go methods


***
### ISO8583 Basics: The language of payments
- ISO8583 standard is the backbone of card payment systems, enbaling seamless and secure communication between financial institutions. It defines the structure and content of messages exchanged during transactions
- Standardization
  - ISo-International organization for standardization create a universal format for financial trsnaction messages
- Interoperability
  - Ensure different payment networks and devices can speak to each other, from POS terminal to bank mainframes
- Global reach
  - Adopted worldwide, facilitating cross-border payments and growth of electronic commerce

##### The core message structure of ISO8583
- MTI (Message type indicator):
  - Defines the purpose of message
- Bitmap
  - Indicates which data elements are present in message (a "map" of whats included)
  - Each bit represent specific DEs
- Data Elements (DEs)
  - Actual transaction information, like card numbers or amounts

##### Understanding MTI Basics (4 digit code)
- MTI tells the recieving system what kind of message is being sent
- Examples of MTI Code
  - 0200: Financial transaction request (authorization request)
  - 0210: Response to 0200 request (eg: approval)
  - 0400: Financial transaction reversal request
  - 0410: Response to 0400 reversal request
  - 0500: Settlement request
  - 0510: Response to 0500 settlement request

#### Data Elements
- Actual fields that carry specific transaction data
- Examples
  - DE2: PAN-Primary account number
  - DE3: transaction processing code
    - Type of transaction: (eg: purchase, withdrawal, refund and cash advance)
  - DE4: Transaction amount (precise monetary value)
  - DE11: System trace audit number (STAN) - a unique trace number (identifier) for message tracking
  - DE39: Response Code - indicates outcome of transaction (approved - 00, declined codes)

#### Why ISO8583 matters?
- New standards are available like ISO20022, ISO8583 still remains backbone of global payment processing for several reasons:
  - Powers billions of card and ATM transactions daily across globe
  - Highly flexible and adaptable to various transaction types and regions
  - Serves as universal language ensuring interoperability between banks, merchants and payment networks worldwide


### Breaking down sample ISO8583 Message
- MTI, Bitmap and data elements makes the ISO8583 message complete
- Approved message
  - MTI = 0210 (Authorization response)
  - DE39 = 00 (Approved)
  - DE4 = $100.00
- Decline message
  - MTI = 0210 (Authorization Response)
  - DE39 = 05 (Do not honor) due to insufficient fund or securoty reasons
  - DE4 = $100.00 

### Single vs Dual message Systems
- Single message system
  - Authorization and settlement of funds occur simultaneously within a single message exchange. Once transaction is approved, funds are immediately moved
  - Authorization + settlement combined (0200/0210)
  - This streamlined process ensures rapid fund availability, ideal for simple, real-time operations like cash-withdrawals
  - Faster but less flexible
- Dual message system
  - Separate transaction into 2 distinct phases: Authorization and Settlement
  - Authorization (0100 -> 0110) happens instantly
  - Settlement (0500 -> 0510) happens later in batch
  - Pre-authorization or adjustments before final settlements 


















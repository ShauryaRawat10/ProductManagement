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

***
## Cards, Terminals and Transactions

#### Payment terminals and transactions
- Understanding Point-of-sals (POS) devices
  - Countertop POS
    - Traditional card machines fixed at a sales counter, ideal for retail stores and restaurabts with dedicated checkout area
  - Mobile POS (mPOS)
    - Portable devices that allow transactions on the go, perfect for food trucks, delivery services, and field sales team, offering flexibilty
  - SoftPOS
    - Smartphones or tablets enabled to accept payments via NFC technology, transforming everyday devices into secure payment terminals without additional hardware
- ATM
  - Cash-out ATMs
    - Primarily used for withdrawing money from bank account
  - Cash-in ATMs
    - Allow users to deposit cash directly into their bank accounts without needing teller
  - Full Function ATMs
    - Advanced machines offering expanded services like bill payments, fund transfer, mobile top-ups, even account opening services

#### Understanding card types
- Debit cards
  - Linked directly to bank account, funds are deducted immediately upon transaction. Ideal for managing spending
- Credit cards
  - Allow users to borrow funds up to limit for purchases, with repayment due later. Offers flexibility and often rewards programs
- Prepaid cards
  - Funds are loaded onto a card in advance, allowing spending only up to loaded amount. Great for budgeting or gifting
- Contactless cards
  - Enabled with NFC technology for tap-and-go convenience, allowing swift transactions without physical contact with terminal

#### Common transaction Types
- Purchases
  - Most common transaction, where funds are transferred from cardholder to merchant for goods and services
- Withdrawals
  - Cash is disbursed from ATM or via a cash-back option at a POS terminal
- Refunds
  - Funds are returned to cardholer's account, reversing a previous purchase
- Reversals
  - Cancels a pending transaction before it settles, often due to an error or transaction timeout
- Balance inquiries
  - A request to check the available balance on an account or card, without any funds movement

#### Unpacking Ddata Elements (DEs) 
- Two most common types are critical for understanding and processing of payment messages
  - DE3: Processing code
    - It is 6-digit field specifying exact type/purpose of transaction being performed
      - 000000: Purchase
      - 010000: Cash withdrawal
      - 200000: refund
  - DE22: POS Entry mode
    - It is 3-digit field indicating how card data was captured by terminal
      - 051: Chip(EMV)
      - 021: Magnetic Stripe (Swipe)
      - 071: Contactless (NFC) - Tap

#### Key terms in Payments - BIN, PIN and more
- BIN : Bank Identification Number
  - The first six or eight digit of card number. The BIN uniquely identifies the financial institution that issued the card
  - Crucial for fraud detection and transaction routing
  - Used by payment processors to direct transactions to correct network
  - Essential for data analytics, providing insights into cardholder demographics and spending patterns
- PIN: Personal Identification Number
  - A confidential numeric password used to authenticate the cardholder for ATM withdrawals or point-of-sale purchases
    - Primarily used with debit cards, but also for credit cards in certain regions or for cash advances
    - Provides an added layer of security, verifying legitimate cardholder
    - Protected by encryption during transmission to prevent unauthorized access
- Signature transactions
  - Traditional method of cardholder verification where customer signs a receipt to authorize a transaction.
    - Relies on matching signature on reciept to signature on back of card
    - Still used in high value transactions or in enviornments where PIN entry is not feasible
    - Often complemented by other security measures, such as Address Verification Service (AVS)
- CVV/CVC
  - Card Verification Value/Code: 3 or 4 digit security code, usually on back of card, used for card-not-present transactions to prevent fraud
- PAN
  - Primary account number, is 16 digit card number. This sensitive data requires strict security protocols like encryption and tokenization
- Acquirer
  - Bank or financial institution that processes credit and debit card payments for merchants. It settles the fund into merchant's account
- Issuer
  - The financial institution that issues credit and debit cards directly to consumers. It sets terms, conditions, and credit limits for cardholders



***
## Exceptions, Disputes and Settlement

#### Failures and Reversals
- The NO-Response Scenario
  - 0400 - Reversal Request
  - 0410 - reversal Response
- The primary purpose of reversal is to negate a previous transaction, ensuring financial integrity
- If a transaction appears to fail but funds are held, a reversal releases those funds, preventing customer from being charged twice
- It safeguard merchants: Protects businesses from accounting errors, chargebacks due to held funds and maintain accurate sales record
- Customer protection: Shields conumers from erroneous charges, duplicate debits, and ensures their funds are accessible

#### Chargebacks and Disputes: When customers challenge transactions
- Different than merchant initiated refund
- Forced Refund:
  - An issuer-initiated forced refund, triggered after a customer disputes a transaction with their bank or card provider
- Consumer protection:
  - Designed as a consumer protection mechanism by card networks, safeguarding buyers from unauthorized or unsatisfactory transactions
- Impact on Merchants
  - Directly impacts merchants revenue, operational costs, and can lead to penalties and increased processing fees

#### Chargeback vs Reversal
- Transaction Reversal
  - A technical correction to a transaction, often due to an error at point of sale
  - Typically, immediate and handled directly between the acuirer and merchant (eg: duplicate charge, incorrect amount)
  - Uses specific ISO8583 Message Type Indicator (MTIs) like 0420/0430
  - Generally has minimal impact on merchant standing
- Customer Chargeback
  - A formal consumer dispute process, initiated by cardholder through their issuing bank
  - Occurs post-settlement, after funds have been transferred to merchant
  - Governed by strict card network rules and regulations, requiring documentation and dispute resolution
  - Can result in financial losses, fees and potential damage to merchant reputation


#### Lifecycle of chargeback
- Cardholder Disputes: Customer contact issuing bank to dispute a transaction, citing specific reason
- Issuer files Chargeback: Files formal chargeback thorugh card network
- Acquirer Notifies merchant: Card network forwards chargeback to acuiring bank, which then notifies merchant
- Merchant responds: Merchant has limited window to accept chargeback or submit compelling evidence to fight it (representment)

#### Common chargeback Reasons
- Fraud/Unauthorized
- Goods not received
- Product Not as described
- Duplicate processing errors


#### Compelling Evidence for merchants
- Proof of delivery
  - Tracking number, delivery confirmation, signed receipts, or proof of shipment to cardholder's address
- Transaction records
  - detailed transaction logs, receipts, order forms, and terminal logs for in-person sales
- Customer Communications
  - Emails, chat logs, phone records, or any correspondence proving customer satisfaction or agreement
- Fraud prevention data
  - AVS (Address Verification Service), CVV (Card Verification Value) and 3D Secure (3DS2) match logs for online transaction

#### Critical time window and deadlines
- Issuing filing window
  - Issuing bank have 60 to 120 days from transaction date to file a chargeback on behalf of their customer
- Merchant response period
  - Merchant are usually given a short window, often between 7 to 45 days to respond to chargeback notification
- Automatic loss
  - Missing these strict deadlines for submitting evidence or responding to inquiries often results in an automatic loss of dispute

#### Prevention strategies: Resolution and Win
- Clear policies
- Fraud checks
- Accurate tracking
- Responsive support


## Clearing in Practice: How banks exchange transaction data
- Clearing is the essential process that happens behind the scenes after a financial transaction is authorized but before the money actually moves. It's how payment networks determine the final financial obligations between banks
- Exchange of transaction details:
  - It's all about sharing the specifics of each financial transaction (digital files)
- Post authorization process
  - Occurs after a payment is approved, preparing it for settlement
- Determines financial obligations
  - Calculates who owes whom, and exactly how much for all transactions
- Batch processing
  - transactions are processed in batches over a period, not in real time for efficiency

* Clearing is accounting backbone of payment ecosystem

#### Flow of files: Outgoing and Incoming
- Outgoing files
  - From: Acquirer Bank
  - To: Payment Network (eg: VISA, Mastercard)
  - Content: Merchant transaction details, purchase amounts, associated fees (eg: interchange, processing fees)
  - Purpose: Informs network of all transactions initiated by merchants it serves
- Incoming files
  - From: Payment Network
  - To: Issuing Bank
  - Content: Customer transaction details, amounts to be debited from cardholder accounts, and fees owed to issuer
  - Purpose: Provides issuer with necessary information to charge customer accounts correctly


#### Network Specification: VISA and Mastercard
- Major payment networks have sophisticated clearing systems to manage the immense volume of transactions and their complexities
- VISA Clearing
  - System: VisaNet Clearing
  - A global, real time processing network that handles authorization, clearing and settlement for VISA products
  - Facilitates data exchange between acuirers and issuers for every VISA transaction
- Mastercard Clearing
  - System: GCMS (Global Clearing Management System)
  - Processes Mastercard transactions for clearing, ensuring accurate data transfer between participating financial institutions
  - Manages end-to-end clearing cycle for Mastercard products and services
- Both system meticulosly manage complex financial components:
  - Interchange fees: Fees paid by acquirer to issuer for each transaction
  - Currency Conversion: Handling transactions involving different currencies, calculating rates and associated fees
  - Clearing ensures all parties in trsnaction chain receives their due funds or are charged appropriately, maintaining integrity of payment ecosystem
    - Merchant receives funds from acquirer, minus various processing fees











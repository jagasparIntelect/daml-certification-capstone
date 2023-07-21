# Capstone Project

**The purpose of this repository is to provide the Daml App required to pass the Daml Fundamentals Certification**

---

# Daml Fundamentals Certificate Sample App

✨ Welcome to the Daml Fundamentals Certification Sample App! ✨

# 🛠️ DamlTicketOffice 🛠️ 
DamlTicketOffice is a project management application built in Daml.

### I. Overview 
This project was created by using the `empty-skeleton` template. The project adopts and exemplifies the `proposal-accept` design pattern. 

The eventOwner can create multiple events and add clients as observers to those contracts. Clients can then see the event contracts and choose to create a TicketPurchaseProposal for the event they wish to attend or for the entire season. They can change those proposals if they're not evaluated yet. The seller (eventOwner) can Reject the proposals providing a reason or Accept them and give origin to the Ticket contracts. After the event has happened the owner can then archive the Event contract and all the tickets related to it.

### II. Workflow
  1. owner creates Event contracts     
  2. owner exercises AddObservers to add all existing clients to the newly created event
  3. client sees the event and creates a TicketPurchaseProposal as proposer for that same event
  4. client exercises ChangeProposal to change the ticketInfo in the TicketPurchaseProposal
  5. seller exercises AcceptPurchase and a Ticket contract is created
  6. seller exercises EventHappened, the Event contract and all the related Ticket contracts are archived

### III. Sidenotes
Functionalties not completely implemented in the project:
  - To make the AddObservers to Event contracts better, 2 automations should be implemented:
    - Every time an Event is added, all the client parties in the system are added as observers
    - Every time a client is onboarded it is added as observer to all existent events
  - To completely make the Season ticket type work correctly, an automation like a Daml Trigger should be added to deduct -1 from the available tickets on all events for that season every time a Season ticket is purchased.

### IV. Compiling & Testing
To compile and test, run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```
# Parking-Garage
Design a reservation and payment system for a parking garage.

The requirements will involve:

a way to reserve a parking spot and receive a ticket/seat
the ability to pay for a parking spot
preventing two people from being able to reserve the same parking spot
three types of parking spots: compact, regular, and large vehicles
the prices for the garage are flat rate based on time duration, and they are different for each type of parking spot

This editor is synced in real time with your peer.

Use it to share thoughts and resources, such as:
- Features scope
- API design
- Pseudo code for specific components
- Data model/schema
- Back-of-the-envelope calculations
- Reference links
- Link to whiteboard or diagram such as https://sketchboard.me/new

Good luck!


mckinsey



API Design
Data Model

Total Users
Type of Communication

Database Model

YT and Posts




Belo horizonte Parking Garage Design


## Requirements:

1. User should be able to reserve Mobile or Desktop 
no Special Machine at the Parking spot
2. A user should be able to login to the system
3. A user should be able to select a parking spot. (Only 1 parking garage)
4. A user should be able to pay with credit card for the parking spot. 
(pix) Also Paypal, Bitcoin
5. Language of the system. Portugese and English
6. A user should be able to choose the type. ( compact, regular, and large vehicles)
7. A user should receive an email confirmation
8. A user should be able to finish the parking and receive an email with the billing details.

9. There is an authorization for the payment when parking is booked.
10. The payment is collected at the end.


11. A user should be able to reserve ahead of time.


NonFuncitonal Requirements:

1. Performance
2. Available
3. Fault-Tolerant
4. Cost


Priority on 1 to 10


Users: 1M Users.
Spots: 1000 spots.


## Data Design

Users
-userid
-email
-name
-city
-phone number
-address

1M * 500 * 4 Bytes = 2000B * 1M =  2GB

ParkingSpot
-parkingid
-type
-details

Reservation
-reservationid
-userid
-parkingid
-datetime
-status(booked,occupied,completed)

Billing
-billingid
-status (Approved, Authorized, Failed Payment )
-creationdate
-approvaldate
-paymentdate
-userid (fix)
-reservationid (fix)


Wallet
-userid
-creditcard(encrpyted) PII Legal 
-pin(encrpyted) PII Legal
-expdate




UP to 100GB


TYPE
#compact
#regular
#large vehicles


https://excalidraw.com/#room=ed9b803f20d8cd5b323e,SltxcfMMWwJ4rfrU-u6QBA




Pagatome
Maracadole




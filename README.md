## Security Review

By letting security experts review code and libraries used the system can be hardened. Threats however come in many different forms so its not only limited to reviewing code.

### White Box Pentest

Security experts will be allowed to perform a so called "white box pen test" after being provided with code etc by the Foundation. However, the Foundation has a limited access to the overall system itself as it relies heavily on Apple and Google.

### Third Party Server Security

To not depend on server security, we one-way encrypt passwords, salted uniquely per user, and send all traffic over TLS. However, iGov.Direct's integrity is built on showing the Real Name of it's members proposals and objections. Voting records are also subject to audit.

### What is it we want to achieve?

1. Collect votes on a proposal (Google Firestore)
2. Store the votes in a file (JSON)
3. Generate a SHA 3 hash of the file
4. Inject the hash into bitcoin blockchain
5. Host the file or records for anybody to audit and compare the hash against

### Known Security Threats

Scenario: A bot attacks the Cloud Functions

Solution: We limit by country IP

Scenario: A hired hack team tries to perform a "wipe"

Solution: Multiple back-ups around the world

Scenario: Open source intelligence (OSINT)

Solution: Limit available information online 

Scenario: DNS spoof for mail or the target site

Solution: Use encryted DNS

Scenario: Fake passport or id-card tries to register

Solution: Verify its a real passport on a protected backend

Scenario: Brut force attack agaist auth function

Solution: Token

Scenario: Physical access with the target pc

Solution: Encryption and hardend passwords

Scenario: Attacker tries to manipulate a voting record

Solution: A generated SHA 3 hash of the file is stored in bitcoin blockchain


### Report a Vulnerability or Threat

Please report a vulnerability or threat to support@ 


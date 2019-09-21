## Security Review

By letting security experts review code and libraries used the system can be hardened. Threats however come in many different forms so its not only limited to reviewing code.

### White Box Pentest

Security experts will be allowed to perform a so called "white box pen test" after being provided with code etc by the Foundation. However, the Foundation has a limited access to the server security as it relies heavily on Apple and Google.

### Server Security (third party)

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

Solution: We use multiple back-ups around the world

Scenario: Open source intelligence (OSINT) to find targets

Solution: We limit available information online 

Scenario: Attacker tries to DNS spoof for mail or target site access

Solution: We use encryted DNS + Yubikeys

Scenario: Fake passport or id-card tries to register

Solution: We verify its a real passport on a protected backend. For some countries we require a two tier registration, that means after registration, the password is sent as SMS to verify it.

Scenario: Brut force attack agaist auth function

Solution: Token (possibly also trigger captcha) 

Scenario: Physical access with the target pc

Solution: Encrypted, backed-up laptops with hardend passwords

Scenario: Attacker tries to manipulate a voting record

Solution: A generated SHA 3 hash of the file is stored in bitcoin blockchain

Scenario: Attacker tries to reverse engineer code in app (for whatever reason)

Solution: We obfuscate the code on Android. On iOS the app binary is encrypted using Apple's fairplay. The only way to decrypt encrypted binary data is on a jailbroken device with a few special tools installed. This gives machine code, which is not human-readable. Decompilers can present the app logic in Assembler and give some basic information about method and class names, but trying to figure out the app logic is exceedingly difficult.


### Report a Vulnerability or Threat

Please report a vulnerability or threat to support@ 


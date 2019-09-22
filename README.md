## Security Review

By letting security experts review code and libraries used the system can be hardened. Threats however come in many different forms so its not only limited to reviewing code. This document will be updated frequently.

### White Box Pentest

Well known security experts and researchers will be invited to perform a so called "white box pen test". This means they are provided with the source code to easier detect vulnerabilites (after passing these tests, the code can be made open source). However, the Foundation has a limited access to the server security as it relies heavily on third parties, hence Apple and Google.

### Server Security (third party)

To not depend on third party server security, we one-way encrypt passwords, salted uniquely per user, and send all traffic over TLS. However, iGov.Direct's integrity is built on showing the real author of it's members proposals and objections. Voting records are also subject to audit.

### What is it we want to achieve?

1. Collect votes on a proposal (Google Firestore)
2. Store the votes in a file (JSON)
3. Generate a SHA 3 hash of the file
4. Inject the hash into bitcoin blockchain
5. Store multple copies of the voting files around independent organisations and iGov.Direct storage locations 
for anybody to audit and compare the hash against

### Known Security Threats

There are many scenarios, but below are a few. The threat level will naturally correlate to the number of voters and members. Listed from medium risk to low risk.


**Scenario:** A bot attacks the Cloud Functions

Counter Measures: We limit by country IP

**Scenario:** A hired hack team tries to perform a "wipe"

Counter Measures: We dump multiple back-ups around the world

**Scenario:** Attacker uses open source intelligence (OSINT) to find targets (developers)

Counter Measures: We limit available information online and at authorities

**Scenario:** Attacker downloads a bunch of password dumps. Attacker searches dumps for passwords of emails (found through from OSINT).

Counter Measures: YubiKey security key replacing password-based authentication (FIDO2)

**Scenario:** Attacker tries to DNS spoof targets for mail i.e. target@igov.direct (thanks [G Suite by Google cloud](https://gsuite.google.com) for supporting the Foundation), or target website access i.e. this one (thanks [GitHub](https://github.com) for supporting the Foundation) or ads.google.com (thanks [Google Ads](https://ads.google.com/home/) for supporting the Foundation). Other websites the Foundation holds are LinkedIn

Counter Measures: We use encryted DNS + Yubikeys (thanks Yubico for support)

**Scenario:** Fake passport or id-card tries to register

Counter Measures: We verify passports are real on a protected backend using all security systems built in to passports. 
For some countries we require a two tier registration, that means after registration, the password is sent as SMS or preferably
using an authenticator app to verify it.

**Scenario:** Brut force attack agaist auth function

Counter Measures: Token (possibly also trigger captcha) 

**Scenario:** Physical access with the target pc

Counter Measures: Encrypted, backed-up laptops with hardend passwords

**Scenario:** Attacker tries to manipulate a voting record

Counter Measures: A generated SHA 3 hash of the file is stored in bitcoin blockchain

**Scenario:** Attacker tries to reverse engineer code in app (Advanced Persistent Threat)

Counter Measures: We obfuscate the code on Android. On iOS the app binary is encrypted using Apple's fairplay. The only way to decrypt encrypted binary data is on a jailbroken device with a few special tools installed. This gives machine code, which is not human-readable. Decompilers can present the app logic in Assembler and give some basic information about method and class names, but trying to figure out the app logic is exceedingly difficult.

**Scenario:** Attacker uses a zero-day vulnerability with a specific goal of disrupting the service by taking over target computer (Advanced Persistent Threat)

Counter Measures: If the target notice that the screen is taken over he/her will have to unplug from internet to stop the attack. The intrusion will be reported as a possible zero-day attack so it can be patched.

### Report a Vulnerability or Threat

Please report a vulnerability or threat to support@ 


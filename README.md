## Security Review

By letting security experts review code and libraries used the system can be hardened. Threats however come in many different forms so its not only limited to reviewing code. This document will be updated frequently.

### White Box Pentest

Well known security experts and researchers will be invited to perform a so called "white box pen test". This means they are provided with the source code to easier detect vulnerabilites (after passing these tests, the code can be made open source). However, the Foundation has a limited access to the server security as it relies heavily on third parties, hence Apple and Google.

### Server Security (third party)

Following the overall objective to **not be responsible for server infrastructure, optimize for search engines and performance anywhere** - a serverless architecture is used.

To add features easily, Google Firebase was choosen. Firebase offers integrated services such as [Authentication](https://firebase.google.com/docs/auth/), [Performance Monitoring](https://firebase.google.com/docs/perf-mon/), [Realtime Database](https://firebase.google.com/docs/database/)), and Cloud Functions¹ (JavaScript). Data is stored as JSON and synchronized in realtime to every connected client. Using the iOS, Android, and JavaScript SDKs, all clients share one Realtime/Firestore Database instance and automatically receive updates with the newest data.

_FaaS platforms (i.e. AWS Lambda, Google Cloud Functions¹, Microsoft Azure Functions) execute application logic but do not store data. A “serverless” application architecture means the burden of protecting and scaling servers is outsourced (in this case to Google). Made with Cloudcraft._

_¹Google Cloud functions is a lightweight, event-based, asynchronous compute solution that allows to create small, single-purpose functions that respond to cloud events without the need to manage a server or a runtime environment. GCF are written in JavaScript and execute in a standard Node.js runtime environment. Functions get dynamically scaled up or down depending on current number of requests and gets time or invocations limits rather than server limits._

To not depend on third party server security, we one-way encrypt passwords, salted uniquely per user, and send all traffic over TLS. However, iGov.Direct's integrity is built on showing the real author of it's members proposals and objections. Voting records are also subject to audit.

# Systems Architecture
![](https://user-images.githubusercontent.com/36473429/44372568-c63a2c00-a4e4-11e8-8b5a-05418d23f65e.png)


### What is it we want to achieve?

1. Collect votes on a proposal (Google Firestore)
2. Store the votes in a file (JSON)
3. Generate a SHA 3 hash of the file
4. Inject the hash into bitcoin blockchain
5. Store multple copies of the voting files around independent organisations and iGov.Direct storage locations 
for anybody to audit and compare the hash against

### Known Security Threats

There are many scenarios, but below are a few. The threat level will naturally correlate to the number of voters and members. Listed from medium risk to low risk.


**Scenario:** Attacker uses open source intelligence (OSINT) to find targets (developers)

Counter Measures: We limit available information online and at authorities

**Scenario:** Attacker downloads a bunch of password dumps. Attacker searches dumps for passwords of emails (found through from OSINT).

Counter Measures: Two factor authentication should be used including YubiKey security key replacing password-based authentication (FIDO2)

**Scenario:** Attacker tries to DNS spoof targets for mail i.e. target@igov.direct (thanks [G Suite by Google cloud](https://gsuite.google.com) for supporting the Foundation), or target website access i.e. this one (thanks [GitHub](https://github.com) for supporting the Foundation) or ads.google.com (thanks [Google Ads](https://ads.google.com/home/) for supporting the Foundation). Other social media website account the Foundation holds, but don't use are LinkedIn, Facebook, and Twitter.

Counter Measures: We use VPN, encryted DNS, and Yubikeys (thanks Yubico for support)

**Scenario:** Attacker tries to register fake passports or id-cards

Counter Measures: We verify that passports are real on a protected backend using all security systems built in to passports. 
For some countries we require a two tier registration, that means after registration, the password is sent as SMS or preferably using an authenticator app to verify it.

**Scenario:** A distributed denial-of-service (DDoS) against the website

Counter Measures: Requires help from Google or possibly CloudFlare.

**Scenario:** A hired hack team tries to perform a "wipe"

Counter Measures: We regulary keep back-up dumpes on usb-sticks around the world

**Scenario:** Attacker tries a brute force attack agaist auth cloud function on multiple accounts to trigger them to lock down in an attempt to disrupt the service

Counter Measures: Only allow function access for authenticated users. When a user registers they get a unique token. This is then used to access every function after that. Any attempt to access such a function will be rejceted by google. 

**Scenario:** Physical access with the target pc due to burglary or theft

Counter Measures: Encrypted, backed-up laptops with hardend passwords

**Scenario:** Attacker tries to manipulate a voting record

Counter Measures: A generated SHA 3 hash of the file is stored in bitcoin blockchain

**Scenario:** Attacker tries to reverse engineer code in app (Advanced Persistent Threat)

Counter Measures: We obfuscate the code on Android. On iOS the app binary is encrypted using Apple's fairplay. The only way to decrypt encrypted binary data is on a jailbroken device with a few special tools installed. This gives machine code, which is not human-readable. Decompilers can present the app logic in Assembler and give some basic information about method and class names, but trying to figure out the app logic is exceedingly difficult.

**Scenario:** Attacker uses a zero-day vulnerability with a specific goal of disrupting the service by taking over target computer (Advanced Persistent Threat)

Counter Measures: If the target notice that the screen is taken over he/her will have to unplug from internet to stop the attack. The intrusion will be reported as a possible zero-day attack so it can be patched.

**Scenario:** Attacker uses hardware backdoor in mobiles, put there during delivery from the manufacturer, to change voting results. (Advanced Persistent Threat)

Counter Measures: Since voting records are auditable, its possible to figure out which manufactors have this problem. The risk for the manufacurer is high as being cought means criminal charges and most likely a ban of sales.

### Report a Vulnerability or Threat

Please report a vulnerability or threat to support@ 


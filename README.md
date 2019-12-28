## Security Review

By letting security experts review code and libraries used the system can be hardened. Threats however come in many different forms so its not only limited to reviewing code. This document will be updated frequently.

### White Box Pentest

Well known security experts and researchers will be invited to perform a so called "white box pen test". This means they are provided with the source code to easier detect vulnerabilities. After passing these initial audits, the code could made open source to let more security researchers look at it. This would obviously also mean a risk of being a target for ill willing people so it's not an easy choice. The researchers would only get access to the client/backend source code as the Foundation is relying on a serverless architecture (see server security below).

### Server Security (third party)

Following the overall objective to **not be responsible for server infrastructure, optimize for search engines and performance anywhere** - a serverless architecture is used. Serverless platforms (i.e. AWS Lambda, Google Cloud Functions¹, Microsoft Azure Functions) execute application logic but do not store data. Data is stored as JSON and synchronizes in realtime to every connected client using the iOS, Android, and JavaScript SDKs. The Foundations current serverless platform is Google Cloud.

_¹Google Cloud Functions (GCF) is a lightweight, event-based, asynchronous compute solution that allows to create small, single-purpose functions that respond to cloud events without the need to manage a server or a runtime environment. GCF are written in JavaScript and execute in a standard Node.js runtime environment. Functions get dynamically scaled up or down depending on current number of requests and gets time or invocations limits rather than server limits._

To not depend on third party server security, we one-way encrypt passwords, salted uniquely per user, and send all traffic over TLS. However, iGov.Direct's integrity is built on showing the real name of proposals and objections authors (to prevent trolling). The voting records are also subject to audit to prevent manipulation and fraud.

<img width="830" alt="iGov backend 2019-09-17 kl  21 06 48" src="https://user-images.githubusercontent.com/36473429/65071656-88316500-d98f-11e9-9eb9-55b8c1a9c3ec.png">

_A serverless application architecture means the burden of protecting and scaling servers is outsourced (in this case to Google). Made with Cloudcraft._

### How does iGov.Direct's digital democracy work?

1. The system stores votes on a proposal in Google Firestore
2. The system generates a JSON file with all the votes on the voting deadline
3. The system generates a SHA 3 hash of the JSON file
4. The system injects the SHA 3 hash into the bitcoin blockchain
5. The system makes the voting files available for anybody to audit and compare the hash against

### Security Threats

There are many, many scenarios, but below are a few examples. The threat level will naturally correlate to the number of voters and members. Listed from medium to low risk (due to the level of work required for the attacker).


**Scenario:** Attacker uses open source intelligence (OSINT) to find targets (developers)

Counter Measures: The Foundation limit available information online and state authorities

**Scenario:** Attacker downloads a bunch of password dumps. Attacker searches dumps for passwords of emails (found through from OSINT).

Counter Measures: The Foundation uses two factor authentication, including YubiKey security keys.

**Scenario:** Attacker tries to DNS spoof targets for mail i.e. target@igov.direct (thanks [G Suite by Google cloud](https://gsuite.google.com) for supporting the Foundation), or target website access i.e. this one (thanks [GitHub](https://github.com) for supporting the Foundation) or ads.google.com (thanks [Google Ads](https://ads.google.com/home/) for supporting the Foundation). Other social media website account the Foundation holds, but don't use are LinkedIn, Facebook, and Twitter.

Counter Measures: The Foundation use VPN, encrypted DNS, and Yubikeys (thanks Yubico for support)

**Scenario:** Attacker tries to register fake passports or id-cards

Counter Measures: The Foundation will be able to verify if a passports is real using a combination of security systems built in to modern passports and national-ID cards with its backend.

**Scenario:** Attacker launches a distributed denial-of-service (DDoS) against the Foundation website or backend

Counter Measures: The Foundation will request help from Google (or possibly CloudFlare)

**Scenario:** Attacker hires a hack team to perform a "wipe", hence delete all data

Counter Measures: The Foundtaion regularly keep back-up dumpes on usb-sticks around the world

**Scenario:** Attacker tries a brute force attack against auth cloud function on multiple accounts to trigger them to lock down in an attempt to disrupt the service

Counter Measures: The Foundation will only allow function access for authenticated users. When a user registers they get a unique token. This is then used to access every function after that. Any attempt to access such a function with the token will be rejected.

**Scenario:** Attacker gets physical access with a target laptop due to burglary or theft.

Counter Measures: The Foundation encrypts and back-up laptops reguraly

**Scenario** State backed attacker uses electronics-sniffing dogs to find hidden usb-sticks in Wipe operation

Counter Measures: The Foundation keeps copies at multiple locations around the world

**Scenario:** Attacker tries to manipulate a voting record

Counter Measures: A generated SHA 3 hash of the file is stored in bitcoin blockchain

**Scenario:** Attacker tries to reverse engineer code in app to find weaknesses

Counter Measures: The Foundation obfuscate the code on Android. On iOS the app binary is encrypted using Apple's fairplay. The only way to decrypt encrypted binary data is on a jailbroken device with a few special tools installed. This gives machine code, which is not human-readable. Decompilers can present the app logic in Assembler and give some basic information about method and class names, but trying to figure out the app logic is exceedingly difficult.

**Scenario:** Attacker uses a zero-day vulnerability with a specific goal of disrupting the service by taking over target computer (Advanced Persistent Threat)

Counter Measures: If the target notice that the screen is taken over he/her will have to unplug from the internet to stop the attack. The intrusion will be reported as a possible zero-day attack so it can be patched.

**Scenario:** Attacker uses hardware backdoor in mobiles, put there during delivery from the manufacturer, to change voting results in a limited number of proposals to avoid detection. (Advanced Persistent Threat)

Counter Measures: Since voting records are auditable for anybody, voters will be able to see if their vote changed. The Foundation also hope to use AI to trigger audits when neccessary. The risk for the manufacturer is very high as being caught means criminal charges and most likely a ban of sales.

### Report a Vulnerability or Threat

Please report a vulnerability or threat to support@ 


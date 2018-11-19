# Security Review

Privacy by Design
We only store info that is critical. 
"You have an updated passport" - scan it now.

### Problem

Scenario: you lost your passport, its vanished, you have a new one. - how do we sort that?

Scenario: A bot attacks the Cloud Functions

Solution: We limit by country IP

## What is it we want to achieve?

The system will never be able to claim that it is secure against every threat. Instead, the systems goal is to make it more secure and conviniant than todays system by:

1. Scan passports (read MRZ, read chip)
2. Verify its a real passport (ReadID does some extra verifications, i.e. is there a hashed fingerprint?)
3. Verify that the personal ID is real (check agaist SPAR etc)
4. Hash passport info using SHA 3 to create a fingerprint
5. Collect votes on a proposal (Google Firestore)
6. Store the votes in a file (JSON)
7. Generate a SHA 3 hash of the file
8. Inject the hash into bitcoin blockchain
9. Host the file or records for anybody to audit and compare the hash against

### What is the goal of the security review?

By letting security experts review code and libraries used we can harden the system. By implementing best practice policies and reducing the times we store any sensitive information we not only lower the risk of attacks but reduce the amount of information that is available that is not already publically available.

### White Box Pentest

## Stage 1



Open source intelligence (OSINT)

### Fuzzing

Fuzzing or fuzz testing is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program. The program is then monitored for exceptions such as crashes, failing built-in code assertions, or potential memory leaks. Typically, fuzzers are used to test programs that take structured inputs. This structure is specified, e.g., in a file format or protocol and distinguishes valid from invalid input. An effective fuzzer generates semi-valid inputs that are "valid enough" in that they are not directly rejected by the parser, but do create unexpected behaviors deeper in the program and are "invalid enough" to expose corner cases that have not been properly dealt with.

For the purpose of security, input that crosses a trust boundary is often the most interesting. For example, it is more important to fuzz code that handles the upload of a file by any user than it is to fuzz the code that parses a configuration file that is accessible only to a privileged user.

### Physical Access
But if u can get physical access with the target pc , mayb u can do a dns spoof for a gmail or the target site.. N ur target will hardly know whats going on,,,, so my advice is that brut force should always b last option

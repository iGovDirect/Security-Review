# Security Review

## What is it we want to achieve?

The system will never be able to claim that it is secure against every threat. Instead, the systems goal is to:

1. Collect votes on a proposal (Google Firestore)
2. Store the votes in a file (JSON)
3. Generate a SHA 3 hash of the file
4. Inject the hash into bitcoin blockchain
5. Host the file or records for anybody to audit and compare the hash against

### What is the goal of the security review?

By letting security experts review code and libraries used we can harden the system. By implementing best practice policies and reducing the times we store any sensitive information we not only lower the risk of attacks but reduce the amount of information that is available that is not already publically available.


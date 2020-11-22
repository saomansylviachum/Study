# Security

## Properties

1. Confidentially.  Only the sender and receiver can know what is in the message
2. Message integrity. They have to make sure that the message hasn't been changed by others during the transfermation.
3. Authentication: make sure that each other has the identity they claim
4. Operation security: firewalls or 

## Different steps

1. Prevention

   Security Policy, Security Awareness, Access control procedures

2. Detection

   Intrusion Detection System

3. Response

## Operation security steps

1. Define your sensitive data
2. Identify possible threats
3. Analyze security holes and other vulnerabilities
4. Appraise the level of risk associated with each vulnerability
5. Get countermeasures in place

## Prerequisites

### Encryption

#### Symmetric Encryption

block cipher

Cipher block chaining

#### PKI(Public Key Instructure)

There is a pair of keys to do this job. The private key would be kept by the owner and the public key would send out to others. 

When other use the public key to encrypt the message, the owner could use the private key to decrypt it.

**Disadvantages**: May take too long to do the job. 

**Session key**: So we would use a session key in the communication. A session key is generated randomly in each communication session, and share between the entities.

### Message integrity

#### Hash Function

MD5 SHA-1

#### MAC (Message Authentic Code)

To avoid the same message has the same hash value that other could get the info

#### Digital Signature

Hash the whole message to a fix-length value and use the private key to sign the value. 

And the receiver would use the public key to decrypt the signature and get the fix-length value. And use the same hash function to get the message hash again.

## SSL

1. Finish the TCP handshakes
2. SSL handshakes: validate the certificate and exchange the session keys.

## Email Security

### Encryption

SSL/TLS: ensure the communication is done by the session keys.

Authentication: Using the Hash and private key to sign the hash value. (Maybe DKIM I think)

### Authentication

#### SPF

Sender Policy Framework: designed to detect forging sender addresses during the delivery of the mail. 

#### DKIM

DomainKey Identified Mail

DKIM is associate with a public key with the domain by putting it into a DNS TXT record and then uses the associate private key to add a signature to mails sent through the domain owners mail server.

#### DMARC

Set the action we would make if there is a forging mail from my domain



## Operation Security

### Firewall

A system designed to prevent unauthorized access to or from a private network. All messages entering or leaving the intranet must pass through the firewall, which examines each message and blocks those that do not meet the specified security critieria.

#### Traditional Packet Filter

Examines each packet entering or leaving the network and accepts or rejects it based on user defined rules.

#### Stateful Filtering

Use a additional connection table to tracing the connection like TCP and prevent the malicious accessing.

#### Webapplication gateway

Proxy server that only allow the authenticated access to pass



### System

#### Intrusion Detection System

#### Intrusion Prevention System


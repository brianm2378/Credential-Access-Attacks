Credential Access: Steal or Forge Kerberos Tickets: Kerberoasting

Risk:

Adversaries may abuse a valid Kerberos ticket-granting ticket (TGT) that is vulnerable to offline hash cracking leading to credential theft, unauthorized access, and lateral movement. 

Event Name:

Kerberoasting
Adversaries possessing a valid Kerberos ticket-granting ticket (TGT) may request one or more Kerberos ticket-granting service (TGS) tickets for any SPN from a domain controller (DC).

A Kerberos Ticket-Granting Ticket (TGT) is a core concept in the Kerberos authentication protocol. It acts like a temporary proof of identity that lets a user request access to multiple services without re-entering credentials each time.

The Kerberos Ticket-Granting Service (TGS) is a core component of the Kerberos authentication system. It works closely with the Ticket-Granting Ticket (TGT) to enable secure, password-free access to services after login.

The SPN (Service Principal Name) is a unique identifier for a specific service instance on a network. It tells the Kerberos system exactly which service a client wants to access so it can issue the correct service ticket.

<img width="915" height="726" alt="image" src="https://github.com/user-attachments/assets/1585decd-fef9-4d93-bc54-f2e57b3f0b74" />

Threat Hypothesis:
The Threat actor performed Kerberos ticket manipulation to obtain and forge authentication tickets. Followed by Kerberoasting techniques to request service tickets for accounts with Service Principal Names (SPNs), then extracted user hashes from the service ticket to attempt offline cracking of the service account credentials.

<img width="1347" height="776" alt="image" src="https://github.com/user-attachments/assets/17a81016-9970-4038-8f7c-fd76a0fb2f97" />


Mitigation

Consider adding all privileged accounts to the Protected Users group to enforce stricter security policies, including the prevention of credential caching, Kerberoasting, and token impersonation. This built-in group helps reduce the attack surface of high-value accounts by applying default protections against common credential abuse techniques.

The Protected Users is a global security group for Active Directory that's designed to protect against credential theft attacks. The group triggers nonconfigurable protection on devices and host computers to prevent credentials from being cached when group members sign in.


Threat Actors Leveraging this Attack

Storm-1811 is a financially-motivated entity linked to Black Basta ransomware deployment. Storm-1811 is notable for unique phishing and social engineering mechanisms for initial access, such as overloading victim email inboxes with non-malicious spam to prompt a fake "help desk" interaction leading to the deployment of adversary tools and capabilities.

Scattered Spider is a native English-speaking cybercriminal group active since at least 2022. The group initially targeted customer relationship management (CRM) providers, business process outsourcing (BPO) firms, and telecommunications and technology companies before expanding in 2023 to gaming, hospitality, retail, managed service provider (MSP), manufacturing, and financial sectors.

Threat Hunting Procedure

Searched for excessive Kerberos service ticket grant requests (4769) in a short period of time. 

Additionally within those 4769 check the encryption for use of RC4 encryption (etype 0x17)

Run the following KQL query to search for adversary performing encryption downgrades to leverage kerberoasting.
https://github.com/Bert-JanP/Hunting-Queries-Detection-Rules/blob/main/Defender%20For%20Identity/PotentialKerberosEncryptionDowngrade.md

Run the following Sigma Rule:
https://github.com/SigmaHQ/sigma/blob/master/rules/windows/builtin/security/win_security_kerberoasting_activity.yml




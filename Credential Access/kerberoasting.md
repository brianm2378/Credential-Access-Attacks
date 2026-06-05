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

<img width="1469" height="73" alt="image" src="https://github.com/user-attachments/assets/c9b5f679-1c08-4085-9353-2db4c7634fd3" />

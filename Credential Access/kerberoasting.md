Credential Access: Steal or Forge Kerberos Tickets: Kerberoasting

Risk:

Adversaries may abuse a valid Kerberos ticket-granting ticket (TGT) that is vulnerable to offline hash cracking leading to credential theft, unauthorized access, and lateral movement. 

Event Name:

Kerberoasting
Adversaries possessing a valid Kerberos ticket-granting ticket (TGT) may request one or more Kerberos ticket-granting service (TGS) tickets for any SPN from a domain controller (DC).

A Kerberos Ticket-Granting Ticket (TGT) is a core concept in the Kerberos authentication protocol. It acts like a temporary proof of identity that lets a user request access to multiple services without re-entering credentials each time.

The Kerberos Ticket-Granting Service (TGS) is a core component of the Kerberos authentication system. It works closely with the Ticket-Granting Ticket (TGT) to enable secure, password-free access to services after login.

The SPN (Service Principal Name) is a unique identifier for a specific service instance on a network. It tells the Kerberos system exactly which service a client wants to access so it can issue the correct service ticket.



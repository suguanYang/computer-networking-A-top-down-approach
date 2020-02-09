## Review Questions
#### SECTION 2.1
R1. List five nonproprietary Internet applications and the application-layer proto- cols that they use.
A1: Web: HTTP; e-mail: SMTP, POP3, IMAP; file-transfer: FTP; bitTorrent: BitTorrent protocol.

R2. What is the difference between network architecture and application architecture?
A2: Network architecture is the design of computer network. It is a framework for the specification of a network's physical components and their functional organization and configuration(e.g., the OSI model), its operational principles and procedures, as well as communication protocols used. Application architecture is designed by the application developer and dictates how the application is structured over the various end systems. It describes the behavior of applications used in a business.

R3. For a communication session between a pair of process, which process is the client and which is the server?
A3: The process which initiates the communicationis the client; the process that waits to be contacted is the server.

R4. Why are the terms client and server still used in peer-to-peer applications?
A4: A peer that requests the file is the client, the peer that upload the file is the server.

R5. What information is used by a process running on one host to identify a pro- cess running on another host?
A5: The IP address of the destination host and the port number of the socket used by the process.

R6. What is the role of HTTP in a network application? What other components are needed to complete a Web application?
A6: HTTP defines how Web clients request Web pages from Web servers and how servers transfer Web pages to clients. A Web application consist of client(browser), server(apache, Microsoft servers, etc.), database(mysql, nosql, etc.)

R7. Referring to Figure 2.4, we see that none of the applications listed in Figure 2.4 requires both no data loss and timing. Can you conceive of an application that requires no data loss and that is also highly time-sensitive?
A7: online-document editor, like google documents.

R8. List the four broad classes of services that a transport protocol can provide. For each of the service classes, indicate if either UDP or TCP (or both) pro- vides such a service.
A8: 1.reliable data transfer only TCP; 2.congest control only TCP. 3.error checking. 4.support for encryption; 5.guaranteed throughput

R9. Recall that TCP can be enhanced with SSL to provide process-to-process security services, including encryption. Does SSL operate at the transport layer or the application layer? If the application developer wants TCP to be enhanced with SSL, what does the developer have to do?
A9: SSL operate at the transport layer. If the application developer wants TCP to be enhanced this SSL, he has to include the SSL code, to encrypt the message before pass it to socket or decrypt it from socket.

#### SECTION 2.2-2.5

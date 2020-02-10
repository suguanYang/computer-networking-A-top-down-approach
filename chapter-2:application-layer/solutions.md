## Review Questions
#### SECTION 2.1
R1. List five nonproprietary Internet applications and the application-layer protocols that they use.

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

A8: 1.reliable data transfer only TCP; 2.congestion control only TCP. 3.error checking. 4.support for encryption; 5.guaranteed throughput

R9. Recall that TCP can be enhanced with SSL to provide process-to-process security services, including encryption. Does SSL operate at the transport layer or the application layer? If the application developer wants TCP to be enhanced with SSL, what does the developer have to do?

A9: SSL operate at the transport layer. If the application developer wants TCP to be enhanced this SSL, he has to include the SSL code, to encrypt the message before pass it to socket or decrypt it from socket.

#### SECTION 2.2-2.5
R10. What is meant by a handshaking protocol?

A10: A communication(like transfer files) between 2 processes that prerequire exchange control packets(establish connection).

R11. What does a stateless protocol mean? Is IMAP stateless? What about SMTP?

A11: A stateless protocol is a communications protocol in which no session information is retained by the receiver, usually a server. Relevant session data is sent to the receiver by the client in such a way that every packet of information transferred can be understood in isolation, without context information from previous packets in the session. IMAP is stateful, SMTP is stateless.
> SMTP is a stateless protocol as the mail server does not maintain any connection with the client, it does not store any information about the client. If an email is asked to be sent twice, the server will resend it without saying that the email has been sent. POP3 is also a stateless protocol. IMAP is a state protocol, because the IMAP server must maintain a folder hierarchy for each of its users, this state information persists across a particular user's successive accesses to the IMAP server.

R12. How can websites keep track of users? Do they always need to use cookies?

A12: When a user first visit the website, the server creates an unique identification and save it in the database for that user, then response it as cookie number, the cookie number will stored on the user's host and managed by the browser. After this, each request to the websites will carry this cookie number by the user. Thus the website knows who is visiting. Not every websites need to use cookies unless they want to use cookie to track client information.

R13. Describe how Web caching can reduce the delay in receiving a requested object. Will Web caching reduce the delay for all objects requested by a user or for only some of the objects? Why?

A13: Web caches can let requested object closer to client thus reduce the response time for a request. Web caches can sub- stantially reduce traffic on an institution’s access link to the Internet.

R14. Telnet into a Web server and send a multiline request message. Include in the request message the If-modified-since: header line to force a response message with the 304 Not Modified status code.

A14: pass.

R15. Are there any constraints on the format of the HTTP body? What about the email message body sent with SMTP? How can arbitrary data be transmitted over SMTP?

A15: The message is written in ordinary ASCII text.
HTTP format(both request and response):
![HTTP format](https://raw.githubusercontent.com/suguanYang/computer-networking-A-top-down-approach/master/pics/http-format.png)
SMTP format:
```
EHLO exampledomain.com
250-server1.exampledomain.com Hello  [1.1.1.2]
250-SIZE 52428800
250-PIPELINING
250-AUTH PLAIN LOGIN
250-STARTTLS
250 HELP
AUTH LOGIN
334 VXNlcm5hbWU6 # username
dXNlcm5hbWUuY29t
334 UGFzc3dvcmQ6 # password
bXlwYXNzd29yZA==
235 Authentication succeeded
HELO exampledomain.com
250 exampledomain.com
MAIL FROM: <xxx@xxx.com>
250 Ok
RCPT TO: <xxx@xxx.com>
250 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
fuzzbuzz
.
250 Ok: queued as
QUIT
221 Bye
```

R16. Suppose Alice, with a Web-based e-mail account (such as Hotmail or Gmail), sends a message to Bob, who accesses his mail from his mail server using POP3. Discuss how the message gets from Alice’s host to Bob’s host. Be sure to list the series of application-layer protocols that are used to move the message between the two hosts.

A16: 1, Alice send mail from mail client to her mail server over http; 2, Alice's mail server send mail to Bob's mail server over SMTP; 3, Bob gets mail from his mail server over POP3.

R17. Print out the header of an e-mail message you have recently received. How many Received: header lines are there? Analyze each of the header lines in the message.

A17:
```
From: Media Temple user (mt.kb.user@gmail.com)
Subject: article: How to Trace a Email
Date: January 25, 2011 3:30:58 PM PDT
To: user@example.com
Return-Path: <mt.kb.user@gmail.com>
Envelope-To: user@example.com
Delivery-Date: Tue, 25 Jan 2011 15:31:01 -0700
Received: from po-out-1718.google.com ([72.14.252.155]:54907) by cl35.gs01.gridserver.com with esmtp (Exim 4.63) (envelope-from <mt.kb.user@gmail.com>) id 1KDoNH-0000f0-RL for user@example.com; Tue, 25 Jan 2011 15:31:01 -0700
Received: by po-out-1718.google.com with SMTP id y22so795146pof.4 for <user@example.com>; Tue, 25 Jan 2011 15:30:58 -0700 (PDT)
Received: by 10.141.116.17 with SMTP id t17mr3929916rvm.251.1214951458741; Tue, 25 Jan 2011 15:30:58 -0700 (PDT)
Received: by 10.140.188.3 with HTTP; Tue, 25 Jan 2011 15:30:58 -0700 (PDT)
Dkim-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=gmail.com; s=gamma; h=domainkey-signature:received:received:message-id:date:from:to :subject:mime-version:content-type; bh=+JqkmVt+sHDFIGX5jKp3oP18LQf10VQjAmZAKl1lspY=; b=F87jySDZnMayyitVxLdHcQNL073DytKRyrRh84GNsI24IRNakn0oOfrC2luliNvdea LGTk3adIrzt+N96GyMseWz8T9xE6O/sAI16db48q4Iqkd7uOiDvFsvS3CUQlNhybNw8m CH/o8eELTN0zbSbn5Trp0dkRYXhMX8FTAwrH0=
Domainkey-Signature: a=rsa-sha1; c=nofws; d=gmail.com; s=gamma; h=message-id:date:from:to:subject:mime-version:content-type; b=wkbBj0M8NCUlboI6idKooejg0sL2ms7fDPe1tHUkR9Ht0qr5lAJX4q9PMVJeyjWalH 36n4qGLtC2euBJY070bVra8IBB9FeDEW9C35BC1vuPT5XyucCm0hulbE86+uiUTXCkaB 6ykquzQGCer7xPAcMJqVfXDkHo3H61HM9oCQM=
Message-Id: <c8f49cec0807011530k11196ad4p7cb4b9420f2ae752@mail.gmail.com>
Mime-Version: 1.0
Content-Type: multipart/alternative; boundary="----=_Part_3927_12044027.1214951458678"
X-Spam-Status: score=3.7 tests=DNS_FROM_RFC_POST, HTML_00_10, HTML_MESSAGE, HTML_SHORT_LENGTH version=3.1.7
X-Spam-Level: ***
Message Body: This is a KnowledgeBase article that provides information on how to find email headers and use the data to trace a email.
```
- From: This displays who the message is from, however, this can be easily forged and can be the least reliable.
- Subject: This is what the sender placed as a topic of the email content.
- Date: This shows the date and time the email message was composed.
- To: This shows to whom the message was addressed, but may not contain the recipient's address.
- Return-Path: The email address for return mail. This is the same as "Reply-To:".
- Envelope-To: This header shows that this email was delivered to the mailbox of a subscriber whose email address is user@example.com.
- Delivery Date: This shows the date and time at which the email was received by your (mt) service or email client.
- Received: They form a list of all the servers/computers through which the message traveled in order to reach you. The received lines are best read from bottom to top. That is, the first "Received:" line is your own system or mail server. The last "Received:" line is where the mail originated. Each mail system has their own style of "Received:" line. A "Received:" line typically identifies the machine that received the mail and the machine from which the mail was received.
- Dkim-Signature & Domainkey-Signature: These are related to domain keys which are currently not supported by (mt) Media Temple services. You can learn more about these by visiting: http://en.wikipedia.org/wiki/DomainKeys.
- Message-id: A unique string assigned by the mail system when the message is first created. These can easily be forged.
- Mime-Version: Multipurpose Internet Mail Extensions (MIME) is an Internet standard that extends the format of email. Please see http://en.wikipedia.org/wiki/MIME for more details.
- Content-Type: Generally, this will tell you the format of the message, such as html or plaintext.
- X-Spam-Status: Displays a spam score created by your service or mail client.
- X-Spam-Level: Displays a spam score usually created by your service or mail client.
- Message Body: This is the actual content of the email itself, written by the sender.

> From: https://mediatemple.net/community/products/dv/204643950/understanding-an-email-header

R18. Assume you have multiple devices, and you connect to your email provider using POP3. You retrieve messages with the “download and keep” strategy from multiple devices. Can your email client tell if you have already read the message in this scenario?

A18: No. In the download and keep strategy, messages are not deleted after the user retrieves the messages. This can    be inconvenient, as each time the user retrieves the stored messages from a new machine, all of non-deleted messages will be transferred to the new machine (including very old messages).

R19. Why are MX records needed? Would it not be enough to use a CNAME record? (Assume the email client looks up email addresses through a Type A query and that the target host only runs an email server.)

A19: Yes an organization’s mail server and Web server can have the same alias for a host name. The MX record is used to map the mail server’s host name to its IP address.

R20. What is the difference between recursive and iterative DNS queries?

A20: Recursive DNS queries occur when a DNS client requests information from a DNS server that is set to query subsequent DNS servers until a definitive answer is returned to the client. Iterative DNS queries are ones in which a DNS server is queried and returns an answer without querying other DNS servers, even if it cannot provide a definitive answer.
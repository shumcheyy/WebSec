[SOURCE](https://thehackernews.com/2021/06/new-tls-attack-lets-attackers-launch.html)


#### Introduction


Researchers have disclosed a new type of attack that exploits misconfigurations in transport layer security (TLS) servers to redirect HTTPS traffic from a victim's web browser to a different TLS service endpoint located on another IP address to steal sensitive information.

The attacks have been dubbed **ALPACA**, short for "Application Layer Protocol Confusion - Analyzing and mitigating Cracks in TLS Authentication,"

"Attackers can redirect traffic from one subdomain to another, resulting in a valid TLS session," the study said. "This breaks the authentication of TLS and cross-protocol attacks may be possible where the behavior of one protocol service may compromise the other at the application layer."

![](https://thehackernews.com/images/-6T8mLagtSTY/YMDsgdOvyXI/AAAAAAAACzg/n9_ubCfFfnAboLcwYQpWORDGYC8rqKxGQCLcBGAsYHQ/s728-e1000/tls-attack.jpg)

ALPACA attacks are possible because TLS does not bind a TCP connection to the intended application layer protocol, the researchers elaborated. The failure of TLS to protect the integrity of the TCP connection could therefore be abused to "redirect TLS traffic for the intended TLS service endpoint and protocol to another, substitute TLS service endpoint and protocol."

Given a client (i.e., web browser) and two application servers (i.e., the intended and substitute), the goal is to trick the substitute server into accepting application data from the client, or vice versa. Since the client uses a specific protocol to open a secure channel with the intended server (say, HTTPS) while the substitute server employs a different application layer protocol (say, FTP) and runs on a separate TCP endpoint, the mix-up culminates in what's called a cross-protocol attack


![](https://thehackernews.com/images/-sAdGuYwxSW8/YMDtPezICJI/AAAAAAAACzo/HrLOe4Ju63cu3xrxmWVIy6reEC5ibyRUgCLcBGAsYHQ/s728-e1000/hacking.jpg)


#### Mitigation

To counter cross-protocol attacks, the researchers propose utilizing Application Layer Protocol Negotiation (ALPN) and Server Name Indication (SNI) extensions to TLS that can be used by a client to let the server know about the intended protocol to be used over a secure connection and the hostname it's attempting to connect to at the start of the handshake process.

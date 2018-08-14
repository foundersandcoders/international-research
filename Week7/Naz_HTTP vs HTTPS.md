>***HTTPS** - Hypertext Transfer Protocol Secure
**HTTP** - Hypertext Transfer Protocol
**SSL** - Secure Sockets Layer
**TLS** - Transport Layer Security
**PKI** - Public Key Infrastructure*


### How does HTTPS work? What are TLS/SSL certificates?

# HTTP vs. HTTPS :
*Using HTTPS, the computers agree on a "code" between them, and then they scramble the messages using that "code" so that no one in between can read them. This keeps your information safe from hackers.*

*They use the "code" on a Secure Sockets Layer (SSL), sometimes called Transport Layer Security (TLS) to send the information back and forth.*

**How Does HTTP Work?**
*In the beginning, network administrators had to figure out how to share the information they put out on the Internet.
They agreed on a procedure for exchanging information and called it HyperText Transfer Protocol (HTTP).*

*Once everyone knew how to exchange information, intercepting on the Internet was not difficult. So knowledgeable administrators agreed upon a procedure to protect the information they exchanged. The protection relies on SSL Certificate to encrypt the online data.*
#### Encryption means that the sender and recipient agree upon a "code" and translate their documents into random-looking character strings.

### The procedure for encrypting information and then exchanging it is called HyperText Transfer Protocol Secure (HTTPS).

*With HTTPS if anyone in between the sender and the recipient could open the message, they still could not understand it. Only the sender and the recipient, who know the "code," can decipher the message.*

*Humans could encode their own documents, but computers do it faster and more efficiently. To do this, the computer at each end uses a document called an ++"SSL Certificate"++ containing character strings that are the keys to their secret "codes."*

**SSL certificates contain the computer owner's "public key."**

***The owner shares the public key** with anyone who needs it. Other users need the public key to encrypt messages to the owner. The owner sends those users the SSL certificate, which contains the public key. **The owner ++does not++ share the Private Key** with anyone.*

#### The security during the transfer is called the Secure Sockets Layer (SSL) and Transport Layer Security (TLS).

*The procedure for exchanging public keys using SSL Certificate to enable HTTPS, SSL and TLS is called Public Key Infrastructure (PKI).*

# What is SSL?
*SSL (Secure Sockets Layer) is a standard security protocol for establishing encrypted links between a web server and a browser in an online communication.*

*The usage of SSL technology ensures that all data transmitted between the web server and browser remains encrypted.*

*An SSL certificate is necessary to create SSL connection. You would need to give all details about the identity of your website and your company as and when you choose to activate SSL on your web server. Following this, two cryptographic keys are created - a Private Key and a Public Key.*



# SSL :
++A highly-simplified example of encrypting using SSL certificates.++
> Sara (the sender) wants to send an encrypted email to Rajiv (the recipient). First Rajiv sends Sara a copy of his SSL Certificate. In this highly-simplified example, the public key in Rajiv's SSL Certificate is "+1." The private key, which stays in Rajiv's computer, is also "+1."
>
> So Sara composes a message to Rajiv. It says, "Hi--Sara." Then she instructs her computer to use Rajiv's SSL certificate to encrypt the message. The computer reads Rajiv's public key and adds +1 to each letter in the message.
>
> For example, A+1=B, B+1=C, and so forth.
>
> The encrypted message looks like this:
>
> HI - SARA becomes IJ - TBSB
>
> Anyone who reads the message along the way cannot understand it, because they do not have Rajiv's SSL certificate.
>
> When Rajiv receives the message, his computer subtracts one from each letter in the message. It is again perfectly readable.
>
> In real life, the public and private keys must be different
> The example above is simplified. It shows identical public and private keys. The problem with this example is that if Rajiv has identical keys, and if he sends Sara his SSL Certificate, then she can decrypt messages he receives from other people. He cannot send her his public key if it is the same as his private key; otherwise she could decrypt all Rajiv's messages.
>
> To protect Internet users, public keys are similar to, but not identical to, private keys. If Rajiv sends his public key to Sara in an SSL certificate, Sara's computer will have enough information to encrypt a message so that only Rajiv's private key can decrypt it.
>
> Here is Rajiv's public key:
>
> 3048 0241 00C9 18FA CF8D EB2D EFD5 FD37 89B9 E069 EA97 FC20 5E35 F577 EE31 C4FB C6E4 4811 7D86 BC8F BAFA 362F 922B F01B 2F40 C744 2654 C0DD 2881 D673 CA2B 4003 C266 E2CD CB02 0301 0001
>
> It hints at, but does not expose, the contents of Rajiv's private key. Rajiv can confidently send this key to Sara. He does not worry that she will be able to guess his private key. Although they are similar, because the keys are so long and complicated, it is computationally infeasible to calculate the private key from the public key.
>
> Based on this public key, Sara's computer uses an algorithm to translate her message into an equally unintelligible string of characters, which only Rajiv will be able to decrypt only with his private key.


## What is SSL/TLS Certificate?
***SSL or TLS** (Transport Layer Security) certificates **are data files that bind a cryptographic key to the details of an organization**. When SSL/TLS certificate is installed on a web server, it enables a secure connection between the web server and the browser that connects to it. The website's URL is prefixed with "https" instead of "http" and a padlock is shown on the address bar. If the website uses an extended validation (EV) certificate, then the browser may also show a green address bar.*

#### TLS uses stronger encryption algorithms and has the ability to work on different ports.
#### SSL certificates create an encrypted connection and establish trust.

## What is SSL used for?
*The SSL protocol is used by millions of online business to **protect** their **customers**, ensuring their online transactions remain **confidential**. A web page should use encryption when it expects users to submit confidential data, including personal information, passwords, or credit card details. All web browsers have the ability to interact with secured sites so long as the site's certificate is issued by a **trusted CA** (Certification Authority).*

## Why do I need SSL certificate?
*The internet has spawned new global business opportunities for enterprises conducting online commerce. However, that growth has also attracted fraudsters and cyber criminals who are ready to exploit any opportunity to steal consumer bank account numbers and card details. Any moderately skilled hacker can easily intercept and read the traffic unless the connection between a client (e.g. internet browser) and a web server is encrypted.*

## What details are included in a SSL certificate
*SSL Certificates will contain details of whom the certificate has been issued to. This includes the domain name or common name, serial number; the details of the issuer; the period of validity - issue date and expiry date; SHA Fingerprints; subject public key algorithm, subject's public key; certificate signature algorithm, certificate signature value. Other important details such as the type of certificate, SSL/TLS version, Perfect Forward Secrecy status, and cipher suite details are included. Organization validated and extended validation certificates also contain verified identity information about the owner of the website, including organization name, address, city, state and country.*

## Who issues SSL Certificates?
*A CA-Certificat Authority issues SSL certificates. On receiving an application, the CA verifies two factors:
It confirms the legal identity of the enterprise/company seeking the certificate and whether the applicant controls the domain mentioned in the certificate. The issued SSL certificates are chained to a 'trusted root' certificate owned by the CA.
Most popular internet browsers such as Firefox, Chrome, Internet Explorer, Microsoft Edge, and others have these root certificates embedded in their 'certificate store'. Only if a website certificate chains to a root in its certificate store will the browser allow a trusted and secure https connection. If a website certificate does not chain to a root then the browser will display a warning that the connection is not trusted.*

## How Does SSL Work?
The following graphic explains how SSL Certificate works on a website. The process of how an 'SSL handshake' takes place is explained below:


![](https://i.imgur.com/97ENflG.png)
![](https://i.imgur.com/Ju2h6Bg.png)




### How do I implement SSL on my website?
*Implementing SSL for a website is quite easy! A typical installation of SSL certificate involves the following steps:*
* Step 1. Acquire SSL certificate

  To implement **SSL/TLS security** on your website, you need to get and install a certificate from a trusted CA. A trusted CA will have its root certificates embedded in all major root store programs, meaning the certificate you purchase will be trusted by the internet browsers and mobile devices used by your website visitors.

  You should also decide which type of certificate suits you best.

  **Single domain certificates** allow you to secure one fully qualified domain name (FQDN).
  Wildcard certificates secure a single domain and unlimited subdomains of that domain.

  ***Multi-domain certificates** allow website owners to secure multiple, distinct domains on a one certificate. For example, a single MDC can be used to secure domain-1.com, domain-2.com, domain-3.co.uk, domain-4.net and so on.*

  ***Extended Validation certificates provide the highest levels of security**, trust and customer conversion for online businesses. Because of this, EV certificates contain a unique differentiator designed to clearly communicate the trustworthiness of the website to its visitors. Whenever somebody visits a website that uses an EV SSL, the address bar will turn green in major browsers such as Internet Explorer, Firefox and Chrome.*

* **Step 2.** Activate and install your SSL certificate

  *When SSL certificate is purchased from a web host, its activation is taken care of by the web host. The administrator of the website can also activate the SSL through Web Host Manager (WHM) or cPanel. In the WHM dashboard select the SSL/TLS option and choose "Generate SSL Certificate and Signing Request". Next, generate your Private Key and fill out the form for Certificate Signing Request (CSR).*


* **Step 3.** Update Website from HTTP to HTTPS

  *Your website is now capable of HTTPS! You must now configure you website so that visitors who access this site get automatically directed to the "HTTPS" version.*

**Resource** : https://www.instantssl.com/https-tutorials/what-is-https.html

**useful vids**: https://www.youtube.com/watch?v=po3zYOe00O4

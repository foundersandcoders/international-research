# HTTP vs HTTPS
Sangita, Simon, Artemis

## How does HTTPS work? What are TLS/SSL certificates? 

### HTTP 

- HTTP stands for **Hypertext Transfer Protocol**
- At it’s most basic, it allows for the communication between different systems.
- It’s most commonly used to **transfer data from a web server to a browser** in order to allow users to view web pages
- It’s the protocol that was used for basically all early websites
- **Problem:** the information that flows from server to browser is not encrypted, which means it can be easily stolen

### HTTPS

- HTTPS stands for **Hypertext Transfer Protocol Secure**
- HTTPS protocols increase security by using an additional **SSL certificate**
- this additional security can be extremely important, especially for websites that take sensitive data from its users (e.g. credit card information and passwords)

![](https://image.ibb.co/dwMkmU/Bildschirmfoto_2018_08_14_um_14_36_20.png)


### How does HTTPS work? 

- The SSL certificate **encrypts the information that users supply to the site**, which basically translates the data into a code
- Even if someone manages to steal the data they would not be able to understand it due to this encryption
- In addition to adding that extra layer of security, HTTPS is also secured via the **TLS protocol**
- TLS **helps provide data integrity**, which helps prevent the transfer of data from being modified or corrupted, and a**uthentication**, which proves to your users that they are communicating with the intended website.


## What is SSL?
Secure Sockets Layer.

### Yes, and? (no drunken giraffes involved)
SSL is a protocol that requires both the client and the server to provide authentication for a secure connection between the two to be established.

## And what's TLS?
*Times Literary Supplement* (if you're bookish), *Transport Layer Security* (if you're a geek).

### Which means ...?
Just a new-improved, and thus more secure, version of SSL. Modern browsers support TLS and some (e.g. Firefox) support both TLS and SSL.

### But how do I know the TLS/SSL isn't fake?
Both TLS and SSL are a form of digital certificate, issued by Certificate Authorities (CAs), such as Comodo. These have their own private key, which they use to sign the TLS/SSL and other types of digital certificates, and their own public key, which is installed in all modern browsers. When the keys match, the browser knows that the website the user is visiting is not a decoy but the authentic website at a valid address.

![](https://www.codeproject.com/KB/IP/326574/mutualssl_small.png)
 
### So when I visit an https URL, all is good?
Not quite. Many websites deliver *mixed content*; that is, although they do use a SSL/TLS certificate to communicate with the browser through a secure channel (HTTPS), they send some of their content via an unsecured connection (HTTP).

### How does this compromise security?
Suppose you're logged in on a website through a secure connection (HTTPS) and click on an image that the server will deliver to you through an insecure connection (HTTP). When you log in, the browser will send an authentication cookie with the request to the server. When you then request an image that will be sent to your browser via HTTP, the request will be unencrypted and sent as plaintext. Anyone eavesdropping can hijack your cookie to log into the website with your credentials.

#### Further reading
Introduction to TLS/SSL certificates
https://www.acunetix.com/blog/articles/tls-ssl-certificates-part-4/
Article on TLS vs SSL from a CA:
'TLS vs SSL: The Difference May Surprise You!'
[https://blog.comodo.com/e-commerce/tls-vs-ssl-whats-difference/](https://)

### TLS vs SSL: FAQs
 
#### When to choose TLS and when to choose SSL?
- When your server is capable of running the latest version of TLS, then go ahead with this protocol. Otherwise, it is better to use SSL.
#### Are they compatible?
- TLS is not compatible with versions of SSL. Similarly, we can say it in the reverse.
#### When do you encounter certificate issues?
- if you have configured your server with TLS protocols and if the communicating server uses any other certificate, this problem occurs and vice versa
#### How to handle certificate issues?
- configure your server with the other supporting protocols 
- be cautious that such an act may create security issues and therefore, be sure to choose a secured internet protocol 
- Or: simply ignore the communication with that particular server that does not support your TLS protocols
#### Which is faster?
- SSL is faster than TLS as authentications are not carried out intensively.
#### Which is more complex to manage on the server side?
- TSL is more complex as it requires certificate validations and good authentications.
#### Can I tell whether my connection is secure?
- Yes: the little green lock before `https` indicates your browser has established a secure connection.

    ![](https://i.imgur.com/8wkgtr8.png)

### Important Terminology 

#### TLS/SSL Handshake 
- client and server meet for the first time
- involves a series of steps through which both the parties validate each other and start communicating through the secure SSL/TLS tunnel
- concludes with the generation of a common key – secret key if you may call it
- [Great explanation](https://cheapsslsecurity.com/blog/what-is-ssl-tls-handshake-understand-the-process-in-just-3-minutes/)


#### TLS/SSL Keys

- The SSL/TLS protocol uses a pair of keys – one private, one public – to authenticate, secure and manage secure connections 
- These keys are a linked pair of text files and are created together as a pair when you create your Certificate Signing Request (CSR)
- SSL works by making one key of the pair (the public key) known to the outside world, while the other (the private key) remains a secret only you know (asymmetric encryption)
- TLS/SSL uses some very cool math tricks to make it easy to use your key pair together for security purposes but practically impossible for anyone else to break your encryption knowing the public key alone

 
# Demo: generate certificates
 
certificate git:(master) ✗ openssl req -x509 -newkey rsa:2048 -keyout client-key.pem -out client-cert.pem -days 365

```

const https = require('https');
const fs = require('fs');

const options = {
  key: fs.readFileSync('key.pem'),
  cert: fs.readFileSync('cert.pem'),
  
  // only required if used while certificate creation
  passphrase: '1234'
};


https.createServer(options, (req, res) => {
  res.writeHead(200);
  res.end('hello world\n');
}).listen(8000);
```


 
 useful sites:
 https://www.netlify.com
 https://letsencrypt.org/



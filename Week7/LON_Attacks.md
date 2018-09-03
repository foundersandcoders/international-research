# Attacks


## What are the following types of attack?

For this presentation, we're starting with the Man in the Middle (attack)

![Michael Jackson Man in the Mirror](https://media.giphy.com/media/nujsQOINyCSqc/giphy.gif)

## Man In The Middle (MITM)

![Man in the middle example](https://securebox.comodo.com/theme/images/man-in-the-middle-attack.png)

In short a Man-in-the-Middle (MitM) attack intercepts a communication between two systems *(server and client)*. 

For example, in an http transaction the target is the TCP connection between client and server. Using different techniques, the attacker splits the original TCP connection into 2 new connections, one between the client and the attacker and the other between the attacker and the server. 

Once the TCP connection is intercepted, the attacker acts as a proxy, being able to read, insert and modify the data in the intercepted communication.

This makes it possible for an attacker to capture a session cookie by reading the http header and also possible to change the amount in a money transaction inside the application context.


### MITM methodes/techniques:

* **LAN**
    * ARP Poisoining, DNS Spoofing, STP Mangling, Port Stealing
* **Local to Remote**
    * ARP Poisoining, DNS Spoofing, DHCP Spoofing, ICMP Redirection, IRDP Spoofing, Route Mangling
* **Remote**
    * DNS Poisoning, Traffic, Route Mangling
* **Wireless**
    * Access Point Reassociation
    * 
![](https://media.giphy.com/media/DO5JobrylWL7i/giphy.gif)

As you imagine, there is complexity in the subject and there is not just simply ‘one type of Man In The Middle attack’ – rather, the term is used to describe a category of attack. 
The techniques used for MITM attacks **can be classified below in consideration of the following three network environment types**: 
* Local Area Network
* From Local To Remote (through a gateway)
* Remote

Here are a few types of MITM attacks:

* **Address Resolution Protocol (ARP) Spoofing**, is a technique by which an attacker sends (spoofed) Address Resolution Protocol (ARP) messages onto a local area network. Generally, the aim is to associate the attacker's MAC address with the IP address of another host, such as the default gateway, causing any traffic meant for that IP address to be sent to the attacker instead.

* **Domain Name System (DNS) Spoofing** is done by replacing the IP addresses stored in the DNS server with the ones under control of the attacker. Once it is done, whenever users try to go to a particular website, they get directed to the false websites placed by the attacker in the spoofed DNS server.

* **Spanning Tree Protocol (STP) mangling** refers to the technique used for the attacker host to be elected as the new root bridge of the spanning tree. The attacker may start either by forging BPDUs (Bridge Protocol Data Units) with high priority assuming to be the new root, or by broadcasting STP Configuration/Topology Change Acknowledgement BPDUs to get his host elected as the new root bridge. By taking over the root bridge, the attacker will be able to intercept most of the traffic.

* **Internet Control Message Protocol (ICMP) redirection**: In case of ICMP MITM attack, first of all, the attacker looks for the network hosts that are down. When these hosts are pinged by other machines in the network, the attacker responds by sending a successful ping message. So, the machine starts exchanging data with the attacker’s machine thinking that it is the host they were looking for.

![](https://media.giphy.com/media/AgWQwLTByaABsBQ9Zf/giphy.gif)

MITM attack is also known as:
—————————————
Bucket-brigade attack :fire_engine:
——————————
Fire brigade attack :fire: 
—————————
Monkey-in-the-middle attack :monkey:
—————————————
Session hijacking :airplane: :computer:	
————————
TCP hijacking :airplane: :page_with_curl:
———————
TCP session hijacking :airplane: :computer:	 :page_with_curl:



### How can you defend against MITM?
* Ask him to change his ways

* Thanks to the “Asymmetric Cryptography”, known as the Public Key Cryptography, web and electronic communications are protected from MitM attacks. This cryptographic algorithm uses the public — private key pair to perform and ensure two essential functions:
    - Authentication — if a private key holder sends a message, its public key is used to verify and authenticate the holder
    - Encryption — only the private key holder can decrypt this message (that was previously encrypted using the public key)
* Therefore, a message can be encrypted by anyone via a public key, but it can only be decrypted by the holder via its matching private key.
* In this way, a hacker won’t be able to decrypt and read any messages sent through an encrypted protocol because the key pair is negotiated only between the existing two parties.


## Cross Site Scripting (XSS)
Cross Site scripting is probably the attack we're all most familiar with - think back to our good friend Bobby Tables. It's like that but injecting javascript not SQL commands.

![](https://i.imgur.com/SApu2zz.png)

* It is an attack where malicious scripts can be injected and executed in a legitimate website or web application.
* In order for an XSS attack to take place the vulnerable website needs to directly include non-validated and un-encoded user input in its pages.
* XSS is most widely abused with JavaScript  because JS is fundamental to most browsing experiences. (but can also be used with VBScript, ActiveX and Flash)

### XSS attacks can be put into three categories:

* **Stored XSS Attacks** - *originates from websites database*
    * These attacks occur when user input containing malicious scripts is stored in a website's database, and served up to visitors later. 
    * occurs commonly on pages with message boards, forums, and comment systems. 
    * malicious code is stored as user comments within the database, then displayed within the page causing the script to execute. 

#### Diagram of a Stored XXS Attack
![](https://i.imgur.com/C1MPLow.png)

1. The attacker uses one of the website's forms to insert a malicious string into the website's database.

2. The victim requests a page from the website.

3. The website includes the malicious string from the database in the response and sends it to the victim.

4. The victim's browser executes the malicious script inside the response, sending the victim's cookies to the attacker's server.


* **Reflected XSS Attacks** - *originates from the victim's request*
    * Reflected javascript injection vulnerabilities exist when web applications take parameters from the URL and displays them on a page. 
    * [Medium Article](https://medium.com/front-end-hacking/js-injection-example-e07ff4959db9) - shows how foxnews.com is vulnerable to a script injection in it's url. 

* **DOM-based XSS Attacks** - *vulnerability is in the client-side code rather than the server-side code*
    * The 'evil code' is executed as a result of modifying the DOM environment (in the victim’s browser) used by the original client-side script. That is, the page itself does not change, but the client side code contained in the page runs in an unexpected manner because of the malicious modifications to the DOM environment.
    * This is in contrast to other XSS attacks (stored or reflected), wherein the 'evil code' is placed in the response page (due to a server side flaw).
    * There seems to be an increased liklihood of a DOM-based attack when Dom is code reviewing your site but so far it's not scientificly proven 🤨. 


### How can you defend against XSS?
* The most important way of preventing XSS attacks is to perform **secure input handling**.
* To prevent all types of XSS attacks, secure input handling has to be performed in **BOTH client-side AND server-side** code.

* Most of the time, **encoding** should be performed whenever user input is included in a page.
    * **Encoding** is where you escape user input so that the browser interprets it only as data, not as code. The most recognizable type of encoding in web development is HTML escaping, which converts characters like < and >.

* In some cases, encoding has to be replaced by or complemented with **validation**.
    * **Validation** is the act of filtering user input so that all malicious parts of it are removed, without necessarily removing all code in it. One of the most recognizable types of validation in web development is allowing some HTML elements (such as ``<em>`` and ``<strong>``) but disallowing others (such as ``<script>``).

* Secure input handling has to take into account which context of a page the user input is inserted into.

* **Content Security Policy** provides an additional layer of defense for when secure input handling fails.
    * **CSP** is used to constrain the browser viewing your page so that it can only use resources downloaded from trusted sources. A resource is a script, a stylesheet, an image, or some other type of file referred to by the page. This means that even if an attacker succeeds in injecting malicious content into your website, CSP can prevent it from ever being executed.

[OWASP's XSS prevention cheat sheet](https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet)
[OWAPS's DOM-based XXS prevention cheat sheet](https://www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet)

#### Useful Links for XXS
https://excess-xss.com/
https://www.acunetix.com/websitesecurity/cross-site-scripting/

### Cross Site Request Forgery (CSRF)
* See resources from [PillarJS](https://github.com/pillarjs/understanding-csrf), [OWASP](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)) and [Acunetix](https://www.acunetix.com/blog/articles/cross-site-request-forgery/)
![Sea Surf](https://media.giphy.com/media/bgv4OvHBEbBQc/giphy.gif)
* Also referred to as CSRF, XSRF, "one-click attack" or "session riding"
    * Unsurprisingly, has nothing to do with CSR
* A CSRF attack tricks a user into **submitting a malicious request** (e.g. a password/email address change) to your site if they are currently authenticated. It does so by exploiting the fact that, for many sites, browser requests automatically include any credentials associated with the site, e.g. the session cookie, IP address...
    * Although there's no straightforward way for the attacker to see the *response* that comes back from a request, (e.g. sensitive data), they could: 
        * make a user update their login credentials and then access their account through these known credentials
        * make a user transfer something to another account
        * compromise the entire application if the victim has admin access!
* Note: using SSL alone doesn't protect from CSRF, as the malicious site could use an https link. Secret cookies don't help, either, as they will still be sent with an http request

So... 
#### How can you defend against CSRF?
Anti-CSRF tokens and same-site cookies
* [OWASP's CSRF prevention cheat sheet](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet)
    * Ensure there are no XSS vulnerabilities (see above)! XSS can often be used to circumvent CSRF defences

#### Anti-CSRF tokens
* This is the **recommended** and most widely-used CSRF prevention technique. You synchronise the cookie with an anti-CSRF token that has already been provided to the user's browser.
* Clever people like [Scott](http://scottksmith.com/blog/2014/09/04/simple-steps-to-secure-your-express-node-application/) and [Acunetix](https://www.acunetix.com/blog/articles/cross-site-request-forgery/) explain that, to mitigate these attacks, you can use a **secret, unique (to the user session) and random token that is embedded** in all HTML forms in your web app, and then verified on the server side upon submission.
    * It looks like you can use Express's CSRF and CSURF modules to achieve the above. It's recommended that you **use preexisting, tested, established/trusted libraries** rather than trying to implement this from scratch

``` 
<form>
// Regular form stuff goes here
<input type="hidden" name="anticsrf_token" value="f10dd7316b65649e" />
// Submit button goes here
</form>
```

* When a user submits a form or makes another authenticated request that requires a cookie, the **request should include the anti-CSRF token**. Your server should then verify the existence and correctness of it before acting on the request
* [According to this article](https://medium.com/node-security/cross-site-request-forgery-mitigation-for-express-js-apps-made-easy-using-the-same-site-cookie-flag-e19ee7d5b513), implementing these tokens can be tedious, so there's no demo for you to follow.
    * Good news, though! Have a look at this [recent article](https://www.twilio.com/blog/2018/01/protect-your-node-js-app-from-cross-site-request-forgery.html) for a node-related guide


#### Same-site cookies
`Set-Cookie: CookieName=CookieValue; SameSite=Strict`
* These "allow servers to mitigate the risk of CSRF and information leakage attacks by asserting that a particular cookie should only be sent with requests initiated from the same registrable domain."
* However, they're [**only supported in more modern browsers**](https://caniuse.com/#search=samesite), so shouldn't be used as your only defence! 
* It should also be noted that having SameSite as `Strict` instead of `Lax` can have some downsides, according to [NetsParker](https://www.netsparker.com/blog/web-security/same-site-cookie-attribute-prevent-cross-site-request-forgery/)
    * "For example, if you click on a link that points to a Facebook profile page, and if facebook.com has set its cookie as `SameSite=Strict`, you cannot continue navigation on Facebook (view the Facebook page) unless you log in to Facebook again. The reason for this is because Facebook`s cookie was not sent by this request."
    
By Monica, Emma and Dominic

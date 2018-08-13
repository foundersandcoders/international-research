### What is a token?


Tokens can be variables, permessions and more...
in our context token is authentication signture generated (token) by the server once you login. returned to the user with certian informations.
what we call JWT (JSON Web Token)
every time user make request to the server the server is going only to validate the signture(hashed code) and not finding the session each time as used in cookies without token.

---
![](https://user-images.githubusercontent.com/36166288/44034192-316b4ea8-9f15-11e8-99bc-894440c00935.jpeg)

---

### What is Stateful Authentication?

1. The user input his/her credentials
2. The app generates a unique session id
3. App stores it server-side and hands it back to the user.
4. Every service that requires some sort of information about the user must consult the data store.

---

![Stateful](https://i.imgur.com/WGCuWF0.png)

---

### What is Stateless Authentication?


Stateless authentication describes a system that enables its components to decentrally verify and introspect tokens. This ability to delegate token verification allows to (partly) get rid of the direct coupling to a central sessionID database.

Using a JWT as a bearer for authorization, you can statelessly verify if the user is authenticated by simply checking if the expiration in the payload hasn’t expired and if the signature is valid.

---

![Stateless](https://i.imgur.com/nyxkwCT.png)

---

### Advantages and disadvantages of Stateless authentication

| Advantages | Disadvantages |
| -------- | -------- |
| Less latency through due to decentralized user verification |Security reliant on secrecy of server side secret |
|Custom authorization fallbacks due to local token interpretation| Less live control over user access |
|Increased resilience by removed network overhead| The size of a JWT token will be more than that of a normal Session token|
|Stop the need to keep track of issued tokens, benefiting storage||
|Easier to support use of several servers. Normally done using a database|

---

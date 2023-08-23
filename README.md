# Cross-SR-Forgary
## **a desire to test everything.** 😋

# What is CSRF

A cross-site request forgery, or CSRF, attack occurs when an attacker can use an HTTP
request to access a user’s information from another website.

# Notes:

1. The httponly attribute
tells the browser that the cookie can only be read through HTTP and HTTPS requests.
2. if a cookie is httponly, browsers won’t allow any scripting languages,
such as JavaScript, to read its value. A cookie without the secure attribute can be sent to
a non-HTTPS site and, likewise, a cookie without httponly set can be read by a non-HTTP
connection.
3. the expiry date simply informs the browser of when the site will no longer consider
the cookie to be valid, so the browser should destroy it.
4. when you log out of a site, that site will typically send an HTTP
response that expires your cookie
5. GET :

<img src=”http://www.bank.com/transfere?from=bob&to=joe&amount=500”>

d the browser then makes the HTTP GET request to the bank. The browser
sends Bob’s authentication cookies to get what it thinks should be an image when in fact
the bank receives the request, processes the URL in the tag’s src attribute, and processes
the transfer.

1. content-type header : 

**content-type** : application/x-www-form-urlencoded or text/plain.

The content-type is important because browsers treat types differently (which
we’ll get to in a second). Now, in this situation, it’s possible for a malicious site to create
a hidden HTML form a

1. the POST request to be submitted with the content-type application/json instead

request that is an application/json
type will have a CSRF token

1. Sending POST requests as application/json are significant because browsers will first
send an OPTIONS HTTP request before the POST request is sent. The site then returns
a response to the OPTIONS call indicating which types of HTTP requests it accepts.
The browser reads this response and then makes the actual POST HTTP request, which
in our example, would be the transfer
2. when CORS is used to protect a site, you can’t submit an application/json request
to call the target application, read the response and make another call, unless the target
site allows it.

**Report Link: https://hackerone.com/reports/1277033**

# Where to look for CSRF

1. if there is an password/email/add-user/phone-num/transfers-money change input
2. i can navigate the request which send by changing the password 
3. the look for any extra headers ( validation-Headers) ⇒ ( taken / referrer header/ session / extra header … etc )

# CSRF PoC Generator

1. burp Generator
2. POST : <form>

# Bypass CSRF Protection

### **Token Validation :**

1. token fixed or static ⇒ copy-paste
2. short token ⇒ brute force
3. mabye7sal4 3aleh validation aslan ⇒ delete it and try to send the request without it , if the request sent successfully then there is no validation on it. 
4. law feh error bey3adeh : taken[]= ⇒ turn it to array y3ny hoa mestany string fa yla2y array fye3adeh (Data type).
5. change it’s value and try.
6. CORS sometimes can be bypassed by
changing the content-type from application/json to application/x-www-form-urlencoded
or by using a GET request instead of a POST request.

### Referrer Header

### Spoofing [ referrer header ]

- **With Get request :-**
- I can change request method to **[** **Get ] →**

 some developer never mind with request method .  

```php
$_request[parameter-name]
$_GET[parameter]
$_POST[parameter]
```

[Referer spoofing and defeating the XSS filter (Edge/IE) - Broken Browser](https://www.brokenbrowser.com/referer-spoofing-defeating-xss-filter/)

- **Open redirection :**

```php
$referrer= http://www.twitter.com/redire?url=http://www.vectem.com
```
*Note :
when CORS is used to protect a site, you can’t submit an application/json request
to call the target application, read the response and make another call, unless the target
site allows it.

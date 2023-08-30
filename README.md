# XSS-reserch
A research related to xss vulnerability
XSS (Cross-Site Scripting) vulnerability refers to code injection where hackers are able to inject malicious code into web pages or other web applications. These codes may include JavaScript, HTML, or other programming languages. An XSS vulnerability allows hackers to steal sensitive user information, steal user sessions, or perform unauthorized operations.

XSS vulnerability is divided into several categories:

    stored
    reflected
    blind
    self
    DOM
    
<Stored-xss>
This type of attack is one of the worst types of XSS attacks, where the hacker permanently places his code on the victim's website so that he can use it permanently 


<Reflected-xss>
This type of attack, which is also the most common XSS attack, the intruder finds temporary security holes in the website and implements his goals.
For example, if the site has a hole in the search section, the hacker can enter the desired code and provide other users with the address of the vulnerable page using shortened links.

<DOM-xss>
DOM XSS is an advanced type of XSS attack that allows an attacker to inject malicious scripts along with data sent to the Document Object Model (DOM). The data is then read by the web application and transferred to the browser.
In JavaScript, sinks refer to places that receive and use external data. Generally, sinks are points in a program or web page where input data is used, and if the input is not properly validated, it can lead to security vulnerabilities.
For example, functions like innerHTML, eval, setAttribute, etc. are common sinks in JavaScript. These functions can directly or indirectly receive external data and use them in a web page or program. If the inputs to these functions are not properly validated, hackers may be able to inject malicious code as inputs to these functions and have them executed in users' browsers.
On the other hand, sources in JavaScript refer to places that generate or provide external data. Generally, sources are points in a program or web page that produce external data.
So, in summary, DOM XSS occurs when a JavaScript source accepts user input and passes it to another function that may execute it as an unsafe sink.

Source

    document.URL
    document.documentURI 
    document.URLUnencoded 
    document.baseURI 
    location 
    document.cookie 
    document.referrer 
    window.name 
    history.pushState 
    history.replaceState
    
sink

    document.write()
    window.location
    document.cookie
    eval()
    document.domain
    WebSocket()
    someElement.src
    postMessage()
    setRequestHeader()
    FileReader.readAsText()
    ExecuteSql()
    sessionStorage.setItem()
    document.evaluate()
    JSON.parse()
    someElement.setAttribute()
    RegExp()

<Blind xss>
Blind XSS vulnerability is a type of Persistent XSS vulnerability. This vulnerability occurs when the penetration test input is stored on the web server and executed by a script in another part of the application or in another application.
Payload

    "><script src=https://hello.xss></script>

<self-xss>
This vulnerability is implemented through social engineering attacks that force the victim to enter malicious code into their console 
  
-------------------------------------------------------

Vulnerabilities that convert to xss:

    css injection 
    html injection 
    clickjacking 
    host header injection 
    Request smuggling 
    File Upload

<css injection>

CSS Injection Vulnerability means injecting malicious CSS code into web pages or web applications. This vulnerability allows hackers to inject malicious CSS code into the page and make changes to the appearance and display of the page. These codes may include changing colors, fonts, hiding elements, and other stylistic changes, or even the vulnerability can be converted to xss.
Payload:

     body {
           background-image: url('javascript:alert("origin")');
     }

     html injection

<HTML injecton>

HTML Injection vulnerability means injecting malicious HTML code into web pages or web applications. This vulnerability allows hackers to inject malicious HTML code into the page and make changes to the structure and display of the page. These codes may include adding new HTML elements, changing content, and hiding elements

<XSSJacking>

If our target has a clickjacking vulnerability, a self xss attack can be executed
Clickjacking vulnerability occurs when the website has used the iframe tag but has not secured it with the X-Frame-Option header.

<XSS via to HOST header injection>

Attacks that include direct injection of the payload into the Host header are called Host header injection attacks, which can sometimes be converted to xss.
Payload

    X-forwarded-host: "><script>alert(origin)</script>

<Xss via upload file>

There are two modes for xss in upload file
1_ Through the file name
Payload

    "><img src=x onerror=alert(origin)>.png

2_ Making changes in the content of the file   

<Request smuggling to xss>

The vulnerability of request smuggling can be converted to xss
for example :

    POST/HTTP/1.1
    Host: hacker
    Content-Length: 150 
    Transfer-Encoding: chunked

    0

    GET /hello
    user-agent: "><script>alert(origin)</script>
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 4

    X = 1
-------------------------------------------------------
<xss exploit>
  
Stealing Cookies:

    alert(document.cookie) 
    
open redirect:

    location.replace(http://......)
    
-------------------------------------------------------
Methods to prevent xss vulnerability :

    HttpOnly 
    CSP
    x-xss-Protection
    Filter

<HttpOnly>

And http-only cookies, the thing about these cookies is that the browser prevents them from being read by javascript.
HttpOnly can be bypassed through phpinfo

<CSP>

Content Security Policy or CSP is a large new HTTP header that controls where a browser is allowed to load content and what type of content it is allowed to load to prevent attacks like XSS.

<x-xss-protection>

This header helps us to prevent the occurrence of xss vulnerability

<Filter>

Characters can be filtered with the help of some functions such as htmlspecialchars

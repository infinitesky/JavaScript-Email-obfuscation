# JavaScript-Email-obfuscation
JavaScript email/phone obfuscation produces a normal, clickable email link for users while obscuring information from spiders
## Welcome to the JavaScript email/phone number obfuscation
JavaScript email obfuscation produces a normal, clickable email link for personal websites. It can obscures the email address, phone OR any text from spiders. Spiders can crawl the source code of web page and harvests email address and phone numbers. This information can be  scrambled, encoded, or otherwise obfuscated using JavaScript. 
**While very convenient for most users, it does reduce accessibility, e.g. for text-based browsers and screen readers, or for those not using a JavaScript-enabled browser.**

Implementation and Source:
JavaScript's event triggers can be used to obfuscate any text or element in HTML. The power of JavaScript to access and manipulate HTML DOM and change all the elements of an HTML document is really awesome. Combined with JavaScript's onclick or onmouseover events, we can toggle the visibility of text on trigger of an event.

**Here is an example of onclick event to obfuscate  email text:**
First, we can [convert the email to Hex](http://www.asciitohex.com/) equivalent and later it can be dynamically converted to ASCII text using JavaScript. So, only value visible to spider crawler is Hex Value. For example, example@example.com can be converted to Hex equivalent of `6578616d706c65406578616d706c652e636f6d`. Use this Hex value in the code and covert it dynamically to ACSII.

`    <p onclick="this.innerHTML = 'Email:  ' + getEmail('6578616d706c65406578616d706c652e636f6d')">
Email: Click to display Email</p>`

`    <script>
    function getEmail(hex) {
    var str = '';
    for (var i = 0; i < hex.length; i += 2)
        str += String.fromCharCode(parseInt(hex.substr(i, 2), 16));
    return str;
    }
    </script>`

**Here is an example of onmouseover event to obfuscate  phone number:**
Just like above, we can use intial phone number as Hex which can be dynamically converted to Decimal using JavaScript. e.g, Hex equivalent of decimal 9999999999 is `2540be3ff`.

`    <div onmouseover="mOver(this)" onmouseout="mOut(this)" >
    Phone: Mouse Over Me</div>`

`    <script>
    function mOver(text) {
        text.innerHTML = 'Phone: ' + '+1' + parseInt("2540be3ff",16);
        }
    function mOut(text) {
    text.innerHTML = "Phone: Mouse Over Me"
    }
    <script>`

PS: Few bots with browser automation API like WebDriver/phantom.js have ability to trigger click events and can load and extract the data from the page. This solution will not be able to protect against such bots.

Check out live example here: 
www.rahulc.dev/contactme.html

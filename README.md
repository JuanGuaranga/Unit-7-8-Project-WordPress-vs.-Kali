# Unit-7-8-Project-WordPress-vs.-Kali

### Authenticated Shortcode Tags Cross-Site Scripting

<img src="Authenticated Shortcode Tags Cross-Site Scripting.gif" alt="Authenticated Shortcode Tags Cross-Site Scripting">

This vulnerability requires the attacker to have an account with posting capabilities. It takes advantage of a shortfall in WordPress's KSES filtering (which filters out non-whitelisted HTML tags).

Recreating the Exploit
Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post:
[caption width="1" caption='<a href="' ">]</a><a href=" <Event-attribute-with-JS-code-here> ">Click me!</a>
which WP processes to:

<figcaption class="wp-caption-text"><a href="</figcaption></figure></a><a href=" <Event-attribute-with-JS-code-here> ">Click me</a>


Other Details
CVE: 2015-5714
Type: XSS
Affects: WordPress <=4.3
Patched: WordPress 4.3.1
 
### Authenticated Stored XSS in YouTube URL Embeds

<img src="Authenticated Stored XSS in YouTube URL Embeds.gif" alt="Authenticated Stored XSS in YouTube URL Embeds">

This vulnerability requires at least Contributor level privileges onto the site. Through this exploit, an attacker could take advantage of YouTube URL embeds to achieve a stored/persistent XSS attack that can affect any user who simply loads the compromised page.

Recreating the Exploit
Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post. Here, we demonstrate the vulnerability through the use of an embed shortcode:
[embed src='https://www.youtube.com/embed/12345\x3csvg <Event-attribute-with-JS-code-here>\x3e'][/embed]


Other Details
CVE: 2017-6817
Type: XSS
Affects: WordPress <=4.7.2
Patched: WordPress 4.7.3

###  Unauthenticated Stored Cross-Site Scripting

<img src="WordPress core stored XSS.gif" alt="WordPress core stored XSS">
 

This exploit requires an attacker to have an account with posting capabilities (i.e. a minimum of Contributor level permissions). In this vulnerability, an attacker can insert arbitrary Javascript via a specially-crafted shortcode onto a page or a post.

Recreating the Exploit
Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post:
<a href="[caption code=">]</a><a title=" <Event-attribute-with-JS-code-here>  ">link</a>


Other Details
CVEs: 2015-5622 and 2015-5623
Type: XSS
Affects: WordPress <=4.2.2
Patched: WordPress 4.2.3
 
### Wpscan vs. WP 4.2

<img src="challenge 7.gif" alt="Wpscan vs. WP 4.2">
 
 For the attack to succeed the following conditions have to be met:
- A WordPress admin uploads a malicious image file requested by a user this admin trusts or a popular malicious image that was spread via social media. This involves social engineering. In the Proof of Concept the file name cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg was used.
- An attacker can now determine if the file name with which the malicious file is available on the WordPress site. With this information he can spread the URL to end users and the WordPress admin.

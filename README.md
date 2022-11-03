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

### WordPress core stored XSS

<img src="WordPress core stored XSS.gif" alt="WordPress core stored XSS">
 
### Wpscan vs. WP 4.2

<img src="challenge 7.gif" alt="Wpscan vs. WP 4.2">

# Project 7 - WordPress Pen Testing

Time spent: **5** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pen Testing Report

### 1. (Required) Authenticated Shortcode Tags Cross-Site Scripting

- [ ] Summary: 

This vulnerability requires the attacker to have an account with posting capabilities. 
It takes advantage of a shortfall in WordPress's KSES  filtering (which filters out non-whitelisted HTML tags).

  - Vulnerability types: Cross-Site Scripting
  - Tested in version: 4.2
  - Fixed in version: 4.3.1
  
- [ ] GIF Walkthrough: 

 <img src="Authenticated Shortcode Tags Cross-Site Scripting.gif" alt="Authenticated Shortcode Tags Cross-Site Scripting">


- [ ] Steps to recreate: 

  Recreating the Exploit
  Gain access to an account with at least posting-level permissions via social engineering or another exploit. 
  (Alternatively, if the site allows unauthenticated   users to post via some special configuration, then an account is not needed.)
  Either create a new page/post or modify an existing one.
  Use the HTML editor (not the Visual editor) to insert code similar to the following and post:
  [caption width="1" caption='<a href="' ">]</a><a href=" <Event-attribute-with-JS-code-here> ">Click me!</a>
  which WP processes to:

  <figcaption class="wp-caption-text"><a href="</figcaption></figure></a><a href=" <Event-attribute-with-JS-code-here> ">Click me</a>
  
- [ ] Affected source code:
  - [Link 1] - http://blog.knownsec.com/2015/09/wordpress-vulnerability-analysis-cve-2015-5714-cve-2015-5715/
  - [Link 2] - https://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/

 
### 2. (Required) Authenticated Stored XSS in YouTube URL Embeds

- [ ] Summary: 

 This vulnerability requires at least Contributor level privileges onto the site. 
 Through this exploit, an attacker could take advantage of YouTube URL embeds to achieve a stored/persistent XSS attack that can affect any user who simply loads the compromised page.
 
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.7.3

- [ ] GIF Walkthrough: 

<img src="Authenticated Stored XSS in YouTube URL Embeds.gif" alt="Authenticated Stored XSS in YouTube URL Embeds">

- [ ] Steps to recreate: 

Recreating the Exploit
Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post. Here, we demonstrate the vulnerability through the use of an embed shortcode:
[embed src='https://www.youtube.com/embed/12345\x3csvg <Event-attribute-with-JS-code-here>\x3e'][/embed]
 
- [ ] Affected source code:
  - [Link 1] (https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/)


### 3. (Required)  Unauthenticated Stored Cross-Site Scripting
 
 - [ ] Summary: 
 
 This exploit requires an attacker to have an account with posting capabilities (i.e. a minimum of Contributor level permissions). In this vulnerability, an attacker can insert arbitrary Javascript via a specially-crafted shortcode onto a page or a post.
 
  - Vulnerability types:
  - Tested in version: 4.2
  - Fixed in version:  4.2.3
 
- [ ] GIF Walkthrough: 
 
 <img src="WordPress core stored XSS.gif" alt="WordPress core stored XSS">
- [ ] Steps to recreate: 
 
 Recreating the Exploit
   Gain access to an account with at least posting-level permissions via social engineering or another exploit. 
   (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
   Either create a new page/post or modify an existing one.
   Use the HTML editor (not the Visual editor) to insert code similar to the following and post:
   <a href="[caption code=">]</a><a title=" <Event-attribute-with-JS-code-here>  ">link</a>
 
- [ ] Affected source code:
 
  - [Link 1] https://packetstormsecurity.com/files/131644/

 
###  4. (Optional) Reflex gallery - Arbitrary File Upload

- [ ] Summary: 
  - Vulnerability types: UPLOAD
  - Tested in version: 4.2
  - Fixed in version: 3.1.4
- [ ] GIF Walkthrough: 
 
 <img src="challenge 7.gif" alt="Wpscan vs. WP 4.2">
 
- [ ] Steps to recreate: 
 
  For the attack to succeed the following conditions have to be met:
- A WordPress admin uploads a malicious image file requested by a user this admin trusts or a popular malicious image that was spread via social media. This involves social engineering. In the Proof of Concept the file name cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg was used.
- An attacker can now determine if the file name with which the malicious file is available on the WordPress site. With this information he can spread the URL to end users and the WordPress admin.
 
- [ ] Affected source code:
  - [Link 1] https://packetstormsecurity.com/files/130845/


 


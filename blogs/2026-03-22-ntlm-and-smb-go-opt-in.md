---
title: "NTLM and SMB go opt-in"
url: "https://daniel.haxx.se/blog/2026/03/22/ntlm-and-smb-go-opt-in/"
date: "Sun, 22 Mar 2026 11:41:09 +0000"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
<p>The NTLM authentication method was always a beast.</p>



<p>It is a proprietary protocol designed by Microsoft which was reverse engineered a long time ago. That effort resulted in the online documentation that I based the curl implementation on back in 2003. I then also wrote the NTLM code for wget while at it.</p>



<p>NTLM broke with the HTTP paradigm: it is made to authenticate <em>the connection</em> instead of <em>the request</em>, which is what HTTP authentication is supposed to do and what all the other methods do. This might sound like a tiny and insignificant detail, but it has a major impact in all HTTP implementations everywhere. Indirectly it is also the cause for quite a few security related issues in HTTP code, because NTLM needs many special exceptions and extra unique treatments.</p>



<p>curl has recorded no less than <em>seven</em> past <a href="https://curl.se/docs/security.html">security vulnerabilities</a> in NTLM related code! While that may not be only NTLM&#8217;s fault, it certainly does not help.</p>



<p>The connection-based concept also makes the method <em>incompatible</em> with HTTP/2 and HTTP/3. NTLM requires services to stick to HTTP/1.</p>



<p>NTLM (v1) uses super weak cryptographic algorithms (DES and MD5), which makes it a bad choice even when disregarding the other reasons.</p>



<p>We are slowly deprecating NTLM in curl, but we are starting out by making it opt-in. Starting in curl 8.20.0, NTLM is disabled by default in the build unless specifically enabled.</p>



<p>Microsoft themselves have deprecated NTLM already. The wget project looks like it is about to make their NTLM support opt-in.</p>



<h2 class="wp-block-heading">SMB</h2>



<p>curl only supports SMB version 1. This protocol uses NTLM for the authentication and it is equally bad in this protocol. Without NTLM enabled in the build, SMB support will also get disabled.</p>



<p>But also: SMBv1 is in itself a weak protocol that is barely used by curl users, so this protocol is also opt-in starting in curl 8.20.0. You need to explicitly enable it in the build to get it added.</p>



<h2 class="wp-block-heading">Not removed yet</h2>



<p>I want to emphasize that we have not removed support for these ancient protocols, we just strongly discourage using them and I believe this is a first step down the ladder that in a future will make them get removed completely.</p>



<p></p>

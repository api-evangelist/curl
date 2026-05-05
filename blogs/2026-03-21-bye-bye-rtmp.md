---
title: "bye bye RTMP"
url: "https://daniel.haxx.se/blog/2026/03/21/bye-bye-rtmp/"
date: "Sat, 21 Mar 2026 14:06:12 +0000"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
<p>In May 2010 we merged support for <a href="https://en.wikipedia.org/wiki/Real-Time_Messaging_Protocol">the RTMP protocol</a> suite into curl, in our desire to support the world&#8217;s internet transfer protocols.</p>



<h2 class="wp-block-heading">RTMP</h2>



<p>The protocol is an example of the spirit of an earlier web: back when we still thought we would have different transfer protocols for different purposes. Before HTTP(S) truly became the one protocol that rules them all.</p>



<p>RTMP was done by Adobe, used by Flash applications etc. Remember those? RTMP is an ugly proprietary protocol that simply was never used much in Open Source.</p>



<p>The common Open Source implementation of this protocol is done in the <a href="https://rtmpdump.mplayerhq.hu/">rtmpdump project</a>. In that project they produce a library, <em>librtmp</em>, which curl has been using all these years to handle the actual binary bits over the wire. Build curl to use librtmp and it can transfer RTMP:// URLs for you.</p>



<h2 class="wp-block-heading">librtmp</h2>



<p>In our constant pursuit to improve curl, to find spots that are badly tested and to identify areas that <em>could</em> be weak from a security and functionality stand-point, our support of RTMP was singled out.</p>



<p>Here I would like to stress that I&#8217;m not suggesting that this is the only area in need of attention or improvement, but this was one of them.</p>



<p>As I looked into the RTMP situation I realized that we had <em>no</em> (zero!) tests of our own that actually verify RTMP with curl. It could thus easily break when we refactor things. Something we do quite regularly. I mean refactor (but also breaking things). I then took a look upstream into the librtmp code and associated project  to investigate what exactly we are leaning on here. What we implicitly tell our users they can use.</p>



<p>I quickly discovered that the librtmp project does not have a single test either.  They don&#8217;t even do releases since many years back, which means that most Linux distros have packaged up their code straight from their repositories. (The project insists that there is nothing to release, which seems contradictory.) </p>



<p>Is there perhaps any librtmp tests perhaps in the pipe? There had not been a single commit done in the project within the last twelve months and when I asked one of their leading team members about the situation, I was made clear to me that there is no tests in the pipe for the foreseeable future either.</p>



<h2 class="wp-block-heading">How about users?</h2>



<p>In November 2025 I explicitly asked for RTMP users on the curl-library mailing list, and <em>one</em> person spoke up who uses it for testing.</p>



<p>In the 2025 user survey, 2.2% of the respondents said they had used RTMP within the last year.</p>



<p>The combination of <em>few users</em> and <em>untested code</em> is a recipe for pending removal from curl unless someone steps up and improves the situation. We therefor announced that we would remove RTMP support six months into the future unless someone cried out and stepped up to improve the RTMP situation.</p>



<p>We repeated this <em>we-are-doing-to-drop-RTMP</em> message in every release note and release video done since then, to make sure we do our best to reach out to anyone actually still using RTMP and caring about it.</p>



<p>If anyone would come out of the shadows <em>now</em> and beg for its return, we can always discuss it &#8211; but that will of course require work and adding test cases before it would be considered.</p>



<h2 class="wp-block-heading">Compatibility</h2>



<p>Can we remove support for a protocol and still claim API and ABI backwards compatibility with a clean conscience?</p>



<p>This is the first time in modern days we remove support for a URL scheme and we do this without bumping the SONAME. We do not consider this an incompatibility primarily because <em>no one will notice</em>. It is only a break if it actually breaks something.</p>



<p>(RTMP in curl actually could be done using six separate URL schemes, all of which are no longer supported: rtmp<code>,</code>rtmpe<code>,</code>rtmps, rtmpt<code>,</code>rtmpte<code>,</code>rtmpts.)</p>



<p>The offical <em>number of URL schemes supported by curl</em> is now down to 27: DICT, FILE, FTP, FTPS, GOPHER, GOPHERS, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, MQTT, MQTTS, POP3, POP3S, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, TELNET, TFTP, WS and WSS.</p>



<h2 class="wp-block-heading">When</h2>



<p><a href="https://github.com/curl/curl/commit/ceae02db040de3cf7ae4c3f8ec99e8286b568c2e">The commit</a> that actually removed RTMP support has been merged. We had the protocol supported for almost sixteen years. The first curl release without RTMP support will be 8.20.0 planned to ship on April 29, 2026</p>



<p></p>

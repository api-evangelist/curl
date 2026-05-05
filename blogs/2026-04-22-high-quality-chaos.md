---
title: "High-Quality Chaos"
url: "https://daniel.haxx.se/blog/2026/04/22/high-quality-chaos/"
date: "Wed, 22 Apr 2026 11:44:40 +0000"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
<p>As I have been preparing slides for my coming talk at foss-north on April 28, 2026 I figured I could take the opportunity and share a glimpse of the current reality here on my blog. The <em>high quality chaos</em> era, as I call it.</p>



<h2 class="wp-block-heading">No more AI slop</h2>



<p>I complained and I complained about the high frequency junk submissions to the curl bug-bounty that grew really intense during 2025 and early 2026. To the degree that we <a href="https://daniel.haxx.se/blog/2026/01/26/the-end-of-the-curl-bug-bounty/">shut it down completely</a> on February 1st this year. At the time we speculated if that would be sufficient or if the flood would go on.</p>



<p>Now we know.</p>



<h2 class="wp-block-heading">Higher volume, higher quality</h2>



<p>In March 2026, the curl project went <a href="https://daniel.haxx.se/blog/2026/02/25/curl-security-moves-again/">back to Hackerone</a> again once we had figured out that GitHub was not good enough.</p>



<p>From that day, the nature of the security report submissions have changed.</p>



<p>The slop situation is not a problem anymore.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29670" height="1080" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Open-Source-AI-reality-Foss-north-20264.jpg" width="1920" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption"><strong>AI slop rate</strong></figcaption></figure>
</div>


<p>The report frequency is higher than ever. Recently it&#8217;s been about double the rate we had through 2025, which already was more than double from previous years.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29665" height="1080" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Open-Source-AI-reality-Foss-north-20261.jpg" width="1920" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption"><strong>Number of hours between security reports</strong></figcaption></figure>
</div>


<p>The quality is higher. The rate of confirmed vulnerabilities is back to and even surpassing the 2024 pre-AI level, meaning somewhere in the 15-16% range.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29667" height="1080" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Open-Source-AI-reality-Foss-north-20262.jpg" width="1920" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption"><strong>Confirmed vulnerability rate</strong></figcaption></figure>
</div>


<p>In addition to that, the share of reports that identify a bug, meaning that they aren&#8217;t vulnerabilities but still some kind of problem, is significantly higher than before.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29668" height="1080" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Open-Source-AI-reality-Foss-north-20263.jpg" width="1920" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption"><strong>Share of reports that were bugs, not vulnerabilities</strong></figcaption></figure>
</div>


<h2 class="wp-block-heading">Everything is AI now</h2>



<p>Almost every security report now uses AI to various degrees. You can tell by the way they are worded, how the report is phrased and also by the fact that they now easily get very detailed duplicates in ways that can&#8217;t be done had they been written by humans.</p>



<p>The difference now compared to before however, is that they are mostly very high quality.</p>



<p>The reporters rarely mention exactly which AI tool or model they used (and really, we don&#8217;t care), but the evidence is strong that they used such help.</p>



<h2 class="wp-block-heading">We are not unique</h2>



<p>I did a quick unscientific poll on Mastodon to see if other Open Source projects see the same trends and man, do they! Friends from the following projects confirmed that they too see this trend. Of course the exact numbers and volumes vary, but it shows its not unique to any specific project.</p>



<p>Apache httpd, BIND, curl, Django, Elasticsearch Python client, Firefox, git, glibc, GnuTLS, GStreamer, Haproxy, Immich, libssh, libtiff, Linux kernel, OpenLDAP, PowerDNS, python, Prometheus, Ruby, Sequoia PGP, strongSwan, Temporal, Unbound, urllib3, Vikunja, Wireshark, wolfSSL, …</p>



<p>I bet this list of projects is just a random selection that just happened to see my question. You will find many more experiencing and confirming this reality view.</p>



<h2 class="wp-block-heading">An explosion</h2>



<p>When we ship curl 8.20.0 in the middle of next week &#8211; end of April 2026, we expect to announce at least six new vulnerabilities. Assuming that the trend keeps up for at least the rest of the year, and I think that is a fair assumption, we are looking at an estimated explosion and a record amount of CVEs to be published by the curl project this year.</p>



<p>We might publish closer to 50 curl vulnerabilities in 2026.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29675" height="1080" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Open-Source-AI-reality-Foss-north-20265.jpg" width="1920" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption"><strong>Number of published vulnerabilities</strong></figcaption></figure>
</div>


<p>Given this universal trend, I cannot see how this pattern can not also be spotted and expected to happen in many other projects as well.</p>



<h2 class="wp-block-heading">Where does it end?</h2>



<p>The tools are still improving. We keep adding flaws when we do bugfixes and add new features.</p>



<p>Someone has suggested it might work as with fuzzing, that we will see a plateau within a few years. I suppose we just have to see how it goes.</p>



<p>This avalanche is going to make maintainer overload even worse. Some projects will have a hard time to handle this kind of backlog expansion without any added maintainers to help.</p>



<p>It is probably a good time for the bad guys who can easily find this many problems themselves by just using the same tools, before all the projects get time, manpower and energy to fix them.</p>



<p>Then everyone needs to update to the newly released <em>fixed</em> versions of all packages, which we know is likely to take an even longer time.</p>



<p>We are up for a bumpy ride.</p>

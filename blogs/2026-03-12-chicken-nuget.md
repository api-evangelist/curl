---
title: "chicken nuget"
url: "https://daniel.haxx.se/blog/2026/03/12/chicken-nuget/"
date: "Thu, 12 Mar 2026 22:05:55 +0000"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
<p>Background: <a href="https://nuget.org/">nuget.org</a> is a Microsoft owned and run service that allows users to package software and upload it to nuget so that other users can download it. It is targeted for .Net developers but there is really no filter in what you can offer through their service.</p>



<p>Three years ago I <a href="https://daniel.haxx.se/blog/2023/03/02/the-curl-nuget-story/">reported on how nuget</a> was hosting and providing ancient, outdated and insecure curl packages. Random people download a curl tarball, build curl and then upload it to nuget, and nuget then offers those curl builds to the world &#8211; forever.</p>



<p>To properly celebrate the three year anniversary of that blog post, I went back to <a href="https://nuget.org/">nuget.org</a>, entered <em>curl</em> into the search bar and took a look at the results.</p>



<p>I immediately found at least <em>seven</em> different packages where people were providing severely outdated curl versions. The most popular of those, <a href="https://www.nuget.org/packages/rmt_curl">rmt_curl</a>, reports that it has been downloaded almost 100,000 times over the years and is still downloaded almost 1,000 times/week the last few weeks. <em>It is still happening</em>.  The packages I reported three years ago are gone, but now there is a new set of equally bad ones. No lessons learned.</p>



<p>rmt_curl claims to provide curl 7.51.0, a version we shipped in November 2016. Right now it has <a href="https://curl.se/docs/vuln-7.51.0.html">64 known vulnerabilities</a> and we have done more than 9,000 documented bugfixes since then. No one in their right mind should ever download or use this version.</p>



<p>Conclusion: the state of nuget is just as sad now as it was three years ago and this triggered another <em>someone is wrong on the internet</em> moments for me. I felt I should do my duty and tell them. Again. Surely they will act this time! Surely they think of the security of their users?</p>



<h2 class="wp-block-heading">Trusting randos</h2>



<p>The entire nuget concept is setup and destined to end up like this: random users on the internet put something together, upload it to nuget and then the rest of the world downloads and uses those things &#8211; trusting that whatever the description says is accurate and well-meaning. Maybe there are some additional security scans done in the background, but I don&#8217;t see how anyone can <em>know</em> that they don&#8217;t contain any backdoors, trojans or other nasty deliberate attacks.</p>



<p>And whatever has been uploaded once seems to then be offered in perpetuity.</p>



<h2 class="wp-block-heading">I reported this again</h2>



<p>Like three years ago I listed a bunch of severely outdated curl packages in my report. nuget says I can email them a report, but that just sent me a bounce back saying they don&#8217;t accept email reports anymore. (Sigh, and yes I reported <em>that </em>as a separate issue.)</p>



<p>I was instead pointed over to the generic Microsoft security reporting page where there is not even any drop-down selection to use for &#8220;nuget&#8221; so I picked &#8220;.NET&#8221; instead when I submitted my report.</p>



<h2 class="wp-block-heading">&#8220;This is not a Microsoft problem&#8221;</h2>



<p>Almost identically to three years ago, my report was closed within less than 48 hours. It&#8217;s not a nuget problem they say.</p>



<p><em>Thank you again for submitting this report to the Microsoft Security Response Center (MSRC).</em></p>



<p><em>After careful investigation, this case has been assessed as not a vulnerability and does not meet Microsoft&#8217;s bar for immediate servicing. None of these packages are Microsoft owned, you will need to reach out directly to the owners to get patched versions published. Developers are responsible for removing their own packages or updating the dependencies.</em></p>



<p>In other words: they don&#8217;t think it&#8217;s nuget&#8217;s responsibility to keep the packages they host, secure and safe for their users. I should instead report these things individually to every outdated package provider, who if they cared, would have removed or updated these packages many years ago already.</p>



<p>Also, that would imply a never-ending wack-a-mole game for me since people obviously keep doing this. I think I have better things to do in my life.</p>



<h2 class="wp-block-heading">Outdated efforts</h2>



<p>In the cases I reported, the packages seem to be of the kind that once had the attention and energy by someone who kept them up-to-date with the curl releases for a while and then they stopped and since then the packages on nuget has just collected dust and gone stale.</p>



<p>Still, apparently users keep finding and downloading them, even if maybe not at terribly high numbers.</p>



<p>Thousands of fooled users per week is thousands too many.</p>



<h2 class="wp-block-heading">How to address</h2>



<p>The uploading users are perfectly allowed to do this, legally, and nuget is perfectly allowed to host these packages as per the curl license.</p>



<p>I don&#8217;t have a definite answer to what exactly nuget should do to address this problem once and for all, but as long as they allow packages uploaded nine years ago to still get downloaded today, it seems they are asking for this. <em>They contribute and aid users getting tricked into downloading and using insecure software</em>, and they are indifferent to it.</p>



<p>A rare few applications that were uploaded nine years ago might actually still be okay but those are <em>extremely</em> rare exceptions.</p>



<h2 class="wp-block-heading">Conclusion</h2>



<p>The last time I reported this nuget problem nothing happened on the issue until I tweeted about it. This time around, a well-known Microsoft developer (who shall remain nameless here) saw my <a href="https://mastodon.social/@bagder/116160195073326855">Mastodon post</a> about this topic when mirrored over to Bluesky and pushed for the case internally &#8211; but not even that helped.</p>



<p>The nuget management thinks this is okay.</p>



<p>If I were into puns I would probably call them <em>chicken nuget</em> for their unwillingness to fix this. Maybe just closing our eyes and pretending it doesn&#8217;t exist will just make it go away?</p>



<p>Absolutely no one should use nuget.</p>

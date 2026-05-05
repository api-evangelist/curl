---
title: "Approaching zero bugs?"
url: "https://daniel.haxx.se/blog/2026/04/30/approaching-zero-bugs/"
date: "Thu, 30 Apr 2026 08:08:34 +0000"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
<p>In this era of <a href="https://daniel.haxx.se/blog/2026/04/22/high-quality-chaos/">powerful tools to find software bugs</a>, we now see tools find a lot of problems at a high speed. This causes problems for developers, as dealing with the growing list of issues is hard. It may take a longer time to address the problems than to find them &#8211; not to mention to put them into releases and then it takes yet another extended time until users out in the wild actually get that updated version into their hands.</p>



<p>In order to find many bugs fast, they have to already exist in source code. These new tools don&#8217;t add or create the problems. They just find them, filter them out and bring them to the surface for exposure. A better filter in the pool filters out more rubbish.</p>



<p>The more bugs we fix, the fewer bugs remain in the code. Assuming the developers manage to fix problems at a decent enough pace.</p>



<p>For every bugfix we merge, there is a risk that the change itself introduces one more more new separate problems. We also tend to keep adding features and changing behavior as we want to improve our products, and when doing so we occasionally slip up and introduce new problems as well.</p>



<p>Source code analyzing tools is a concept as old as source code itself. There has always existed tools that have tried to identify coding mistakes. Now they <a href="https://daniel.haxx.se/blog/2025/10/10/a-new-breed-of-analyzers/">just recently got better</a> so they can find more mistakes.</p>



<p>These new tools, similar to the old ones, don&#8217;t find <em>all</em> the problems. Even these new modern tools sometimes suggest fixes to the problems they find that are incomplete and in fact sometimes downright buggy.</p>



<p>Undoubtedly code analyzer tooling will improve further. The tools of tomorrow will find even more bugs, some of them were not found when the current generation of tools scanned the code yesterday.</p>



<p>Of course, we now also introduce these tools in CI and general development pipelines, which should make us land better code with fewer mistakes going forward. Ideally.</p>



<p>If we assume that we fix bugs faster than we introduce new ones and we assume that the AI tools can improve further, the question is then more how much more they can improve and for how long that improvement can go on. Will the tools find 10% more bugs? 100%? 1000%? Is the tool improving going to gradually continue for the next two, ten or fifty years? Can they actually find <em>all</em> bugs?</p>



<p>Can we reach the utopia where we have no bugs left in a given software project and when we do merge a new one, it gets detected and fixed almost instantly?</p>



<h2 class="wp-block-heading">Are we close?</h2>



<p>If we assume that there is at least a theoretical chance to reach that point, how would we know when we reach it? Or even just if we are getting closer?</p>



<p>I propose that one way to measure if we are getting closer to <em>zero bugs</em> is to check the age of reported and fixed bugs. If the tools are this good, we should soon only be fixing bugs we introduced very recently.</p>



<p>In the curl project we don&#8217;t keep track of the age of regular bugs, but we do for vulnerabilities. The worst kind of bugs. If the tools can find almost all problems, they should soon only be finding very recently added vulnerabilities too. The age of new finds should plummet and go towards zero.</p>



<p>If the age of newly reported vulnerabilities are getting younger, it should make the average and median age of the total collection go down over time.</p>



<h2 class="wp-block-heading">Average age of vulnerabilities</h2>



<p>The average and median time vulnerabilities had existed in the curl source code by the time they were found and reported to the project.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29731" height="1445" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Screenshot-2026-04-30-at-09-37-07-curl-Project-status-dashboard.png" width="2569" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption">Accumulated vulnerability age when reported</figcaption></figure>
</div>


<h2 class="wp-block-heading">Bugfixes</h2>



<p>When the tools have found most problems there should be less bugs left to fix. The bugfix rate should go down rapidly &#8211; independently of how you count them or how liberal we are in counting exactly what is a bugfix.</p>


<div class="wp-block-image">
<figure class="aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-29736" height="1445" src="https://daniel.haxx.se/blog/wp-content/uploads/2026/04/Screenshot-2026-04-30-at-09-50-17-curl-Project-status-dashboard.png" width="2569" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button><figcaption class="wp-element-caption">Bugfixes</figcaption></figure>
</div>


<p>Given the data from the curl project, there does not seem to be fewer bugfixes done &#8211; yet. Maybe the bugfix speed goes up before it goes down?</p>



<h2 class="wp-block-heading">We are not close</h2>



<p>Given the look of these graphs I don&#8217;t think we are close to <em>zero bugs</em> yet. These two curves do not seem to even start to fall yet.</p>



<p>Yes, these graphs are based on data from a single project, which makes it super weak to draw statistical conclusions from, but this is all I have to work with.</p>



<h2 class="wp-block-heading">So when?</h2>



<p>I think that&#8217;s mostly an indication of what you believe the tooling can do and how good they can eventually end up becoming.</p>



<p>I don&#8217;t know. I will keep fixing bugs.</p>



<p></p>

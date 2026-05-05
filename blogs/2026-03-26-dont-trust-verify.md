---
title: "Don’t trust, verify"
url: "https://daniel.haxx.se/blog/2026/03/26/dont-trust-verify/"
date: "Thu, 26 Mar 2026 10:09:07 +0000"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
<p>Software and digital security should rely on <em>verification</em>, rather than trust. I want to strongly encourage more users and consumers of software to verify curl. And ideally require that you could do at least this level of verification of other software components in your dependency chains.</p>



<h2 class="wp-block-heading">Attacks are omnipresent</h2>



<p>With every source code commit and every release of software, there are risks. Also entirely independent of those.</p>



<p>Some of the things a widely used project can become the victim of, include&#8230;</p>



<ul class="wp-block-list">
<li><em><a href="https://en.wikipedia.org/wiki/XZ_Utils_backdoor">Jia Tan</a></em> is a skilled and friendly member of the project team but is <em>deliberately</em> merging malicious content disguised as something else.</li>



<li>An established committer might have been breached unknowingly and now their commits or releases contain tainted bits.</li>



<li>A rando convinced us to merge what looks like a bugfix but is a small step in a long chain of tiny pieces building up a planted vulnerability or even backdoor</li>



<li>Someone blackmails or extorts an existing curl team member into performing changes not otherwise accepted in the project</li>



<li>A change by an established and well-meaning project member that adds a feature or fixes a bug mistakenly creates a security vulnerability.</li>



<li>The website on which tarballs are normally distributed gets hacked and now evil alternative versions of the latest release are provided, spreading malware.</li>



<li>Credentials of a known curl project member is breached and misinformation gets distributed appearing to be from a <em>known</em> and <em>trusted source</em>. Via email, social media or websites. Could even be this blog!</li>



<li>Something in this list is backed up by an online deep-fake video where a known project member seemingly repeats something incorrect to aid a malicious actor.</li>



<li>A tool used in CI, hosted by a cloud provider, is hacked and runs something malicious</li>



<li>While the primary curl git repository has a downtime, someone online (impersonating a curl team member?) offers a temporary &#8220;curl mirror&#8221; that contains tainted code.</li>
</ul>



<p>In the event any of these would happen, they could of course also happen in combinations and in a rapid sequence.</p>



<h2 class="wp-block-heading">You can verify</h2>



<p>curl, mostly in the shape of libcurl, runs in tens of billions of devices. Clearly one of the most widely used software components in the world.</p>



<p>People ask me how I sleep at night given the vast amount of nasty things that <em>could</em> occur virtually at any point.</p>



<p>There is only one way to combat this kind of insomnia: do everything possible and do it openly and transparently. Make it a little better this week than it was last week. Do software engineering right. Provide means for everyone to verify what we do and what we ship. Iterate, iterate, iterate.</p>



<p>If even just a few users verify that they got a curl release signed by the curl release manager and they verify that the release contents is untainted and only contains bits that originate from the git repository, then we are in a pretty good state. We need enough <em>independent</em> outside users to do this, so that one of them can blow the whistle if anything at any point would look wrong.</p>



<p>I can&#8217;t tell you who these users are, or in fact if they actually exist, as they are and must be completely independent from me and from the curl project. We do however provide all the means and we make it easy for such users to <a href="https://curl.se/docs/verify.html">do this verification</a>.</p>



<h2 class="wp-block-heading">We must verify</h2>



<p>The few outsiders who verify that nothing was tampered with in the releases can only validate that the releases are made from what exists in git. It is our own job to make sure that what exists in git is <em>the real thing</em>. The secure and safe curl.</p>



<p>We must do <em>a lot</em> to make sure that whatever we land in git is okay. Here&#8217;s a list of activities we do.</p>



<ol class="wp-block-list">
<li>we have a consistent code style (invalid style causes errors). This reduces the risk for mistakes and makes it easier to debug existing code.</li>



<li>we ban and avoid a number of &#8220;sensitive&#8221; and &#8220;hard-to-use&#8221; C functions (use of such functions causes errors)</li>



<li>we have a ceiling for complexity in functions to keep them easy to follow, read and understand (failing to do so causes errors)</li>



<li>we review all pull requests before merging, both with humans and with bots. We link back commits to their origin pull requests in commit messages.</li>



<li>we ban use of &#8220;binary blobs&#8221; in git to not provide means for malicious actors to bundle encrypted payloads (trying to include a blob causes errors)</li>



<li>we actively avoid base64 encoded chunks as they too could function as ways to obfuscate malicious contents</li>



<li>we ban most uses of Unicode in code and documentation to avoid easily mixed up characters that look like other characters. (adding Unicode characters causes errors)</li>



<li>we document everything to make it clear how things are supposed to work. No surprises. Lots of documentation is tested and verified in addition to spellchecks and consistent wording.</li>



<li>we have thousands of tests and we add test cases for (ideally) every functionality. Finding &#8220;white spots&#8221; and adding coverage is a top priority. curl runs on countless operating systems, CPU architectures and you can build curl in billions of different configuration setups: not every combination is practically possible to test</li>



<li>we build curl and run tests in over two hundred CI jobs that are run for every commit and every PR. We do not merge commits that have unexplained test failures.</li>



<li>we build curl in CI with the most picky compiler options enabled and we never allow compiler warnings to linger. We always use <code>-Werror</code> that converts warnings to errors and fail the builds.</li>



<li>we run all tests using valgrind and several combinations of sanitizers to find and reduce the risk for memory problems, undefined behavior and similar</li>



<li>we run all tests as &#8220;torture tests&#8221;, where each test case is rerun to have every invoked fallible function call fail once each, to make sure curl never leaks memory or crashes due to this.</li>



<li>we run fuzzing on curl: non-stop as part of Google&#8217;s OSS-Fuzz project, but also briefly as part of the CI setup for every commit and PR</li>



<li>we make sure that the CI jobs we have for curl never &#8220;write back&#8221; to curl. They access the source repository read-only and even if they would be breached, they cannot infect or taint source code.</li>



<li>we run <code>zizmor</code> and other code analyzer tools on the CI job config scripts to reduce the risk of us running or using insecure CI jobs.</li>



<li>we are committed to always fix reported vulnerabilities in the following release. Security problems never linger around once they have been reported.</li>



<li>we document everything and every detail about all curl vulnerabilities ever reported</li>



<li>our commitment to never breaking ABI or API allows all users to easily upgrade to new releases. This enables users to run recent security-fixed versions instead of legacy insecure versions.</li>



<li>our code has been audited several times by external security experts, and the few issues that have been detected in those were immediately addressed</li>



<li>Two-factor authentication on GitHub is mandatory for all committers</li>
</ol>



<p>All this done in the open with full transparency and full accountability. Anyone can follow along and verify that we follow this.</p>



<p>Require this for all your dependencies.</p>



<h2 class="wp-block-heading">Not paranoia</h2>



<p>We plan for the event when someone actually wants and tries to hurt us and our users really bad. Or when that happens by mistake. A successful attack on curl can in theory reach <em>widely</em>.</p>



<p>This is not paranoia. This setup allows us to sleep well at night.</p>



<p><em>This is why users still rely on curl after thirty years in the making.</em></p>



<h2 class="wp-block-heading">Documented</h2>



<p>I recently added a <a href="https://curl.se/docs/verify.html">verify page</a> to the curl website explaining some of what I write about in this post.</p>

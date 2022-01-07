---
id: 302
title: 'How to: change GIT push.default and why you should do it'
date: 2014-03-01T22:31:30+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=302
permalink: /2014/03/01/how-to-change-git-push-default-and-why-you-should-do-it/
categories:
  - git
tags:
  - git
---
How to change GIT push.default and why you should do it.

If you are working with git you need to configure the **push.default** behaviour  
To make sure that git will not merge all my different branches accidentally I choose to set my **default** to **simple**.

Its&#8217; quite easy to set up this you just type:

<pre class="toolbar:2 nums:false lang:default decode:true">git config --global push.default simple</pre>

&nbsp;

If you do not change **push.default** you will get the below text when you try to push git with **git push**

<p style="padding-left: 30px;">
  warning: push.default is unset; its implicit value is changing in<br /> Git 2.0 from &#8216;matching&#8217; to &#8216;simple&#8217;. To squelch this message<br /> and maintain the current behavior after the default changes, use:
</p>

<p style="padding-left: 30px;">
  git config &#8211;global push.default matching
</p>

<p style="padding-left: 30px;">
  To squelch this message and adopt the new behavior now, use:
</p>

<p style="padding-left: 30px;">
  git config &#8211;global push.default simple
</p>

<p style="padding-left: 30px;">
  See &#8216;git help config&#8217; and search for &#8216;push.default&#8217; for further information.<br /> (the &#8216;simple&#8217; mode was introduced in Git 1.7.11. Use the similar mode<br /> &#8216;current&#8217; instead of &#8216;simple&#8217; if you sometimes use older versions of Git)
</p>

<div class="post-text">
  <p>
    The stackoverflow user: <a title="hammar" href="http://stackoverflow.com/users/98117/hammar">hammar</a> describes it very well below:
  </p>
  
  <blockquote title="Pasted from hammar's comment on stackoverflow">
    <p>
      It&#8217;s explained in great detail in <a href="http://git-scm.com/docs/git-config.html">the docs</a> (search for <code>push.default</code> on the page), but I&#8217;ll try to summarize:
    </p>
    
    <ul>
      <li>
        <code>matching</code> means <code>git push</code> will <strong>push all your local branches</strong> to the ones with the same name on the remote. This makes it easy to accidentally push a branch you didn&#8217;t intend to.
      </li>
      <li>
        <code>simple</code> means <code>git push</code> will <strong>push only the current branch to the one that <code>git pull</code> would pull from</strong>, and also checks that their names match. This is a more intuitive behavior, which is why the default is getting changed to this.
      </li>
    </ul>
    
    <p>
      This setting only affects the behavior of your local client, and can be overridden by explicitly specifying which branches you want to push on the command line. Other clients can have different settings, <strong>it only affects what happens when you don&#8217;t specify which branches you want to push</strong>.
    </p>
  </blockquote>
</div>

&nbsp;
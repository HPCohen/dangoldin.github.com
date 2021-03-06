---
layout: post
title: "Identifying duplicate bills across states"
description: "We use the OpenStates API to download bills from various states and compare them against each other in order to find similar language that will indicate bills written under a 3rd party influence."
category:
keywords: "bicoastal datafest, hackathon, politics, laws, natural language processing"
image_url: "/assets/static/images/gun1-in.png"
tags: ["#datascience", "#dataviz", "#code"]
---
{% include setup %}
This past weekend I participated in the <a href="http://www.bdatafest.computationalreporting.com/">Bicoastal Datafest</a> hackathon that brought together journalists and hackers with the goal of analyzing money’s influence in politics. I came in with the idea of analyzing the evolution of a bill in order to see which politician made the various changes and relate that to campaign contributions. I quickly discovered that that wouldn't be very easy, especially in two days, but I did meet <a href="https://twitter.com/llewellynhinkes">Llewellyn</a>, a journalist/hacker, who had a more practical idea of programmatically identifying bills across states that used the same language. The intuition behind this being that it would identify bills that were unlikely to have been written independently of one another and likely to have been influenced by a 3rd party.

We ended up with the following approach that we were able to code up during the weekend:
1. Use the OpenStates API to get the URL of the bills
2. Download the bills and convert each to raw text - from PDF and HTML
3. Extract 8 word phrases from each bill, excluding stopwords
4. See which phrases were duplicated across states
5. Examine the duplicate phrases to see which bills are most likely duplicates

Somewhat surprisingly, this approach led us to discover the following duplicate bills:

<h3>Firearms Freedom Acts</h3>
<p>Shared the phrase: <strong>manufactured without inclusion significant parts imported another state</strong></p>
<ul class="thumbnails">
  <li class="span3">
    <div class="thumbnail">
      <p>
        <a href="http://www.in.gov/legislative/bills/2013/PDF/FISCAL/SB0130.001.pdf">Indiana</a>
      </p>
      <amp-img src="{{ IMG_PATH }}gun1-in.png" alt="Tweets sent by hour" data-src="{{ IMG_PATH }}gun1-in.png"  width="977" height="718" layout="responsive"></amp-img>
    </div>
  </li>
  <li class="span3">
    <div class="thumbnail">
      <p>
        <a href="http://www.legislature.mi.gov/documents/2013-2014/billanalysis/Senate/htm/2013-SFA-0063-S.htm">Michigan</a>
      </p>
      <amp-img src="{{ IMG_PATH }}gun1-mi.png" alt="Tweets sent by hour" data-src="{{ IMG_PATH }}gun1-mi.png"  width="792" height="625" layout="responsive"></amp-img>
    </div>
  </li>
</ul>

<h3>Prohibit US government officials from enforcing firearm-related acts</h3>
<p>Shared the phrase: <strong>accessory ammunition owned manufactured commercially privately state remains</strong></p>
<ul class="thumbnails">
  <li class="span3">
    <div class="thumbnail">
      <p>
        <a href="http://www.azleg.gov//FormatDocument.asp?inDoc=/legtext/51leg/1r/summary/s.1112ps.doc.htm&amp;Session_ID=110">Arizona</a>
      </p>
      <amp-img src="{{ IMG_PATH }}gun2-az.png" alt="Tweets sent by hour" data-src="{{ IMG_PATH }}gun2-az.png"  width="789" height="402" layout="responsive"></amp-img>
    </div>
  </li>
  <li class="span3">
    <div class="thumbnail">
      <p>
        <a href="http://wapp.capitol.tn.gov/apps/billinfo/BillSummaryArchive.aspx?BillNumber=HB0042&amp;ga=108">Tennessee</a>
      </p>
      <amp-img src="{{ IMG_PATH }}gun2-tn.png" alt="Tweets sent by hour" data-src="{{ IMG_PATH }}gun2-tn.png"  width="872" height="505" layout="responsive"></amp-img>
    </div>
  </li>
</ul>

<h3>Prevent pharmaceutical substitution of opioid drugs</h3>
<p>Shared the phrase: <strong>bear labeling claim respect reduction tampering abuse abuse</strong></p>
<ul class="thumbnails">
  <li class="span3">
    <div class="thumbnail">
      <p>
        <a href="http://open.nysenate.gov/legislation/bill/S1753-2013">New York</a>
      </p>
      <amp-img src="{{ IMG_PATH }}drug-ny.png" alt="Tweets sent by hour" data-src="{{ IMG_PATH }}drug-ny.png"  width="924" height="563" layout="responsive"></amp-img>
    </div>
  </li>
  <li class="span3">
    <div class="thumbnail">
      <p>
        <a href="http://www.njleg.state.nj.us/2012/Bills/A3000/2590_S1.HTM">New Jersey</a>
      </p>
      <amp-img src="{{ IMG_PATH }}drug-nj.png" alt="Tweets sent by hour" data-src="{{ IMG_PATH }}drug-nj.png"  width="953" height="666" layout="responsive"></amp-img>
    </div>
  </li>
</ul>

The code's up on <a href="https://github.com/dangoldin/lawdiff">Github</a> so if you have any ideas or improvements - contribute and help out. In two days we were able to get something useful done and it's exciting to see what we can discover if we stick with it.
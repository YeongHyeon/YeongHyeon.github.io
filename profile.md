---
title: About
permalink: "/about/"
layout: post
---

<div class="profile">
  <div class="photo">
    <img src="/images/profile2.png" alt="YeongHyeon Park">
  </div>
  <div>
    <h2>YeongHyeon Park, Ph.D.</h2>
    <p><strong>Research interests:</strong> Anomaly Detection, Computer Vision, Signal Processing</p>
    <ul class="links">
      <li><a href="https://scholar.google.com/citations?hl=en&user=cZq6j0MAAAAJ">Google Scholar</a></li>
      <li><a href="https://github.com/YeongHyeon">GitHub</a></li>
      <li><a href="https://www.linkedin.com/in/yeonghyeon-park-25aa97138/">LinkedIn</a></li>
      <li><a href="{{ "/resume/YeongHyeon_Park-CV.pdf" | relative_url }}">CV (PDF)</a></li>
    </ul>
  </div>
</div>

## Education

<ul class="cv">
  <li><strong>Ph.D.</strong>, Electrical and Computer Engineering — SungKyunKwan University<em>Rep. of Korea · Feb. 2022 – Feb. 2025</em></li>
  <li><strong>M.S.</strong>, Computer and Electronic Systems Engineering — Hankuk University of Foreign Studies<em>Rep. of Korea · Mar. 2018 – Feb. 2020</em></li>
  <li><strong>B.S.</strong>, Digital Information Engineering — Hankuk University of Foreign Studies<em>Rep. of Korea · Feb. 2012 – Feb. 2018</em></li>
</ul>

## Experience

<ul class="cv">
  <li><strong>Postdoctoral Research Fellow</strong>, MD Anderson Cancer Center<em>TX, U.S. · Aug. 2025 – Feb. 2026</em></li>
  <li><strong>Research Engineer</strong>, SK Planet Co., Ltd.<em>Rep. of Korea · Sep. 2019 – Apr. 2025</em></li>
  <li><strong>Research Assistant</strong>, SungKyunKwan University<em>Rep. of Korea · Oct. 2021 – Jan. 2025</em></li>
  <li><strong>Research Assistant</strong>, Hankuk University of Foreign Studies<em>Rep. of Korea · Sep. 2017 – Aug. 2019</em></li>
  <li><strong>Research Intern</strong>, StoryAnt INC.<em>Rep. of Korea · Jan. 2017 – Feb. 2017</em></li>
</ul>

## Activities

### Academic Service

<p><strong>Journal reviewing:</strong>
{% for journal in site.data.reviewing.journals %}<a href="{{ journal.url }}">{{ journal.name }}</a>{% unless forloop.last %} · {% endunless %}{% endfor %}
</p>

<p><strong>Conference reviewing:</strong>
{% for conference in site.data.reviewing.conferences %}<a href="{{ conference.url }}">{{ conference.name }}</a> ({{ conference.years | join: ", " }}){% unless forloop.last %} · {% endunless %}{% endfor %}
</p>

### Additional Activities

<ul class="cv">
  <li>NVIDIA University Ambassador<em><a href="https://learn.nvidia.com/certificates?id=1403c0a68647461485704f0b0041cf86">certificate</a></em></li>
  <li>NVIDIA DLI Instructor<em><a href="https://learn.nvidia.com/certificates?id=96017e53395a4dacb32dfe69be7d2530">certificate</a></em></li>
  <li>Samsung Electronics Social Communication Reporters Group<em>Rep. of Korea · Sep. 2016 – Jan. 2017</em></li>
</ul>

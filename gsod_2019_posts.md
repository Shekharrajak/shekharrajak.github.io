---
layout: default
title: Google Season of Docs 2019
---

<div class="container" style= "padding-top:50px;">
      <!-- Top Navigation -->

      <header class="codrops-header">
        <h1> Google Season of Docs 2019</h1>
        <p> Organization : NumPy & SciPy
        <br> High level restructuring and redesigning of NumPy and SciPy website</p>

      </header>

      <section class="demo-1">
        <div class="grid">

          {% for post in site.categories.gsod2019_post %}
              <a href="{{ site.baseurl }}{{ post.url }}">
                <div class="box">
                  <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
                    <line class="top" x1="0" y1="0" x2="3000" y2="0"/>
                    <line class="left" x1="0" y1="460" x2="0" y2="-920"/>
                    <line class="bottom" x1="0" y1="400" x2="-3000" y2="300"/>
                    <line class="right" x1="0" y1="0" x2="0" y2="0"/>
                  </svg>



                      <h6>{{ post.title }}</h6>
                      <span> GSoD 2019 Report </span>
                      <span> {{ post.week }}  </span>

                      <div class="entry">
                      </div>

                </div>
              </a>
          {% endfor %}
       </div>
      </section>
</div>

{% include footer-front.html %}

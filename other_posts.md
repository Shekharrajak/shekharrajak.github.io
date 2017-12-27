---
layout: default
title: Conferences
---

<div class="container" style= "padding-top:50px;">
			<!-- Top Navigation -->

			<header class="codrops-header">
				<h1> Other blog posts </h1>
				<p> Blogs on different topics and subjects </p>
			</header>

			<section class="demo-1">
				<div class="grid">

          {% for post in site.categories.other %}
              <a href="{{ site.baseurl }}{{ post.url }}">
      					<div class="box">
      						<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
      							<line class="top" x1="0" y1="0" x2="3000" y2="0"/>
      							<line class="left" x1="0" y1="460" x2="0" y2="-920"/>
      							<line class="bottom" x1="0" y1="400" x2="-3000" y2="300"/>
      							<line class="right" x1="0" y1="0" x2="0" y2="0"/>
      						</svg>



                      <h6>{{ post.title }}</h6>
                      <span>  </span>
          						<span> {{ post.week }}  </span>

                      <div class="entry">
                        <!-- {{ post.excerpt }} Instead of this use post.desc where
											desc will be small intro about blog.-->
                      </div>

                </div>
      				</a>
          {% endfor %}


			</div><!--
			</div><!-- /grid -->
			</section>
  </div>

{% include footer-front.html %}
<!--
<div class="posts">
  {% for post in site.posts %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
 </div> -->

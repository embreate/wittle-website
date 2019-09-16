---
title: Inspiration
permalink: "/inspiration/"
layout: default
isInNav: true
---

<section class="mb-5 mt-3 text-center">
    <div class="border-bottom border-warning mt-5">
			<h1 class="text-center text-uppercase">{{page.title}}</h1>
		</div>
    <div class="row justify-content-center mt-3">
      <div class="col-md-6">
        <p>We've collected our favorite examples of the experience of depression being explored across a multitude of media.</p>
      </div>
    </div>
</section>

<section class="text-center mt-5">

  <!-- Categories-->
  <div>
      {% assign categories = "All" %}
      {% for story in site.stories %}
        {% assign categories = categories | concat: story.categories %}
      {%endfor%}
      {% assign categories = categories | uniq %}
      {% for category in categories %}
      <a id="{{category}}" class="catButton btn btn-primary {{category}}" href="#">{{category}}</a>
      {%endfor%}
  </div>

  <br>
  <br>
</section>

<!-- Content -->
<div class="card-columns">
{% assign stories = site.stories | where: "internal", "false" %}
{% for story in stories %}
  <div class="card mb-4 {{story.categories | join: ' '}}">
    <img src="{{ story.image | relative_url }}" class="card-img-top" alt="...">
    <div class="card-body">
      <a href="{{ story.url | relative_url }}"><h5 class="card-title">{{story.title}}</h5></a>
      <p class="card-text">{{story.description}}</p>
      <a href="{{story.link.url}}" target="_blank" class="btn btn-primary">{{story.link.text}}</a>
    </div>
  </div>
{%endfor%}
</div>

<script>
  $(document).ready(function(){
    $(".catButton").click(function(){
      $('.card').hide('fast','linear');
      var id = $(this).attr('id');
      if(id == 'All') {
        $('.card').show('fast','linear');
      } else {
         $('.'+id).show('fast','linear');
      }
    });
  });
  
</script>

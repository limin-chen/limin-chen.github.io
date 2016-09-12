---
layout: all
title: 全部
---

<h2 class="post_title">{{ page.title }}</h2>
<div class="content">
	<div class="post">
		<div class="postlist">
			<ul>
				{% for post in site.posts %}
				{% include archive.html %}
				{% endfor %}
			</ul>
		</div>
	</div>
</div>

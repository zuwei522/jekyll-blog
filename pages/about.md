---
layout: page
title: 关于 / About
description: Love & Share
keywords: Jiang Zuwei, 祖为
comments: true
menu: 关于
permalink: /about/
---

博观而约取，厚积而薄发。

## 联系

<ul>
{% for website in site.data.social %}
<li>{{website.sitename }}：<a href="{{ website.url }}" target="_blank">@{{ website.name }}</a></li>
{% endfor %}
<li>E-mail：<a href="mailto:祖为<jiang@zuwei.top>" target="_blank">jiang@zuwei.top</a></li>
</ul>


## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}

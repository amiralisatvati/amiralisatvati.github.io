---
layout: home
title: "صفحه اصلی"
author_profile: true
---

<div class="hero-wrapper">
  <h1 class="hero-title">تبدیل داده به دانش</h1>
  <p class="hero-subtitle">
    من امیرعلی سطوتی هستم؛ تحلیل‌گر داده و دانشجوی آمار.<br>
    تلاش می‌کنم با ترکیب <strong>آمار</strong>، <strong>برنامه‌نویسی</strong> و <strong>خلاقیت بصری</strong>، راه‌حل‌ه‌ای هوشمند بسازم.
  </p>
  <a href="/about/" class="btn-hero btn-primary-glow">درباره من بیشتر بدانید</a>
  <a href="/blog/" class="btn-hero btn-secondary-outline">مقالات و پروژه‌ها</a>
</div>

## 🛠 جعبه ابزار من

<div style="text-align: center; margin-bottom: 2rem;">
  <span class="skill-tag">R (Semi-Pro)</span>
  <span class="skill-tag">Python (Intermediate)</span>
  <span class="skill-tag">Statistical Analysis</span>
  <span class="skill-tag">Data Visualization</span>
  <span class="skill-tag">Machine Learning</span>
</div>

## 🙋 جدیدترین مقالات

{% for post in site.posts limit:3 %}
<div class="post-card">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p class="post-meta">
    <small>{{ post.date | date: '%d %B %Y' }} | {% include read-time.html %}</small>
  </p>
  <p>{{ post.excerpt }}</p>
  <a href="{{ post.url }}">ادامه مطلب →</a>
</div>
{% endfor %}

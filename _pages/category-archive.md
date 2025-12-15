---
layout: single
title: "دسته‌بندی موضوعات"
permalink: /categories/
author_profile: true
---

<div dir="rtl" style="text-align: right; font-family: Tahoma, sans-serif;">

<div style="background: #e3f2fd; border-right: 5px solid #2196f3; padding: 15px; border-radius: 5px; margin-bottom: 30px; color: #0d47a1;">
  📚 اینجا آرشیو موضوعی مطالب منه. روی هر موضوع کلیک کنی، لیست پست‌هاش رو می‌بینی.
</div>

<style>
  .cat-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 15px;
    margin-bottom: 40px;
  }
  
  .cat-card {
    background: linear-gradient(135deg, #ffffff 0%, #f9f9f9 100%);
    border: 1px solid #eee;
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    text-decoration: none !important;
    color: #333 !important;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }

  .cat-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 15px rgba(0,0,0,0.1);
    border-color: #2196f3;
  }

  .cat-card h3 {
    margin: 10px 0 5px 0;
    font-size: 1rem;
    color: #444;
  }

  .cat-count {
    background: #2196f3;
    color: white;
    font-size: 0.75rem;
    padding: 2px 8px;
    border-radius: 10px;
    display: inline-block;
  }

  .cat-icon {
    font-size: 2rem;
    margin-bottom: 5px;
    display: block;
    opacity: 0.8;
  }

  /* استایل لیست پست‌ها */
  .category-section {
    background: #fff;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 30px;
    border: 1px solid #eee;
  }
  
  .category-header {
    border-bottom: 2px solid #2196f3;
    padding-bottom: 10px;
    margin-bottom: 15px;
    color: #2196f3;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .post-item {
    padding: 8px 0;
    border-bottom: 1px dashed #eee;
    transition: padding-right 0.2s;
  }
  
  .post-item:hover {
    padding-right: 10px;
  }

  .post-item a {
    color: #555;
    text-decoration: none;
    font-weight: 500;
  }
  
  .post-item a:hover {
    color: #2196f3;
  }
  
  .post-date {
    font-size: 0.8em;
    color: #999;
    margin-right: 10px;
  }
</style>

<div class="cat-grid">
  {% for category in site.categories %}
    <a href="#{{ category[0] | slugify }}" class="cat-card">
      <span class="cat-icon">📂</span>
      <h3>{{ category[0] }}</h3>
      <span class="cat-count">{{ category[1].size }} پست</span>
    </a>
  {% endfor %}
</div>

<hr style="margin: 40px 0; border: 0; border-top: 1px solid #ddd;">

{% for category in site.categories %}
  <div id="{{ category[0] | slugify }}" class="category-section">
    <h2 class="category-header">
      <span># {{ category[0] }}</span>
    </h2>
    
    <div style="list-style: none;">
      {% for post in category[1] %}
        <div class="post-item">
          <span style="color: #2196f3;">🔹</span>
          <a href="{{ post.url }}">{{ post.title }}</a>
          <span class="post-date">({{ post.date | date: "%Y-%m-%d" }})</span>
        </div>
      {% endfor %}
    </div>
  </div>
{% endfor %}

</div>
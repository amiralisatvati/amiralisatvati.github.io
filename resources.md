---
layout: single
title: "منابع یادگیری"
permalink: /resources/
author_profile: true
---

<style>
.blog-posts-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

.blog-card {
  background: linear-gradient(135deg, rgba(30, 41, 59, 0.8), rgba(15, 23, 42, 0.9));
  border: 1px solid rgba(100, 116, 139, 0.2);
  border-radius: 12px;
  padding: 1.5rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.blog-card:hover {
  transform: translateY(-4px);
  border-color: rgba(6, 182, 212, 0.5);
  box-shadow: 0 12px 24px rgba(6, 182, 212, 0.15);
}

.blog-card-icon {
  width: 48px;
  height: 48px;
  background: linear-gradient(135deg, rgba(6, 182, 212, 0.2), rgba(139, 92, 246, 0.2));
  border: 1px solid rgba(6, 182, 212, 0.3);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  color: #06b6d4;
  margin-bottom: 1rem;
}

.blog-card-tags {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  margin-bottom: 0.75rem;
}

.blog-tag {
  font-size: 0.75rem;
  font-family: 'Courier New', monospace;
  background: rgba(6, 182, 212, 0.1);
  color: rgba(6, 182, 212, 0.9);
  border: 1px solid rgba(6, 182, 212, 0.2);
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
}

.blog-card-title {
  font-size: 1.125rem;
  font-weight: 700;
  color: #fff;
  margin: 0.5rem 0;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.blog-card-title:hover {
  color: #06b6d4;
}

.blog-card-desc {
  font-size: 0.875rem;
  color: #94a3b8;
  margin: 0.5rem 0;
  line-height: 1.5;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.blog-card-date {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.75rem;
  color: #64748b;
  margin-top: 1rem;
}

.page-intro {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 3rem;
}

.page-intro h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #06b6d4, #8b5cf6, #10b981);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.page-intro p {
  font-size: 1.125rem;
  color: #94a3b8;
}
</style>

<div class="page-intro">
  <h1>📚 منابع یادگیری</h1>
  <p>مجموعه منتخب از مطالب آموزشی، پست‌های بلاگ و منابع یادگیری</p>
</div>

<div class="blog-posts-grid">
  {% for post in site.posts %}
  <a href="{{ post.url | relative_url }}" class="blog-card" style="text-decoration: none;">
    <div class="blog-card-icon">
      <i class="fas fa-file-alt"></i>
    </div>
    
    {% if post.tags %}
    <div class="blog-card-tags">
      {% for tag in post.tags limit:2 %}
      <span class="blog-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
    
    <h3 class="blog-card-title">{{ post.title }}</h3>
    
    {% if post.description %}
    <p class="blog-card-desc">{{ post.description }}</p>
    {% endif %}
    
    <div class="blog-card-date">
      <i class="far fa-calendar"></i>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </div>
  </a>
  {% endfor %}
</div>

{% if site.posts.size == 0 %}
<div style="text-align: center; padding: 3rem; color: #64748b;">
  <i class="fas fa-inbox" style="font-size: 3rem; margin-bottom: 1rem;"></i>
  <p>هنوز پستی منتشر نشده است.</p>
</div>
{% endif %}

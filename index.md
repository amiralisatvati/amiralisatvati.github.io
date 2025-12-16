---
layout: home
title: "صفحه اصلی"
author_profile: true
---

<style>
.hero-wrapper {
  text-align: center;
  padding: 4rem 1rem;
  background: radial-gradient(circle at top right, rgba(124, 58, 237, 0.2), transparent 40%),
              radial-gradient(circle at bottom left, rgba(0, 212, 255, 0.1), transparent 40%);
  border-radius: 16px;
  margin-bottom: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.hero-title {
  font-size: 2.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, #fff 0%, #00d4ff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 1rem;
}

.hero-subtitle {
  font-size: 1.2rem;
  color: #a1a1aa;
  max-width: 600px;
  margin: 0 auto 2rem;
}

.btn-hero {
  display: inline-block;
  padding: 12px 32px;
  border-radius: 50px;
  font-weight: 700;
  text-decoration: none !important;
  transition: all 0.3s ease;
  margin: 0 10px;
}

.btn-primary-glow {
  background: linear-gradient(90deg, #7c3aed, #00d4ff);
  color: #fff !important;
  box-shadow: 0 4px 15px rgba(0, 212, 255, 0.3);
}

.btn-primary-glow:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 212, 255, 0.4);
}

.btn-secondary-outline {
  background: transparent;
  color: #00d4ff !important;
  border: 2px solid #00d4ff;
}

.btn-secondary-outline:hover {
  background: rgba(0, 212, 255, 0.1);
}

.skill-tag {
  display: inline-block;
  padding: 8px 16px;
  margin: 6px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid #7c3aed;
  border-radius: 8px;
  font-size: 0.9rem;
  color: #00d4ff;
  transition: all 0.3s ease;
}

.skill-tag:hover {
  background: rgba(124, 58, 237, 0.15);
  border-color: #00d4ff;
}

.post-card {
  background: rgba(26, 31, 58, 0.7);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1rem;
  transition: all 0.3s ease;
}

.post-card:hover {
  border-color: #00d4ff;
  box-shadow: 0 4px 20px rgba(0, 212, 255, 0.2);
}
</style>

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
  <h3><a href="{{ post.url }}" style="color: #00d4ff; text-decoration: none;">{{ post.title }}</a></h3>
  <p class="post-meta" style="color: #a1a1aa;">
    <small>{{ post.date | date: '%d %B %Y' }}</small>
  </p>
  <p style="color: #e4e4e7;">{{ post.excerpt }}</p>
  <a href="{{ post.url }}" style="color: #00d4ff;">ادامه مطلب →</a>
</div>
{% endfor %}

---
layout: single
title: "آرشیو مطالب"
permalink: /posts/
author_profile: true
---

<div dir="rtl" style="text-align: right; font-family: Tahoma, sans-serif;">

<div class="search-container">
  <input type="text" id="searchInput" onkeyup="filterPosts()" placeholder="🔍 دنبال چه مطلبی می‌گردی؟ اینجا بنویس...">
</div>

<style>
  /* استایل باکس جستجو */
  .search-container {
    margin-bottom: 40px;
    position: relative;
  }
  
  #searchInput {
    width: 100%;
    padding: 15px 20px;
    font-size: 1.1rem;
    border: 2px solid #eee;
    border-radius: 50px;
    background: #fdfdfd;
    transition: all 0.3s ease;
    font-family: inherit;
    box-shadow: 0 4px 6px rgba(0,0,0,0.02);
  }

  #searchInput:focus {
    border-color: #2196f3;
    outline: none;
    box-shadow: 0 4px 15px rgba(33, 150, 243, 0.2);
  }

  /* استایل سال‌ها */
  .year-header {
    font-size: 1.8rem;
    color: #e0e0e0;
    font-weight: 900;
    margin: 40px 0 20px 0;
    position: relative;
    padding-right: 15px;
  }
  
  .year-header::before {
    content: '';
    position: absolute;
    right: 0;
    top: 10px;
    height: 70%;
    width: 4px;
    background: #2196f3;
    border-radius: 2px;
  }

  /* استایل گرید پست‌ها */
  .posts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
  }

  /* استایل کارت پست */
  .post-card {
    background: white;
    border: 1px solid #f0f0f0;
    border-radius: 12px;
    padding: 20px;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    position: relative;
    top: 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    box-shadow: 0 2px 5px rgba(0,0,0,0.02);
  }

  .post-card:hover {
    top: -5px;
    box-shadow: 0 10px 20px rgba(0,0,0,0.08);
    border-color: #bbdefb;
  }

  .post-card h3 {
    margin: 0 0 10px 0;
    font-size: 1.1rem;
    line-height: 1.5;
  }

  .post-card h3 a {
    text-decoration: none;
    color: #333;
    transition: color 0.2s;
  }

  .post-card h3 a:hover {
    color: #2196f3;
  }

  .post-meta {
    font-size: 0.85rem;
    color: #888;
    margin-top: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px dashed #eee;
    padding-top: 10px;
  }

  .post-cat {
    background: #e3f2fd;
    color: #1976d2;
    padding: 2px 8px;
    border-radius: 4px;
    font-size: 0.75rem;
    font-weight: bold;
  }

  .no-result {
    text-align: center;
    color: #999;
    padding: 20px;
    display: none;
    font-size: 1.2rem;
  }
</style>

{% assign postsByYear = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}

<div id="postsContainer">
  {% for year in postsByYear %}
    <div class="year-group">
      <div class="year-header">{{ year.name }}</div>
      <div class="posts-grid">
        {% for post in year.items %}
          <div class="post-card">
            <div>
              <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
              <p style="font-size: 0.9em; color: #666; margin-bottom: 0;">
                {{ post.excerpt | strip_html | truncate: 80 }}
              </p>
            </div>
            <div class="post-meta">
              <span>📅 {{ post.date | date: "%Y/%m/%d" }}</span>
              {% if post.categories.size > 0 %}
                <span class="post-cat">{{ post.categories | first }}</span>
              {% endif %}
            </div>
            <span style="display:none;">{{ post.title }} {{ post.excerpt }} {{ post.categories }}</span>
          </div>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
</div>

<div id="noResult" class="no-result">
  😔 متاسفانه پستی با این عنوان پیدا نشد.
</div>

<script>
function filterPosts() {
  var input, filter, container, cards, i, txtValue, yearGroups, foundAny;
  input = document.getElementById('searchInput');
  filter = input.value.toUpperCase();
  container = document.getElementById("postsContainer");
  cards = container.getElementsByClassName('post-card');
  yearGroups = container.getElementsByClassName('year-group');
  foundAny = false;

  // جستجو در کارت‌ها
  for (i = 0; i < cards.length; i++) {
    // جستجو در تایتل و متن مخفی
    txtValue = cards[i].innerText || cards[i].textContent;
    if (txtValue.toUpperCase().indexOf(filter) > -1) {
      cards[i].style.display = "";
      foundAny = true;
    } else {
      cards[i].style.display = "none";
    }
  }

  // مدیریت نمایش سال‌ها (اگر همه پست‌های یک سال مخفی شد، سال هم مخفی شود)
  for (i = 0; i < yearGroups.length; i++) {
    var visibleCards = yearGroups[i].querySelectorAll('.post-card:not([style*="display: none"])');
    if (visibleCards.length > 0) {
      yearGroups[i].style.display = "";
    } else {
      yearGroups[i].style.display = "none";
    }
  }

  // پیام پیدا نشد
  if (!foundAny) {
    document.getElementById("noResult").style.display = "block";
  } else {
    document.getElementById("noResult").style.display = "none";
  }
}
</script>

</div>
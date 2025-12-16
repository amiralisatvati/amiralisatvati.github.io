---
layout: single
title: "شبیه‌سازی اعداد تصادفی در R"
date: 2025-12-15
categories: [R, Statistics]
tags: [simulation, random-numbers, coding]
excerpt: "بررسی روش‌های تولید اعداد تصادفی و شبیه‌سازی‌های آماری در R"
read_time: true
---

## مقدمه

در این پروژه به بررسی روش‌های تولید اعداد تصادفی (Random Number Generation) در زبان R می‌پردازیم. اعداد تصادفی پایه و اساس بسیاری از شبیه‌سازی‌های آماری (Simulation) هستند.

### کود نمونه در R

```r
# تنظیم Seed برای تکرارپذیری
set.seed(123)

# تولید ۱۰۰ عدد نرمال استاندارد
data <- rnorm(100, mean = 0, sd = 1)

# رسم هیستوگرام
hist(data, main="توزیع نرمال شبیه‌سازی شده", col="lightblue")
```

### روش‌های تولید اعداد

**1. Uniform Distribution**
```r
# اعداد یكنواخت مطالعه بیشتر مبحث نا رنجها را نگاه کنید.
uniform <- runif(1000, min = 0, max = 1)
```

**2. Normal Distribution**
```r
normal <- rnorm(1000, mean = 100, sd = 15)
```

**3. Poisson Distribution**
```r
poisson <- rpois(1000, lambda = 5)
```

---

## نتیجه‌گیری

اعداد تصادفی ابزار قوي برای متالع رفتار سیستم‌های پیچیده در شرایط مختلف هستند.

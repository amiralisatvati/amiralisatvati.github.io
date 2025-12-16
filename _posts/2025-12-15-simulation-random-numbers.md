---
layout: single
title: "فصل ۳ شبیه‌سازی: روشهای تولید اعداد تصادفی"
date: 2025-12-15
categories: [R, Statistics, Simulation]
tags: [simulation, random-numbers, lcg, methodology]
excerpt: "جزوه کامل فصل ۳ شبیه‌سازی - روشهای تولید اعداد تصادفی: روش میان‌مربع، همنهشتی خطی (LCG) و تست‌های یکنواختی"
read_time: true
---

## مقدمه

اعداد تصادفی پایه و اساس بسیاری از شبیه‌سازی‌های آماری هستند. این فصل روش‌های مختلف تولید اعداد تصادفی را بررسی می‌کند.

## ۱. روش میان‌مربع (Middle Square Method)

### تاریخچه

روش میان‌مربع توسط جان فون نویمان در سال ۱۹۴۶ ارائه شد.

### الگوریتم

1. عددی شش‌رقمی به عنوان بذر انتخاب کنید (مثلاً x₀ = 123456)
2. x₀ را مربع کنید: x₀² = 15241578750656
3. ۶ رقم میانی را استخراج کنید: x₁ = 241578
4. این عدد را بر 10⁶ تقسیم کنید: u₁ = 0.241578
5. برای تولید عدد بعدی، مرحله ۲ را تکرار کنید

### مثال عملی در R

```r
middle_square <- function(seed, n) {
  results <- numeric(n)
  x <- seed
  
  for (i in 1:n) {
    x <- x^2
    # استخراج ۶ رقم میانی
    x <- as.numeric(substr(as.character(x), 4, 9))
    results[i] <- x / 1e6
  }
  
  return(results)
}

# استفاده
random_nums <- middle_square(123456, 10)
print(random_nums)
```

### مشکلات

- ❌ دوره‌های کوتاه (cycle)
- ❌ خصوصیات آماری ضعیف
- ❌ اگر به صفر برسد، تمام اعداد بعدی صفر می‌شوند

## ۲. روش همنهشتی خطی (Linear Congruential Generator - LCG)

### تعریف

روش LCG یک روش بسیار محبوب برای تولید اعداد شبه‌تصادفی است.

### فرمول

$$x_{n+1} = (a \cdot x_n + c) \mod m$$

جایی که:
- **a**: مضروب (multiplier)
- **c**: افزایش (increment)
- **m**: مدولوس (modulus)
- **x₀**: بذر (seed)

### پارامترهای معروف

| نام | a | c | m | منبع |
|-----|---|---|-|------|
| MINSTD | 16807 | 0 | 2³¹-1 | Park & Miller |
| RANDU | 65539 | 0 | 2³¹ | IBM |
| Numerical Recipes | 1664525 | 1013904223 | 2³² | Press et al. |

### پیاده‌سازی در R

```r
lcg <- function(seed, n, a = 1664525, c = 1013904223, m = 2^32) {
  results <- numeric(n)
  x <- seed
  
  for (i in 1:n) {
    x <- (a * x + c) %% m
    results[i] <- x / m
  }
  
  return(results)
}

# مثال
random_lcg <- lcg(123456, 1000)

# رسم هیستوگرام
hist(random_lcg, breaks = 50, main = "LCG Generated Uniform Random Numbers")
```

### مزایا
- ✅ سریع و موثر
- ✅ آسان به پیاده‌سازی
- ✅ دوره طولانی

### معایب
- ❌ ارتباطات پی‌درپی
- ❌ بیتهای کم‌ارتباط ضعیف‌تر هستند

## ۳. تست‌های یکنواختی (Uniformity Tests)

### تست Chi-Square

تقسیم بازه [0,1) به k بازه مساوی و بررسی:

$$\chi^2 = \sum_{i=1}^{k} \frac{(O_i - E_i)^2}{E_i}$$

**در R:**
```r
chi_square_test <- function(random_nums, k = 10) {
  expected <- length(random_nums) / k
  observed <- table(cut(random_nums, breaks = k))
  
  chi_sq <- sum((observed - expected)^2 / expected)
  p_value <- 1 - pchisq(chi_sq, df = k - 1)
  
  return(list(chi_sq = chi_sq, p_value = p_value))
}

# استفاده
test_result <- chi_square_test(random_lcg)
print(test_result)
```

### تست Kolmogorov-Smirnov

```r
ks_test <- function(random_nums) {
  return(ks.test(random_nums, "punif"))
}

# استفاده
ks_result <- ks_test(random_lcg)
print(ks_result)
```

## ۴. مقایسهٔ روش‌ها

| معیار | Middle Square | LCG | Modern Generators |
|--------|---------------|-----|-------------------|
| سرعت | متوسط | سریع | سریع |
| کیفیت | ضعیف | متوسط | عالی |
| دوره | کوتاه | متوسط | خیلی طولانی |
| استفاده | تاریخی | محدود | گسترده |

## ۵. مثال عملی: شبیه‌سازی پرتاب تاس

```r
# تولید 10000 پرتاب تاس
simulation_dice <- function(n = 10000) {
  random_nums <- random_lcg(123456, n)
  # تبدیل به اعداد 1-6
  dice_rolls <- floor(random_nums * 6) + 1
  
  # رسم جدول فراوانی
  print(table(dice_rolls))
  
  # رسم هیستوگرام
  hist(dice_rolls, breaks = 0:7, main = "Simulation of Dice Rolls")
}

simulation_dice()
```

## نتیجه‌گیری

- روش میان‌مربع اکنون **منسوخ** است
- LCG هنوز برای **مقاصد ساده** استفاده می‌شود
- برای **مقاصد جدی** از Mersenne Twister یا newer generators استفاده کنید

## منابع

1. Knuth, D. E. (1997). The Art of Computer Programming, Vol. 2
2. L'Ecuyer, P. (1994). Uniform random number generation
3. Park, S. K., & Miller, K. W. (1988). Random number generators

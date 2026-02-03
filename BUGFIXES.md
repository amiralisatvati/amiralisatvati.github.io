# 🐛 Bug Fixes Applied - February 2026

This document tracks all bugs that were identified and fixed in the portfolio website.

## ✅ Fixed Issues

### 1. **Open Graph URL Mismatch** (🔴 Critical)
- **Problem**: `og:url` had incorrect domain with hyphen: `amirali-satvati.github.io`
- **Fix**: Updated to correct domain: `amiralisatvati.github.io`
- **Location**: `index.html` line 19
- **Commit**: [05e19fe](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/05e19fe9bf2b1b3457431d4e46328ba4323f609e)

### 2. **Missing Twitter Card Image** (🟡 High)
- **Problem**: `twitter:image` meta tag was missing, affecting social media shares
- **Fix**: Added `twitter:image` meta tag with proper image URL
- **Location**: `index.html` line 27
- **Commit**: [05e19fe](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/05e19fe9bf2b1b3457431d4e46328ba4323f609e)

### 3. **Static Language Attribute** (🟡 High)
- **Problem**: HTML `lang` attribute was always `"en"` even when switching to Persian
- **Fix**: Added dynamic language switching with `id="html-root"` and updated `toggleLanguage()` function
- **Location**: `index.html` line 3 & JavaScript section
- **Commit**: [05e19fe](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/05e19fe9bf2b1b3457431d4e46328ba4323f609e)

### 4. **Mysterious 'bar' File** (🟢 Medium)
- **Problem**: Unknown file `bar` with no clear purpose existed in repository root
- **Fix**: Removed the file completely
- **Commit**: [6f8ca04](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/6f8ca049d3ea2b051f0df3560aae09c99846a622)

### 5. **Invalid Sitemap URLs** (🟡 High)
- **Problem**: Sitemap included non-existent pages: `/about/`, `/projects/`, `/blog/`
- **Fix**: Updated sitemap to only include actual pages and updated lastmod date
- **Location**: `sitemap.xml`
- **Commit**: [70bb0b1](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/70bb0b120fc0665d746610b9150a583a35c9af9e)

### 6. **Missing LinkedIn in Config** (🟢 Medium)
- **Problem**: LinkedIn link was in `index.html` but not defined in `_config.yml`
- **Fix**: Added LinkedIn configuration to `_config.yml` author.links section
- **Location**: `_config.yml`
- **Commit**: [08e74c1](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/08e74c192242d5ade700b6f8d999bc0a8b3b7235)

### 7. **Improved Accessibility** (🟢 Medium)
- **Problem**: Language toggle buttons lacked descriptive `aria-label` attributes
- **Fix**: Added comprehensive `aria-label` descriptions for screen readers
- **Location**: `index.html` navigation section
- **Commit**: [05e19fe](https://github.com/amiralisatvati/amiralisatvati.github.io/commit/05e19fe9bf2b1b3457431d4e46328ba4323f609e)

---

## 🚫 Known Limitations

Some issues identified but not fixed yet:

### 1. **PWA Icons Missing** (🟡 High)
- **Issue**: `site.webmanifest` references icon files that don't exist in `/assets/`
- **Current Workaround**: Using ui-avatars.com API for dynamic icon generation
- **Future Fix**: Create and upload actual icon files (192x192 and 512x512)

### 2. **Open Graph Image** (🟢 Medium)
- **Issue**: Referenced OG image `/assets/og-image.jpg` doesn't exist
- **Current Status**: Social media platforms will use fallback images
- **Future Fix**: Create and upload a custom OG image

---

## 🔙 How to Rollback

If you need to revert these changes:

```bash
# Revert to backup branch
git checkout backup-fixes-part1

# Or revert to specific commit before fixes
git revert 08e74c1..05e19fe
```

**Backup Branch**: [`backup-fixes-part1`](https://github.com/amiralisatvati/amiralisatvati.github.io/tree/backup-fixes-part1)

---

## 📊 Statistics

- **Total Bugs Fixed**: 7
- **Critical**: 1
- **High**: 3
- **Medium**: 3
- **Files Modified**: 3 (`index.html`, `sitemap.xml`, `_config.yml`)
- **Files Deleted**: 1 (`bar`)
- **Total Commits**: 4

---

## 👥 Credits

**Fixed by**: Perplexity AI Assistant  
**Requested by**: @amiralisatvati  
**Date**: February 3, 2026  

---

### 🔗 Useful Links

- [🏠 Live Website](https://amiralisatvati.github.io)
- [💾 Repository](https://github.com/amiralisatvati/amiralisatvati.github.io)
- [🔄 Backup Branch](https://github.com/amiralisatvati/amiralisatvati.github.io/tree/backup-fixes-part1)

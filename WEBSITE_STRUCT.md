# Stromy Website Structure

This document provides a high-level overview of the website's page hierarchy, navigation, and internal linking structure.

## Site Overview

- **Base URL**: https://corentin-tin.github.io/
- **Static Site Generator**: Hugo (Extended)
- **Theme**: hugo-saasify-theme
- **Languages**: English (default), Chinese (zh-cn)

---

## Page Hierarchy

```
/ (Homepage)
├── /features/
│   ├── /performance/           → Lightning-Fast Performance
│   ├── /design-system/         → Beautiful Design System
│   └── /developer-experience/  → Developer Experience
│
├── /pricing/                   → Pricing Plans & FAQ
│
├── /blog/                      → Blog Listing
│   ├── /getting-started-with-hugo/
│   ├── /optimizing-hugo-performance/
│   ├── /deploying-hugo-sites/
│   ├── /content-management-hugo/
│   └── /customizing-your-hugo-theme/
│
├── /company/                   → About Us, Leadership, Investors
│
├── /careers/                   → Join Our Team
│   └── /jobs/
│       ├── /senior-frontend-developer/
│       └── /product-manager/
│
├── /privacy/                   → Privacy Policy
├── /license/                   → MIT License
│
└── /zh-cn/                     → Chinese translations
    ├── / (homepage)
    └── /blog/example-post/
```

---

## Navigation Structure

### Header Menu

```
┌─────────────────────────────────────────────────────────┐
│  [Logo]  Features ▾  Pricing  Blog  Company ▾  [Sign In] [Get Started]  │
└─────────────────────────────────────────────────────────┘
              │                         │
              │                         └─── About Us → /company/
              │                              Careers → /careers/
              │
              └─── Performance → /features/performance/
                   Design System → /features/design-system/
                   Developer Experience → /features/developer-experience/
```

### Footer Menu (3 Columns)

```
┌──────────────────┬──────────────────┬──────────────────┐
│    FEATURES      │     COMPANY      │      LEGAL       │
├──────────────────┼──────────────────┼──────────────────┤
│ Performance      │ Blog             │ License          │
│ Design System    │ About Us         │ Privacy Policy   │
│ Developer Exp.   │ Careers          │                  │
└──────────────────┴──────────────────┴──────────────────┘
```

---

## Internal Linking Flow

### From Homepage (/)

The homepage is the central hub connecting to all major sections:

```
Homepage
├── Hero CTAs
│   ├── Primary CTA → /get-started
│   └── Secondary CTA → /demo
│
├── Feature Blocks
│   ├── Performance → /features/performance/
│   ├── Design System → /features/design-system/
│   └── Developer Experience → /features/developer-experience/
│
└── Global CTA Section
    ├── Primary CTA → /get-started
    └── Secondary CTA → /demo
```

### Feature Pages (/features/*)

Each feature page includes:
- Standalone content (no cross-links to other features)
- Back to homepage via header navigation
- Access to all sections via footer

### Company Section (/company/)

```
Company Page
├── Leadership Team
│   ├── William Masquelier → [LinkedIn Profile]
│   └── Corentin Merlé → [LinkedIn Profile]
│
├── Investors Section (4 investors with logos)
├── Company Values (3 values)
└── Company Stats
```

### Careers & Jobs Flow

```
/careers/ → Join Our Team
    │
    └── Displays job listings from:
        ├── /jobs/senior-frontend-developer/
        └── /jobs/product-manager/
```

### Blog Section (/blog/)

```
Blog Listing Page
├── Individual Posts
│   ├── /blog/getting-started-with-hugo/
│   ├── /blog/optimizing-hugo-performance/
│   ├── /blog/deploying-hugo-sites/
│   ├── /blog/content-management-hugo/
│   └── /blog/customizing-your-hugo-theme/
│
└── Taxonomies (Categories & Tags)
    └── Auto-generated listing pages
```

---

## Key Components & Sections

### Homepage Sections (in order)
1. **Hero Section** - Main value proposition with CTAs
2. **Client Logos** - 5 customer logos
3. **Features Section** - 3 feature blocks (linked to feature pages)
4. **Testimonials** - 3 customer testimonials
5. **Global CTA** - Final call-to-action before footer

### Feature Pages (consistent structure)
- Badge indicator (color-coded by type)
- Main heading and description
- Feature list (4 key features)
- Technical details section
- Visual mockup/screenshot

### Company Page Sections
- Mission statement
- Leadership team (2 members)
- Investors (4 investors)
- Company values (3 values)
- Company statistics

### Pricing Page Components
- 2 pricing tables
- 6 total plans (Starter, Company, Enterprise + Basic, Professional, Business)
- FAQ section (5 questions)

---

## External Links

### Social Media (configured in hugo.toml)
- LinkedIn, Twitter/X, Bluesky, YouTube, Facebook
- Instagram, GitHub, Telegram, Discord, Slack
- Medium, Dribbble, Behance

### Team Links
- Leadership LinkedIn profiles (William Masquelier, Corentin Merlé)

### Attribution
- Designer credit → Chaoming Li

---

## Multilingual Setup

### English (default)
- All pages available at root level

### Chinese (zh-cn)
- Homepage: `/zh-cn/`
- Sample blog post: `/zh-cn/blog/example-post/`
- Configured for expansion

---

## User Journey Examples

### Discovery Journey
```
Homepage → Feature (Performance/Design/Dev) → Pricing → Get Started
```

### Learning Journey
```
Homepage → Blog → Specific Tutorial → Related Posts (via categories/tags)
```

### Company Information Journey
```
Homepage → Company → Leadership/Values → Careers → Job Posting
```

### Quick Navigation (via Footer)
```
Any Page → Footer Menu → Direct access to Features/Company/Legal sections
```

---

## Notes

- All header menu items are accessible from every page
- Footer provides consistent navigation across all pages
- Homepage serves as the primary hub for feature discovery
- Blog uses Hugo's taxonomy system for content organization
- Careers page dynamically lists jobs from `/jobs/` directory
- Multilingual content follows Hugo's standard `/[lang]/` structure

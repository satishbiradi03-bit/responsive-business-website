# Production Portfolio Implementation Plan

## Overview
Personal software builder portfolio using Next.js 14+, TypeScript, Tailwind CSS with:
- Type-safe data structure for easy customization
- Server-side form validation
- SEO optimization (metadata, sitemaps, robots.txt)
- Accessible keyboard navigation
- Mobile-first responsive design

---

## File Structure

```
responsive-business-website/
├── src/
│   ├── app/
│   │   ├── layout.tsx              # Root layout with metadata, fonts
│   │   ├── page.tsx                # Home page
│   │   ├── work/
│   │   │   └── page.tsx            # Portfolio/work page
│   │   ├── services/
│   │   │   └── page.tsx            # Services page
│   │   ├── about/
│   │   │   └── page.tsx            # About page
│   │   ├── contact/
│   │   │   └── page.tsx            # Contact page
│   │   ├── robots.ts               # SEO: robots.txt
│   │   ├── sitemap.ts              # SEO: dynamic sitemap
│   │   └── api/
│   │       └── contact/
│   │           └── route.ts        # Server action for form submission
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Header.tsx          # Navigation header
│   │   │   ├── Footer.tsx          # Footer with links
│   │   │   └── Container.tsx       # Max-width wrapper
│   │   ├── common/
│   │   │   ├── Button.tsx          # Reusable button
│   │   │   ├── Card.tsx            # Reusable card
│   │   │   ├── Badge.tsx           # Tag/skill badge
│   │   │   └── SectionHeading.tsx  # Section titles
│   │   └── sections/
│   │       ├── Hero.tsx            # Home hero section
│   │       ├── CTA.tsx             # Call-to-action block
│   │       └── ContactForm.tsx     # Reusable form
│   ├── data/
│   │   └── portfolio.ts            # All portfolio data (typed, easily replaceable)
│   ├── types/
│   │   └── index.ts                # TypeScript interfaces
│   ├── lib/
│   │   ├── cn.ts                   # classNames utility
│   │   └── validation.ts           # Form validation logic
│   └── styles/
│       └── globals.css             # Global Tailwind directives
├── public/
│   ├── favicon.ico
│   └── robots.txt                  # Fallback (generated in app/robots.ts)
├── package.json
├── tsconfig.json
├── tailwind.config.ts
├── next.config.js
└── .env.local (example)            # Environment variables
```

---

## Key Features & Implementation Details

### 1. **Data Structure** (`src/data/portfolio.ts`)
- Single, typed source of truth for all portfolio content
- Easy to replace: name, title, bio, projects, services, contact info
- No hardcoded strings across components

### 2. **Pages**
| Page | Purpose | Key Sections |
|------|---------|--------------|
| **Home** | First impression | Hero, 2-3 featured projects, CTA, testimonial placeholder |
| **Work** | Full portfolio | All projects with descriptions, tech stack, links |
| **Services** | What I offer | Service cards with descriptions |
| **About** | Professional background | Bio, skills, experience highlights |
| **Contact** | Inquiry & collaboration | Server-validated form, contact info |

### 3. **Components**
- **Reusable**: Button, Card, Badge, SectionHeading
- **Layout**: Header, Footer, Container (max-width wrapper)
- **Sections**: Hero, CTA, ContactForm
- **Accessibility**: ARIA labels, keyboard nav, semantic HTML

### 4. **SEO & Meta**
- `layout.tsx`: Global metadata, Open Graph, Twitter cards
- `robots.ts`: Dynamic robots.txt generation
- `sitemap.ts`: Dynamic XML sitemap
- Each page: Custom metadata override via `generateMetadata()`

### 5. **Form Handling**
- Server action in `app/api/contact/route.ts`
- Client-side validation + server-side validation
- Spam protection placeholder (rate limiting pattern)
- No actual email sending (user configures)

### 6. **Styling**
- Tailwind CSS utility-first
- Custom config for consistent spacing, colors, typography
- CSS variables for easy theme switching
- Mobile-first breakpoints

### 7. **Accessibility**
- Semantic HTML (`<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`)
- ARIA labels on interactive elements
- Keyboard navigation (Tab, Enter, Escape)
- Focus indicators on buttons/links
- Alt text on images (when present)
- Color contrast compliance

---

## Tech Stack

| Technology | Purpose |
|------------|---------|
| **Next.js 14+** | React framework with App Router, server components |
| **TypeScript** | Type safety, better DX |
| **Tailwind CSS** | Utility-first styling |
| **React Hook Form** | (Optional) Lightweight form state |
| **Zod** | Schema validation for form data |

---

## Development Flow

1. **Phase 1**: Set up project structure, install dependencies
2. **Phase 2**: Create reusable components (Button, Card, etc.)
3. **Phase 3**: Build layout components (Header, Footer)
4. **Phase 4**: Create data structure and types
5. **Phase 5**: Build pages (Home → About → Services → Work → Contact)
6. **Phase 6**: Implement form handling with validation
7. **Phase 7**: Add SEO (metadata, robots, sitemap)
8. **Phase 8**: Testing and optimization

---

## Data Replacement Guide

All customizable content lives in `src/data/portfolio.ts`. Structure:

```typescript
export const portfolio = {
  personal: { name, title, bio, email, phone, social },
  projects: [ { title, description, tech, link, year } ],
  services: [ { title, description, icon? } ],
  testimonials: [ { text, author, role } ], // placeholder only
  experience: [ { role, company, duration, description } ],
}
```

Simply update these values to customize the entire site.

---

## Next Steps

1. Confirm file structure ✓
2. Initialize Next.js project
3. Install dependencies
4. Create TypeScript types
5. Create reusable components (one at a time)
6. Build out pages
7. Add form handling & validation
8. Configure SEO

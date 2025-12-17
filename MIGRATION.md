# Migration from GitBook to Mintlify

This document outlines the changes made when migrating Universal Protocol documentation from GitBook to Mintlify.

## Original Structure (GitBook)

```
docs.universal.xyz/docs/

Introduction to Universal
├── Introduction to Universal
├── Universal Protocol Overview
├── Introduction to uAssets
├── Frequently Asked Questions
└── Proof of Reserves

DEVELOPERS
├── Building with uAssets
├── Integrate the Universal API
├── Integrate the Issuance & Redemption Universal API
├── Contract Addresses
├── Partnerships
└── uAsset Logos

Community
├── Twitter/X
└── Discord

Links
├── Buy Universal Assets
├── Mint or Redeem with native assets
├── Whitepaper
├── Disclaimer
├── Terms of Service
├── Universal EVM Audit
└── Universal Solana Audit
```

## New Structure (Mintlify)

```
docs/

🏠 Home
└── index.mdx (New landing page)

📚 Introduction Tab
├── Overview
    ├── Welcome (Introduction to Universal)
    ├── Protocol Overview (Universal Protocol Overview)
    ├── Introduction to uAssets (Introduction to uAssets)
    ├── FAQ (Frequently Asked Questions)
    └── Proof of Reserves (Proof of Reserves)

👨‍💻 Developers Tab
├── Getting Started
    ├── Building with uAssets (Building with uAssets)
    ├── API Integration (Integrate the Universal API)
    ├── Issuance & Redemption API (Integrate the Issuance & Redemption Universal API)
    ├── Contract Addresses (Contract Addresses)
    ├── Partnerships (Partnerships)
    └── uAsset Logos (uAsset Logos)
├── API Reference
    └── Introduction (New)

🔗 Global Navigation
├── Open App → app.universal.xyz
├── Discord → discord.gg/universal
└── Twitter/X → x.com/joinuniversal

📑 Footer
├── Socials (Twitter, Discord)
└── Links (Whitepaper, Terms, Disclaimer)
```

## Content Mapping

| GitBook Page | Mintlify Page | Changes |
|-------------|---------------|---------|
| Introduction to Universal | `/introduction/welcome.mdx` | Enhanced with cards, better formatting |
| Universal Protocol Overview | `/introduction/protocol-overview.mdx` | Added visual components |
| Introduction to uAssets | `/introduction/uassets.mdx` | Improved layout with CardGroups |
| Frequently Asked Questions | `/introduction/faq.mdx` | Converted to Accordion format |
| Proof of Reserves | `/introduction/proof-of-reserves.mdx` | Enhanced with cards and CTAs |
| Building with uAssets | `/developers/building-with-uassets.mdx` | Added code examples placeholders |
| Integrate the Universal API | `/developers/api-integration.mdx` | Simplified, linked to full docs |
| Integrate the Issuance & Redemption Universal API | `/developers/issuance-redemption-api.mdx` | Restructured with flow diagrams |
| Contract Addresses | `/developers/contract-addresses.mdx` | Enhanced with warnings and links |
| Partnerships | `/developers/partnerships.mdx` | Improved presentation |
| uAsset Logos | `/developers/uasset-logos.mdx` | Added usage guidelines |
| — | `/index.mdx` | **NEW: Home landing page** |
| — | `/api-reference/introduction.mdx` | **NEW: API reference section** |

## Key Improvements

### 1. Navigation

**Before:**
- Flat structure
- Limited categorization
- External links mixed with docs

**After:**
- Tab-based navigation (Introduction, Developers)
- Clear section grouping
- Global anchors for external links
- Better information architecture

### 2. Design

**Before:**
- Light theme (GitBook default)
- Standard GitBook layout
- Limited customization

**After:**
- Dark theme matching universal.xyz
- Purple color scheme (#7B3FF2)
- Custom components (Cards, Accordions, Tabs)
- Modern, engaging layout

### 3. Content Presentation

**Before:**
```markdown
# Introduction to Universal

Universal is a wrapped asset protocol...

## What Problems Does Universal Solve?

### 1. The Cold Start Problem for Chains
...
```

**After:**
```mdx
# Introduction to Universal

Universal is a wrapped asset protocol...

## What Problems Does Universal Solve?

<CardGroup cols={3}>
  <Card title="Limited Onchain Availability" icon="link-slash">
    Many high-value assets like DOGE, XRP...
  </Card>
  ...
</CardGroup>
```

### 4. Developer Experience

**Before:**
- Basic markdown
- Limited code highlighting
- Text-heavy explanations

**After:**
- Rich MDX components
- Syntax-highlighted code blocks
- Interactive accordions
- Visual cards and callouts
- Better scannability

### 5. Mobile Experience

**Before:**
- Standard GitBook mobile view
- Limited optimization

**After:**
- Mintlify responsive design
- Touch-friendly navigation
- Optimized card layouts
- Better mobile typography

## Component Usage

### New Components Added

```mdx
<!-- Cards for features and navigation -->
<CardGroup cols={2}>
  <Card title="..." icon="..." href="...">
    Description
  </Card>
</CardGroup>

<!-- Accordions for FAQs and optional content -->
<AccordionGroup>
  <Accordion title="..." icon="...">
    Content
  </Accordion>
</AccordionGroup>

<!-- Callouts for important information -->
<Note>Important information</Note>
<Tip>Helpful tip</Tip>
<Warning>Warning message</Warning>
<Info>Additional context</Info>

<!-- Checkmarks for lists -->
<Check>Feature or benefit</Check>

<!-- Tabs for multi-option content -->
<Tabs>
  <Tab title="Option 1">Content</Tab>
  <Tab title="Option 2">Content</Tab>
</Tabs>
```

## URL Mapping

### Old URLs → New URLs

| Old (GitBook) | New (Mintlify) |
|--------------|----------------|
| `/docs` | `/introduction/welcome` |
| `/docs/universal-protocol-overview` | `/introduction/protocol-overview` |
| `/docs/introduction-to-uassets` | `/introduction/uassets` |
| `/docs/frequently-asked-questions` | `/introduction/faq` |
| `/docs/proof-of-reserves` | `/introduction/proof-of-reserves` |
| `/docs/building-with-uassets` | `/developers/building-with-uassets` |
| `/docs/integrate-the-universal-api` | `/developers/api-integration` |
| `/docs/integrate-the-issuance-redemption-universal-api` | `/developers/issuance-redemption-api` |
| `/docs/contract-addresses` | `/developers/contract-addresses` |
| `/docs/partnerships` | `/developers/partnerships` |
| `/docs/uasset-logos` | `/developers/uasset-logos` |

### Redirects Needed

When deploying, set up redirects:

```
/docs → /introduction/welcome
/docs/* → [appropriate new path]
```

## Configuration Changes

### GitBook `book.json` → Mintlify `docs.json`

**GitBook:**
```json
{
  "title": "Universal Protocol",
  "theme": "default",
  "plugins": [...]
}
```

**Mintlify:**
```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "dark",
  "name": "Universal Protocol",
  "colors": {
    "primary": "#7B3FF2",
    "light": "#A78BFA",
    "dark": "#5B21B6"
  },
  "navigation": {
    "home": "index",
    "tabs": [...]
  }
}
```

## Features Added

### ✅ New in Mintlify

1. **Home Page** - Dedicated landing page with overview
2. **Tab Navigation** - Better organization with tabs
3. **Global Anchors** - Quick access to app, Discord, Twitter
4. **Dark Mode** - Optimized for dark theme
5. **Rich Components** - Cards, accordions, tabs
6. **Better Search** - Enhanced search functionality
7. **Analytics Ready** - Easy to add GA4, etc.
8. **Custom Domain** - Simple custom domain setup

### 🔄 Improved Features

1. **Code Blocks** - Better syntax highlighting
2. **Link Previews** - Card-based link presentations
3. **Mobile UX** - Responsive, touch-optimized
4. **Loading Speed** - Faster page loads
5. **SEO** - Better meta tags and structure

## Migration Checklist

### ✅ Completed

- [x] Migrate all content pages
- [x] Set up navigation structure
- [x] Configure theme and colors
- [x] Add global anchors
- [x] Create home page
- [x] Convert content to MDX
- [x] Add Mintlify components
- [x] Set up footer links
- [x] Create README and setup docs

### 📝 To Do

- [ ] Replace placeholder images
- [ ] Add real contract addresses
- [ ] Populate API reference
- [ ] Add Universal logos
- [ ] Set up custom domain (docs.universal.xyz)
- [ ] Configure redirects from old URLs
- [ ] Add analytics tracking
- [ ] Test all links
- [ ] Deploy to Mintlify
- [ ] Sunset GitBook site

## Breaking Changes

### URLs Changed
All URLs have changed. Set up redirects to avoid broken links.

### External Links
Any external sites linking to old GitBook URLs will need updating or redirects.

### Bookmarks
Users with bookmarked pages will need new URLs.

## Benefits of Migration

### For Users
- ✅ Better visual experience
- ✅ Easier navigation
- ✅ Faster load times
- ✅ Better mobile experience
- ✅ Dark mode support

### For Developers
- ✅ Better code examples
- ✅ Interactive components
- ✅ Clearer structure
- ✅ Easier to find information
- ✅ Better API documentation

### For Universal Team
- ✅ Easier to maintain
- ✅ Better analytics
- ✅ More professional appearance
- ✅ Matches universal.xyz branding
- ✅ Version control with Git
- ✅ Auto-deployment

## Testing Plan

### Before Launch

1. **Content Review**
   - [ ] All pages render correctly
   - [ ] No broken links
   - [ ] Images load properly
   - [ ] Code blocks format correctly

2. **Navigation Test**
   - [ ] All tabs work
   - [ ] Sidebar navigation functions
   - [ ] Global anchors link correctly
   - [ ] Footer links work

3. **Cross-Browser Testing**
   - [ ] Chrome
   - [ ] Firefox
   - [ ] Safari
   - [ ] Edge

4. **Device Testing**
   - [ ] Desktop (various sizes)
   - [ ] Tablet
   - [ ] Mobile

5. **SEO Check**
   - [ ] Meta titles set
   - [ ] Meta descriptions set
   - [ ] og:image tags set
   - [ ] Sitemap generated

## Rollout Plan

### Phase 1: Soft Launch
- Deploy to Mintlify staging
- Internal team review
- Fix any issues

### Phase 2: Beta
- Share with select community members
- Gather feedback
- Iterate on design/content

### Phase 3: Public Launch
- Configure custom domain
- Set up redirects
- Announce on Discord/Twitter
- Update all links to new docs

### Phase 4: Sunset GitBook
- Add deprecation notice to GitBook
- Monitor redirect traffic
- Eventually shut down GitBook site

## Support During Migration

### For Users
- Announcement in Discord
- Tweet about new docs
- Update links in app
- Keep old docs available during transition

### For Developers
- Update integration guides
- Notify partners
- Update SDK documentation
- Provide migration guide

## Success Metrics

Track these metrics after migration:

- Page views (expect increase)
- Time on site (expect increase)
- Bounce rate (expect decrease)
- Search usage
- Feedback/support requests
- Integration starts

## Timeline

**Recommended:**
- Week 1: Final content review and image replacement
- Week 2: Deploy to staging, internal testing
- Week 3: Beta testing with community
- Week 4: Public launch
- Week 5+: Monitor and iterate

---

**Migration Date**: TBD  
**Old Platform**: GitBook  
**New Platform**: Mintlify  
**Status**: Ready for staging deployment


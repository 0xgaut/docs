# Universal Documentation Setup Guide

This guide will help you get the Universal Protocol documentation up and running locally and deployed.

## Prerequisites

- Node.js 18 or higher
- npm or yarn
- Git

## Installation

### 1. Install Mintlify CLI

```bash
npm install -g mintlify
```

Verify installation:
```bash
mintlify --version
```

### 2. Run Documentation Locally

From the `/Users/gaut/Documents/docs` directory:

```bash
cd /Users/gaut/Documents/docs
mintlify dev
```

The documentation will be available at `http://localhost:3000`

## Project Structure

```
docs/
├── index.mdx                     # Home page
├── docs.json                     # Mintlify configuration
├── .cursorrules                  # AI documentation guidelines
│
├── introduction/                 # Introduction section
│   ├── welcome.mdx              # Main introduction
│   ├── protocol-overview.mdx    # How Universal works
│   ├── uassets.mdx              # uAssets explained
│   ├── proof-of-reserves.mdx    # PoR documentation
│   └── faq.mdx                  # Frequently asked questions
│
├── developers/                   # Developer section
│   ├── building-with-uassets.mdx
│   ├── api-integration.mdx
│   ├── issuance-redemption-api.mdx
│   ├── contract-addresses.mdx
│   ├── partnerships.mdx
│   └── uasset-logos.mdx
│
├── api-reference/               # API documentation
│   ├── introduction.mdx
│   └── openapi.json
│
├── images/                      # Images and assets
├── logo/                        # Logo files
└── README.md                    # Project README

```

## Configuration (`docs.json`)

The main configuration file controls:
- **Theme**: Dark mode
- **Colors**: Purple theme matching universal.xyz
- **Navigation**: Tabs, groups, and page structure
- **Footer**: Social links and legal pages
- **Navbar**: Primary CTA and quick links

### Key Configuration Sections

```json
{
  "theme": "dark",
  "colors": {
    "primary": "#7B3FF2",
    "light": "#A78BFA",
    "dark": "#5B21B6",
    "background": { "dark": "#0F0F1E" }
  },
  "navigation": {
    "home": "index",
    "tabs": [...]
  }
}
```

## Customization

### Update Branding

1. **Replace logos**:
   - `/logo/light.svg` - Logo for light mode
   - `/logo/dark.svg` - Logo for dark mode

2. **Replace hero images**:
   - `/images/hero-light.png` - Light mode hero
   - `/images/hero-dark.png` - Dark mode hero

3. **Update favicon**:
   - `/favicon.svg` - Browser favicon

### Add New Pages

1. Create a new `.mdx` file in the appropriate directory
2. Add frontmatter with `title` and `description`
3. Add the page path to `docs.json` navigation
4. Write content using Mintlify components

Example:
```mdx
---
title: "My New Page"
description: "Description for SEO"
---

# My New Page

Content goes here...
```

### Mintlify Components

Available components:
- `<Card>` - Cards with icons and links
- `<CardGroup>` - Group of cards
- `<Accordion>` / `<AccordionGroup>` - Collapsible content
- `<Tabs>` / `<Tab>` - Tabbed content
- `<Note>` / `<Tip>` / `<Warning>` / `<Info>` - Callout boxes
- `<Check>` - Checkmark items
- Code blocks with syntax highlighting

## Deployment

### Deploy to Mintlify

1. **Sign up for Mintlify**: https://mintlify.com
2. **Connect your GitHub repo**
3. **Configure custom domain** (docs.universal.xyz)
4. **Push changes** - Auto-deploys on commit

### Deploy to Other Platforms

Mintlify docs can also be deployed to:
- Vercel
- Netlify
- AWS Amplify
- GitHub Pages

## Content Guidelines

### Following the System Prompt

The `.cursorrules` file contains the documentation system prompt with:
- Copywriting style (Uniswap-inspired)
- Content organization principles
- Visual design guidelines
- Universal-specific terminology
- Writing best practices

### Key Principles

1. **Use Only Real Content**: Don't make up technical details
2. **Developer-First**: Assume technical competence
3. **Progressive Disclosure**: Simple first, then complex
4. **Code-Forward**: Show code examples where possible
5. **Scannable**: Use headers, bullets, and formatting

### Universal Terminology

- **uAssets**: Wrapped tokens (not "wrapped assets")
- **Minting**: Creating uAssets (not "creating")
- **Redemption**: Converting back (not "unwrapping")
- **Merchants**: Permissioned actors
- **Backing**: 1:1 collateral in custody

## Adding Content

### From Existing Docs

When adding content from https://docs.universal.xyz/docs:
1. Copy the actual content (don't paraphrase)
2. Enhance with Mintlify components
3. Add cross-links to related pages
4. Maintain the original meaning

### Technical Details

For technical content:
- Always link to official sources
- Use code blocks with proper syntax highlighting
- Include practical, runnable examples
- Add comments to explain complex logic

## Testing

### Local Testing

```bash
# Start dev server
mintlify dev

# Check for broken links
mintlify check

# Validate configuration
mintlify validate
```

### Check Before Deploying

- [ ] All links work
- [ ] Images load correctly
- [ ] Code blocks have syntax highlighting
- [ ] Navigation is logical
- [ ] Mobile view works
- [ ] Dark mode looks good
- [ ] SEO titles and descriptions are set

## Troubleshooting

### Port Already in Use

```bash
# Kill process on port 3000
lsof -ti:3000 | xargs kill -9

# Or use a different port
mintlify dev --port 3001
```

### Images Not Loading

- Ensure images are in `/images` directory
- Use absolute paths: `/images/hero.png`
- Check file extensions match

### Navigation Not Working

- Verify paths in `docs.json` match file structure
- Check for typos in page paths
- Ensure `.mdx` extension is omitted in paths

## Resources

- [Mintlify Documentation](https://mintlify.com/docs)
- [Universal Website](https://www.universal.xyz)
- [Universal Original Docs](https://docs.universal.xyz/docs)
- [Uniswap Docs](https://docs.uniswap.org) - Inspiration

## Support

For documentation questions:
- Discord: https://discord.gg/universal
- Twitter/X: https://x.com/joinuniversal

## Next Steps

1. ✅ Install Mintlify CLI: `npm install -g mintlify`
2. ✅ Run locally: `mintlify dev`
3. 📝 Replace placeholder images with Universal branding
4. 📝 Add detailed API documentation
5. 📝 Add real contract addresses
6. 📝 Add code examples from your codebase
7. 🚀 Deploy to Mintlify
8. 🌐 Configure custom domain

---

Built with ❤️ for Universal Protocol


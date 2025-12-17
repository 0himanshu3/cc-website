# CC Club Website

Welcome to the official website of the Computer Coding Club! This is a modern, fast, and maintainable static website built with [Zola](https://www.getzola.org/) static site generator and the [Goyo](https://github.com/hahwul/goyo) theme.

## 🚀 Quick Start

### Prerequisites

- **Zola** (Static Site Generator) - Version 0.17.0 or higher
  - Download: [https://www.getzola.org/documentation/getting-started/installation/](https://www.getzola.org/documentation/getting-started/installation/)

### Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-org/cc-website.git
   cd cc-website
   ```

2. **Initialize the Goyo theme submodule**:
   ```bash
   git submodule update --init --recursive
   ```

3. **Run the development server**:
   ```bash
   zola serve
   ```

4. **Open in browser**:
   - Navigate to `http://127.0.0.1:1111`
   - Site will auto-reload when you make changes

### Building for Production

```bash
zola build
```

The static site will be generated in the `public/` directory.

## 📁 Project Structure

```
cc-website/
├── config.toml              # Site configuration (nav, theme settings, etc.)
├── content/                 # All content (Markdown files)
│   ├── _index.md           # Homepage with landing page sections
│   ├── about.md            # About CC Club
│   ├── team.md             # Current team (uses data/team.yaml)
│   ├── alumni.md           # Alumni directory (uses data/alumni.yaml)
│   ├── contact.md          # Contact information
│   ├── blog/               # Blog posts
│   │   ├── _index.md       # Blog listing page
│   │   └── 2025/          # Blog posts organized by year
│   ├── events/             # Event pages
│   │   ├── _index.md       # Events listing
│   │   └── 2024/, 2025/   # Events by year
│   ├── contrihub/          # ContriHub event pages
│   │   ├── _index.md       # ContriHub overview
│   │   ├── how-to-participate.md
│   │   └── 2024/, 2025/, 2026/  # ContriHub events by year
│   ├── impact/             # Club impact showcase
│   ├── roadmaps/           # Learning roadmaps (DSA, Web Dev, etc.)
│   └── resources/          # Curated learning resources
├── data/                    # YAML data files for team, alumni, etc.
│   ├── team.yaml           # Team member information
│   ├── alumni.yaml         # Alumni directory data
│   ├── README.md           # Data file documentation
│   └── contrihub/          # ContriHub-specific data
│       └── 2024/, 2025/, 2026/
├── static/                  # Static assets (copied as-is to public/)
│   ├── css/
│   │   └── custom.css      # Custom styles (optional)
│   ├── js/
│   │   └── alumni-search.js # Alumni search/filter logic
│   └── images/             # All images (team, alumni, blog, etc.)
├── templates/               # Custom templates (only where needed)
│   ├── alumni.html         # Alumni page with server-side rendering
│   ├── blog.html           # Blog listing with search
│   ├── team.html           # Team page rendering
│   ├── events.html         # Events listing (upcoming/past)
│   ├── contrihub_index.html # ContriHub landing
│   ├── contrihub_event.html # Individual ContriHub event
│   ├── impact.html         # Impact showcase
│   └── tags/               # Taxonomy templates
│       ├── list.html       # All tags listing (/tags/)
│       └── single.html     # Posts for a tag (/tags/react/)
├── themes/
│   └── goyo/               # Goyo theme (git submodule - DO NOT EDIT)
├── scripts/
│   └── validate-data.py    # Validates YAML data files
├── CONTRIBUTING.md          # How to contribute
├── CONTENT_GUIDE.md         # Content creation guide
└── README.md               # This file
```

## ✨ Features

### Core Features
- ⚡ Lightning-fast static site generation with Zola
- 🏷️ **Tag System**: Filter blog posts by technology/topic
- 📄 **Pagination**: Automatic pagination for blog (10 posts per page)
- 🔍 **Search**: Full-text search across all content
- 📱 **Responsive**: Mobile-first design with DaisyUI
- 🎨 **Dark Mode**: Automatic theme switching
- 👥 **Dynamic Data**: Team and alumni from YAML files
- 📊 **SSR Filtering**: Server-side rendering for better performance

### Powered by Goyo Theme
- ⚡ Minimalist documentation-focused design
- 🌙 Dark/light mode with customizable themes
- 📱 Fully responsive mobile-first design
- 🔍 Built-in client-side search
- 📊 Rich shortcodes (alerts, badges, collapse, gallery, etc.)
- 💬 Comment system support (Giscus/Utterances)
- 🎨 DaisyUI + TailwindCSS styling
- 📝 Syntax highlighting for code blocks
- 🔗 Social sharing buttons
- ♿ Accessible markup

### Custom CC Club Features
- 👥 **Alumni Directory** - Server-side rendered with client-side filtering
- 🎯 **ContriHub Showcase** - Annual open source contribution event
- 📚 **Learning Roadmaps** - Structured paths for different domains
- 📝 **Blog** - Tagged articles with search functionality
- 📅 **Event Management** - Automatic upcoming/past categorization
- 💡 **Impact Stories** - Showcase club achievements
- 📖 **Resource Library** - Curated learning materials

## 📝 Content Management

### For Non-Developers

Most content updates require **only editing Markdown or YAML files** - no coding needed!

#### Adding a Blog Post

1. Create a new file: `content/blog/2025/your-post-title.md`
2. Add frontmatter:
   ```markdown
   +++
   title = "Your Post Title"
   date = 2025-01-15
   description = "Brief description"
   
   [taxonomies]
   tags = ["Tutorial", "Web Dev"]
   +++
   
   Your content here...
   ```
3. Commit and push

#### Adding a Team Member

1. Open `data/team.yaml`
2. Add entry under appropriate section (faculty/coordinators/executives):
   ```yaml
   - name: "Your Name"
     role: "Your Role"
     image: "/images/team/yourname.jpg"
     bio: "Short bio"
     linkedin: "https://linkedin.com/in/yourname"
     github: "https://github.com/yourname"
   ```
3. Add your photo to `static/images/team/`

#### Adding an Alumni

1. Open `data/alumni.yaml`
2. Add entry:
   ```yaml
   - name: "Your Name"
     batch: "2021-2025"
     graduation_year: 2025
     current_role: "Software Engineer"
     company: "Company Name"
     domain: "Backend Development"
     location: "City, Country"
     image: "/images/alumni/yourname.jpg"
     linkedin: "https://linkedin.com/in/yourname"
     github: "https://github.com/yourname"
     message: "Optional advice for juniors"
   ```
3. Add your photo to `static/images/alumni/`

#### Adding an Event

1. Create: `content/events/2025/event-name.md`
2. Add frontmatter:
   ```markdown
   +++
   title = "Event Name"
   date = 2025-03-15
   description = "Event description"
   
   [extra]
   location = "Venue"
   registration_link = "https://..."
   +++
   
   Event details...
   ```

See [CONTENT_GUIDE.md](CONTENT_GUIDE.md) for detailed instructions.

## 🎨 Customization

### Theme Settings

Edit `config.toml` to customize:

```toml
[extra.theme]
colorset = "dark"              # "dark" or "light"
brightness = "normal"          # "darker", "normal", "lighter"
disable_toggle = false         # Hide theme toggle

[extra.logo]
text = "CC Club"
image_path = "images/logo.png" # Add your logo

[extra.sidebar]
expand_depth = 2               # Sidebar auto-expansion depth
```

### Custom Styling

Add custom CSS in `static/css/custom.css`:
- File includes helpful comments and examples
- Extends Goyo theme without overriding
- Uses DaisyUI utilities

### Templates

Custom templates (in `templates/`) are used only where Goyo doesn't provide the functionality:

| Template | Purpose | Extends Goyo? |
|----------|---------|---------------|
| `alumni.html` | Alumni directory with filters | ✅ Yes (`page.html`) |
| `blog.html` | Blog listing with search | ✅ Yes (`index.html`) |
| `team.html` | Team member cards from YAML | ✅ Yes (`page.html`) |
| `events.html` | Event listing (upcoming/past) | ✅ Yes (`index.html`) |
| `contrihub_*.html` | ContriHub pages | ✅ Yes |
| `impact.html` | Impact showcase | ✅ Yes |
| `taxonomy_*.html` | Tag pages (required) | ✅ Yes |

**Important:** These templates extend Goyo - they don't replace it. Goyo updates will still apply.

## 🚀 Deployment

### GitHub Pages

The site can be deployed to GitHub Pages using GitHub Actions.

1. **Enable GitHub Pages** in repository settings
2. **Add GitHub Actions workflow** (`.github/workflows/deploy.yml`):

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true
      
      - name: Install Zola
        run: |
          wget https://github.com/getzola/zola/releases/download/v0.17.2/zola-v0.17.2-x86_64-unknown-linux-gnu.tar.gz
          tar -xzf zola-v0.17.2-x86_64-unknown-linux-gnu.tar.gz
          sudo mv zola /usr/local/bin/
      
      - name: Build
        run: zola build
      
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

3. **Push to main branch** - Site will auto-deploy!

### Other Platforms

**Netlify:**
- Connect GitHub repo
- Build command: `zola build`
- Publish directory: `public`

**Vercel:**
- Import GitHub repo
- Framework: Other
- Build command: `zola build`
- Output directory: `public`

**Cloudflare Pages:**
- Connect GitHub repo
- Build command: `zola build`
- Build output directory: `public`

## 🛠️ Development

### Architecture

**This site follows the Zola + Goyo best practices:**

1. **Content in Markdown** - `content/` directory
2. **Data in YAML** - `data/` directory  
3. **Styling via DaisyUI/Tailwind** - Minimal custom CSS
4. **Templates extend Goyo** - Not replace
5. **Server-side rendering** - JavaScript only for interactivity

**What makes this maintainable:**
- Non-developers can edit Markdown/YAML without touching code
- Custom templates are minimal and well-documented
- Goyo theme updates are automatically inherited
- Static site = fast, secure, cheap hosting

### Local Development

```bash
# Clone with submodules
git clone --recurse-submodules https://github.com/your-org/cc-website.git

# Or if already cloned
git submodule update --init --recursive

# Start dev server
zola serve

# Build for production
zola build

# Validate content
zola check
```

### Recommended Tools

- **VS Code** with extensions:
  - Markdown All in One
  - YAML
  - Better TOML

- **Optional Git GUI**:
  - GitHub Desktop (simplest)
  - GitKraken
  - SourceTree

### Common Tasks

**Adding images:**
```bash
# Place in static/images/
cp photo.jpg static/images/team/yourname.jpg

# Reference in markdown or YAML
image: "/images/team/yourname.jpg"
```

**Working with drafts:**
```markdown
+++
draft = true  # Won't appear in production
+++
```

View drafts: `zola serve --drafts`

**Testing before deploy:**
```bash
# Build and check for errors
zola build

# Check internal links
zola check

# Serve production build locally
cd public && python3 -m http.server
```

## 🚀 Deployment

### Before First Deployment

Update `config.toml`:
```toml
base_url = "https://your-actual-domain.com"
edit_url = "https://github.com/your-org/cc-website/edit/main"
```

### Deployment Options

**GitHub Pages (Main):**
1. Push to main branch
2. GitHub Actions auto-deploys
3. See `.github/workflows/deploy.yml`

**Netlify:**
- Build: `zola build`
- Publish: `public/`

**Vercel/Cloudflare Pages:**
- Framework: Other
- Build: `zola build`
- Output: `public/`

## 📚 Documentation & Resources

- [Zola Documentation](https://www.getzola.org/documentation/)
- [Goyo Theme Docs](https://github.com/hahwul/goyo)
- [DaisyUI Components](https://daisyui.com/)
- [CONTENT_GUIDE.md](CONTENT_GUIDE.md) - How to add content
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contribution workflow
- [data/README.md](data/README.md) - Data file documentation

## 🤝 Contributing

We welcome contributions from all club members!

**For non-developers:**
- Edit Markdown files for content
- Update YAML files for team/alumni
- Fix typos and improve documentation

**For developers:**
- Improve templates
- Add features
- Fix bugs
- Enhance styling

See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- Step-by-step contribution guide
- Content guidelines
- Git workflow
- Pull request process
- Code style

## 👥 Maintainers

**Current:** Shanu Kumawat ([@Shanu-Kumawat](https://github.com/Shanu-Kumawat))

**Web Team:** See [Team Page](/team)

**Alumni Maintainers:** We encourage past web team members to continue contributing!

## 📄 License

MIT License - see [LICENSE](LICENSE)

**Goyo Theme:** MIT License by [hahwul](https://github.com/hahwul/goyo)

## 🙋 Support & Help

**Need help?**

1. 📖 Read [CONTENT_GUIDE.md](CONTENT_GUIDE.md) for content questions
2. 🔍 Search [GitHub Issues](https://github.com/your-org/cc-website/issues)
3. 💬 Ask on club Discord/Slack
4. 🐛 Open a new issue for bugs
5. ✉️ Contact web team

## 📊 Project Status

**Current Version:** 2.0 (Post-Refactor)

**Recent Updates (December 2024):**
- ✅ Removed unnecessary template overrides
- ✅ Fixed blog taxonomy filtering
- ✅ Refactored alumni page to SSR
- ✅ Simplified JavaScript (300 → 200 lines)
- ✅ Removed unused categories taxonomy
- ✅ Updated all documentation

**Maintenance:**
- Regular: Content updates (blog, events, team)
- Occasional: Goyo theme updates (git submodule)
- Rare: Template modifications (only if needed)
- ✅ Custom templates
- ✅ YAML data structure
- ✅ Documentation

**To Do:**
- 🔄 Add real content (replace examples)
- 🔄 Custom CSS styling (design team)
- 🔄 Collect team photos
- 🔄 Collect alumni data
- 🔄 Add more blog posts
- 🔄 Add more roadmaps
- 🔄 Set up GitHub Actions deployment
- 🔄 Add analytics (optional)

**Future Enhancements:**
- Newsletter subscription
- Event registration integration
- Project submission portal
- Member dashboard
- Achievement badges
- Photo gallery
- ContriHub live leaderboard

## 🎉 Acknowledgments

- **Goyo Theme** by Jeevan Gantait
- **Zola** static site generator
- **DaisyUI** component library
- **Tailwind CSS** utility framework
- **Font Awesome** icons
- All CC Club contributors!

---

**Made with ❤️ by CC Club, Mnnit**

**Last Updated:** January 2025

# Content Guide

**Last Updated:** December 2024 (Post-Refactor)

This guide explains how to add and edit content on the CC Club website. **Most tasks require only editing Markdown or YAML files** - no coding needed!

## Quick Reference

| Task | File to Edit | Difficulty |
|------|-------------|------------|
| Add blog post | `content/blog/2025/post-name.md` | ⭐ Easy |
| Add event | `content/events/2025/event-name.md` | ⭐ Easy |
| Update team | `data/team.yaml` | ⭐ Easy |
| Add alumni | `data/alumni.yaml` | ⭐ Easy |
| Add roadmap | `content/roadmaps/domain.md` | ⭐⭐ Medium |
| Add resource | `content/resources/topic.md` | ⭐ Easy |

## Directory Structure

```
content/                   # All Markdown content
├── _index.md             # Homepage (landing page sections)
├── about.md              # About CC Club
├── team.md               # Current team (uses data/team.yaml)
├── alumni.md             # Alumni directory (uses data/alumni.yaml)
├── contact.md            # Contact information
├── blog/                 # Blog posts
│   ├── _index.md         # Blog listing page
│   └── 2025/            # Posts by year
├── events/               # Events
│   ├── _index.md         # Events listing
│   └── 2025/, 2026/     # Events by year
├── contrihub/            # ContriHub event
│   ├── _index.md
│   └── 2024/, 2025/
├── impact/               # Club impact showcase
├── roadmaps/             # Learning roadmaps
└── resources/            # Curated resources

data/                      # YAML data files
├── team.yaml             # Team members
├── alumni.yaml           # Alumni directory
└── contrihub/            # ContriHub data
    └── 2025/

static/                    # Static files
├── images/               # All images
│   ├── blog/
│   ├── events/
│   ├── team/
│   └── alumni/
├── css/custom.css        # Custom styles
└── js/alumni-search.js   # Alumni filtering logic
```

## Adding Content

### Blog Posts

**File:** `content/blog/2025/your-post-title.md`

```markdown
+++
title = "Your Post Title"
date = 2025-01-15
description = "Brief description for SEO and previews"

[taxonomies]
tags = ["tutorial", "web-development", "python"]

[extra]
author = "Your Name"
author_role = "Your Role"
author_github = "yourgithub"
author_linkedin = "yourlinkedin"
reading_time = 5  # minutes
featured = false
badge = "NEW"
cover_image = "/images/blog/your-post.jpg"
+++

Your content here in Markdown...

## Headings work

- Lists work
- Code blocks work

\```python
print("Hello World")
\```
```

**Tags:** Use existing tags when possible. Browse [/tags](/tags) to see all tags. Tags must be in `[taxonomies]` section for filtering to work.

**Images in posts:**
```markdown
![Alt text](/images/blog/2025/your-image.jpg)
```

### Events

**File:** `content/events/2025/event-name.md`

```markdown
+++
title = "Event Name"
date = 2025-03-15  # Event date
description = "Brief event description"

[extra]
location = "Venue Name"
registration_link = "https://forms.google.com/..."
badge = "UPCOMING"  # Optional: UPCOMING, COMPLETED, etc.
+++

Event details, schedule, speakers, etc.

## Event Schedule

- 10:00 AM - Registration
- 11:00 AM - Workshop
```

**Automatic categorization:** Events are automatically marked as "Upcoming" or "Past" based on the date.

### Team Members

**File:** `data/team.yaml`

```yaml
# Faculty Advisors
faculty:
  - name: "Prof. Name"
    designation: "Professor"
    department: "Department Name"
    bio: "Brief bio"
    image: "/images/team/prof-name.jpg"

# Club Coordinators
coordinators:
  - name: "Student Name"
    role: "President"  # or "Vice President", "Secretary"
    bio: "Brief bio"
    image: "/images/team/student-name.jpg"
    linkedin: "https://linkedin.com/in/username"
    github: "https://github.com/username"

# Executive Members
executives:
  - name: "Student Name"
    role: "Web Team Lead"  # or "Events Head", "Content Lead"
    image: "/images/team/student-name.jpg"
    linkedin: "https://linkedin.com/in/username"
    github: "https://github.com/username"
```

**Images:**
1. Add photo to `static/images/team/yourname.jpg`
2. Reference: `image: "/images/team/yourname.jpg"`
3. Recommended size: 400x400px, square crop

### Alumni

**File:** `data/alumni.yaml`

```yaml
alumni:
  - name: "Full Name"
    batch: "2021-2025"
    graduation_year: 2025
    current_role: "Software Engineer"
    company: "Google"
    domain: "Backend Development"  # See domains list below
    location: "Bangalore, India"
    image: "/images/alumni/yourname.jpg"
    linkedin: "https://linkedin.com/in/username"
    github: "https://github.com/username"
    message: "Optional advice for juniors"
```

**Valid domains:**
- Backend Development
- Frontend Development
- Full Stack
- Machine Learning
- Natural Language Processing
- Computer Vision
- Cloud Infrastructure
- Distributed Systems
- Product Management
- Documentation
- Security
- Fintech
- Creative Cloud

**Note:** Filters are automatically generated from the data - no need to update templates!

### Roadmaps

**File:** `content/roadmaps/domain-name.md`

```markdown
+++
title = "Domain Name Roadmap"
description = "Learning path for Domain Name"
weight = 1
+++

# Domain Name Roadmap

## Phase 1: Beginner (0-3 months)
- Topic 1
- Topic 2

## Phase 2: Intermediate (3-6 months)
- Topic 3
- Topic 4

## Projects
1. Project idea 1
2. Project idea 2

## Resources
- [Resource Name](URL)
```

### Resources

**File:** `content/resources/topic.md`

```markdown
+++
title = "Topic Name"
description = "Resources for learning Topic"
weight = 1
+++

## Courses
- [Course Name](URL) - Description

## Books
- Book Name by Author - Description

## Practice
- [Platform Name](URL) - Description
```
description = "Brief event description"
date = 2025-03-15  # Event date
template = "contrihub-event.html"  # Optional: custom template

[extra]
badge = "UPCOMING"  # or "COMPLETED"
location = "Venue Name"
start_time = "10:00 AM"
end_time = "05:00 PM"

[extra.tags]
category = ["workshop", "hackathon", "seminar"]  # Choose relevant
+++

Event content in markdown...
```

5. Ensure year has `_index.md`:

```toml
+++
title = "2025 Events"
sort_by = "date"
template = "section.html"

[extra]
badge = "NEW"  # Optional
+++
```

### ContriHub (`content/contrihub/`)

ContriHub pages are organized with a main landing and year-specific event pages:

```
contrihub/
├── _index.md                   # ContriHub main landing page
├── how-to-participate.md       # Single guide for all years (edit as needed)
└── 2025/
    └── _index.md               # ContriHub 2025 event page (uses contrihub-event.html)
```

**Why one guide?**
- Only current year participation matters
- Update the single guide when process changes
- Past event participation guides are irrelevant
- Keeps content simple and maintainable

**Creating a new ContriHub year:**

1. Create year folder and event page:
```bash
mkdir -p content/contrihub/2026
```

2. Create `_index.md` with event details:
```toml
+++
title = "ContriHub 2026"
description = "ContriHub 2026 event description"
template = "contrihub-event.html"

[extra]
contrihub_year = "2026"  # Important: links to data/contrihub/2026/
status = "upcoming"       # or "completed"
+++
```

3. Create data files:
```bash
cp -r data/contrihub/2025 data/contrihub/2026
# Edit files in data/contrihub/2026/ with new stats
```

4. **Update how-to-participate.md** only if process changes (not every year!)

**No year-specific guides needed** - one guide serves all years!

## Frontmatter Standards

### Date Fields

**Use ONE date field per page** - avoid duplicates:

```toml
# ✅ CORRECT - Single date field
+++
title = "Event Name"
date = 2025-03-15  # Main event date

[extra]
# Additional time details if needed
start_time = "10:00 AM"
end_time = "05:00 PM"
+++
```

```toml
# ❌ WRONG - Duplicate date fields
+++
title = "Event Name"
date = 2025-03-15
start_date = 2025-03-15  # Don't do this!
+++
```

### Required Fields by Content Type

**Events**:
```toml
title = "..."         # Required
description = "..."   # Required
date = YYYY-MM-DD    # Required
template = "..."      # Optional (uses default if not set)
```

**ContriHub Guides**:
```toml
title = "..."         # Required
description = "..."   # Required
weight = 1           # Required (for ordering)
```

**Blog Posts**:
```toml
title = "..."         # Required
date = YYYY-MM-DD    # Required
description = "..."   # Recommended

[taxonomies]         # For tags (enables filtering)
tags = ["tag1", "tag2"]

[extra]              # For custom fields
author = "Name"
featured = true
badge = "NEW"
```

### Using [extra] Section

Goyo theme uses `[extra]` for custom fields and theme-specific features:

```toml
[extra]
badge = "UPCOMING"           # Badge display
location = "Event venue"     # Custom field
featured = true              # Feature flag

[extra.hero]                 # Landing page hero
title = "Main Title"
subtitle = "Subtitle text"

[extra.tags]                 # Tags for filtering
category = ["workshop", "tech"]
```

### Badges

Use badges to highlight page status:

- `NEW` - Recently added content
- `UPDATED` - Recently modified
- `UPCOMING` - Future events
- `COMPLETED` - Past events
- `FEATURED` - Highlighted content

```toml
[extra]
badge = "UPCOMING"
```

## Section Index Files (`_index.md`)

Every directory that represents a section needs an `_index.md`:

```
events/
├── _index.md        # Required - Events section page
└── 2025/
    └── _index.md    # Required - 2025 year subsection page
```

**Basic _index.md template:**

```toml
+++
title = "Section Name"
sort_by = "date"           # How to sort pages: "date", "weight", "title"
template = "section.html"  # Template to use

[extra]
badge = "NEW"             # Optional
+++

Optional section description in markdown.
```

## Content Guidelines

### File Naming

- Use lowercase with hyphens: `event-name.md`
- Be descriptive: `docker-kubernetes-workshop.md` not `workshop.md`
- Avoid special characters, spaces, or underscores
- Keep names concise but meaningful

### Image Paths

Always use absolute paths from the static directory:

```markdown
✅ CORRECT
![Event Photo](/images/events/2025/event-photo.jpg)

❌ WRONG
![Event Photo](../../static/images/events/2025/event-photo.jpg)
![Event Photo](images/events/2025/event-photo.jpg)
```

### Content Structure

Use clear heading hierarchy:

```markdown
+++
title = "Page Title"
+++

Brief introduction paragraph.

## First Section

Section content...

### Subsection

Subsection content...

## Second Section

More content...
```

## Validation

Run validation before committing:

```bash
# Validate data files and frontmatter
python scripts/validate-data.py

# Test build
zola build

# Local preview
zola serve
```

## Best Practices

1. **Organize by year for temporal content** - Events, ContriHub editions, etc.
2. **Use single date field** - Avoid duplicates like `date` and `start_date`
3. **Include _index.md for sections** - Required for proper navigation
4. **Use descriptive filenames** - Helps with maintenance
5. **Validate before committing** - Catch errors early
6. **Test locally** - Preview changes with `zola serve`
7. **Use absolute paths for images** - Prevents broken links
8. **Follow Goyo theme conventions** - Use [extra] for custom fields

## Migration Notes

Recent structural changes (2025-01):

- ✅ Events reorganized from `upcoming/`/`past/` to year-based (`2025/`, `2024/`)
- ✅ ContriHub guides moved into year folders (`2025/`)
- ✅ Duplicate date fields removed from event pages
- ✅ All sections now have proper `_index.md` files
- ✅ Alumni data split into year-based YAML files

These changes improve long-term maintainability and scalability.

## Troubleshooting

**Problem**: Page returns 404

**Solution**:
- Check filename and path are correct
- Ensure `_index.md` exists in parent directory
- Verify frontmatter has required fields (`title`, etc.)
- Run `zola build` to check for errors

**Problem**: Page doesn't appear in section list

**Solution**:
- Check `_index.md` has `sort_by` specified
- Verify page has proper `date` or `weight` for sorting
- Ensure page is in correct directory

**Problem**: Images not loading

**Solution**:
- Use absolute paths starting with `/`
- Verify image exists in `static/` directory
- Check filename matches exactly (case-sensitive)

## Questions?

For more information:
- **Data files**: See `/data/README.md`
- **Alumni data**: See `/data/alumni/README.md`
- **Goyo theme**: See `themes/goyo/README.md`
- **Validation**: Run `scripts/validate-data.py`

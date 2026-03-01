# 📄 Pandoc Multi-Format Site Template

This template uses **Pandoc** and **GitHub Actions** to turn simple Markdown files into a polished documentation site with:

* 📘 PDF output (with cover page and table of contents)
* 🌐 Responsive multi-page HTML website with dynamic navigation
* 📖 EPUB ebook with metadata and optional cover image
* 📝 Microsoft Word document with table of contents
* 🚀 Automatic deployment to GitHub Pages

---

## 🚀 Getting Started

1. **Use this template** to create your own repository on GitHub.
2. Upload your Markdown files to the `src/` folder (feel free to delete the sample files included with the template).
3. Add your Markdown files using the naming convention:

```
index.md
01-intro.md
02-topic.md
03-more.md
```

> Note that the `index.md` file is needed to become the homepage of a website deliverable, but it will be the last file processed in an EPUB, PDF, or Word deliverable.

4. Push your changes to the `main` branch.
5. GitHub Actions will automatically:
   * Build your PDF, EPUB, Word, and HTML deliverables
   * Create a dynamic navigation menu based on your content
   * Publish your site to GitHub Pages

---

## ✍️ Writing Your Markdown Files

* Each file **must begin with a YAML metadata block**.
* Required field:

```yaml
navtitle: "Title to Show in Navigation Menu"
```

* Example:

```markdown
---
navtitle: "Structured Authoring"
---

# Structured Authoring

Write your content here using regular Markdown.
```

* File names like `01-intro.md`, `02-chapter.md` define the order in the menu.
* `index.md` is always listed first and becomes the landing page.

---

## 🔧 Enabling GitHub Pages

1. Go to **Settings → Pages** in your repo
2. Set source to the `gh-pages` branch and root (`/`) folder
3. Visit your site at `https://<your-username>.github.io/<your-repo>/`

---

## 🔐 GitHub Actions Permissions

1. Go to **Settings → Actions → General**
2. Under **Workflow permissions**, check:
   > ✅ "Read and write permissions"
3. Click **Save**

This is required for GitHub Actions to deploy your site.

---

## 🎨 Customizing the Look and Feel

Modify the following files in the `assets/` folder to style your site:

* `style.css`: Main stylesheet
* `footer.html`: Footer block
* `cover.jpg`: Optional EPUB cover
* `cover.tex`: Optional LaTeX title page for PDF
* `reference.docx`: Optional Word template to control fonts and heading styles in the DOCX output

> The navigation header is generated automatically. Do **not** edit `header.html` manually—it's built during the workflow run using your Markdown titles.

---

## 📄 Accessing PDF, EPUB, and Word Deliverables

The PDF, EPUB, and Word outputs are not deployed directly to GitHub Pages.  
Instead, each workflow run on the **Actions** page provides them as downloadable **artifacts**:

1. Go to the **Actions** tab in your repository.
2. Select the latest successful workflow run.
3. Scroll down to the **Artifacts** section.
4. Download the `site-outputs.zip` file to access the PDF, EPUB, and Word artifacts.

> **Tip:** To customize Word styles, generate a default reference file locally with `pandoc --print-default-data-file reference.docx > assets/reference.docx`, open it in Word, apply your preferred styles, and save it back. Pandoc will use those styles when building the DOCX.

---

## 📁 Folder Overview

```
.github/workflows/      # GitHub Actions workflow
assets/                 # CSS, footer, LaTeX, optional cover image, optional Word template
src/                    # Markdown files (index.md, 01-intro.md, etc.)
output/                 # Generated site and files
metadata.yaml           # Global metadata (for EPUB, PDF, Word)
README.md               # This file
```

---

## 🙋 Need Help?

This template was created by Carlos Evia with help from your uncle [Claude](https://claude.ai) (Anthropic).  

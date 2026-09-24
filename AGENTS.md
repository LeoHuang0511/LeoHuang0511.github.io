# Repository Guide for Coding Agents

## Project

This repository is the English academic homepage of Feng-Kai Huang, published with GitHub Pages at the custom domain in the root CNAME file. It is a Jekyll site with a small custom layout and plain CSS. Keep the site simple; do not add a theme, JavaScript framework, or gem unless the existing Jekyll features cannot meet a concrete need.

## Repository map

- _config.yml: site identity, contact links, SEO metadata, and Jekyll exclusions.
- index.md: home biography, research summary, optional news, and three selected publications.
- research.md, publications.md, cv.md: the Research, Publications, and CV pages.
- _data/publications.yml: publication records rendered on the home and Publications pages.
- _data/optional_content.yml: optional news, projects, and CV sections, each controlled by an enabled flag.
- _layouts/homepage.html: shared document shell, profile links, page navigation, and conditional CV navigation.
- _includes/: shared publication and optional-section markup.
- assets/css/site.css: all site styles, including responsive rules.
- assets/img/: profile image, favicon, and publication teaser images.
- bibtex/: downloadable BibTeX records.
- resume/: LaTeX CV sources and the PDF linked by _config.yml.
- assets/certificates/: certificate PDFs retained as supporting material.
- google_scholar_crawler/ and .github/workflows/: scheduled citation-data automation; crawler sources are excluded from the generated site.
- Gemfile: local GitHub Pages/Jekyll dependencies. _site/ is generated output and is ignored by Git.

## Editing content

- Keep the website in English. Do not invent or infer biographical facts; use facts already present in the public site unless the user provides updates.
- Update site identity and links in _config.yml; write the biography in index.md.
- Add publications to the top of _data/publications.yml so the newest appears first. Preserve the existing record keys: title, authors, conference_short, conference, pdf, code, page, bibtex, notes, and image. Author fields intentionally allow small HTML tags for bolding the site owner's name.
- Put internal asset paths in root-relative form (for example /assets/img/name.jpg) and pass them through Jekyll's relative_url filter when rendering. Keep external URLs absolute.
- Optional groups in _data/optional_content.yml start disabled. Add complete content before setting enabled to true; empty groups should remain hidden. CV navigation is shown only when an enabled CV group has content.
- Keep CV source/PDF updates separate from website bio data unless the user asks to synchronize them; they are distinct maintained files.
- Put publication images in assets/img/ and BibTeX files in bibtex/. Do not add generated build output to source control.

## Coding style

- Ponytail full is active. First check whether the change is needed, then reuse existing Jekyll/Liquid/CSS patterns. Prefer the smallest working change, deletion over duplication, native HTML/CSS over JavaScript, and the standard library over new dependencies.
- Avoid abstractions, configuration, or dependencies without a current use. Keep shared markup in _includes/ only when it removes real duplication.
- Keep Liquid readable and HTML semantic. Keep styles in assets/css/site.css; avoid inline styles and new JavaScript for presentation.
- Preserve accessibility basics: meaningful image alt text, semantic headings, visible link text, keyboard-accessible navigation, and responsive layout.
- For non-trivial logic, leave one small runnable check as Ponytail requires. Do not add a test framework or broad test suite for this static site.
- Do not run formatters that rewrite unrelated files.

## Local development and verification

The supported local setup is Conda. The Conda environment must contain Ruby 3.2, c-compiler, cxx-compiler, and make; install Bundler and the Gemfile gems inside that environment. Conda RubyGems may require this environment-local symlink once:

~~~sh
ln -sfn "$CONDA_PREFIX/bin/ruby" "$CONDA_PREFIX/share/rubygems/bin/ruby"
~~~

With the environment activated:

~~~sh
bundle install
bundle exec jekyll serve --host 127.0.0.1
~~~

Open http://localhost:4000. For VS Code Remote SSH, forward port 4000 in the Ports panel. Before finishing a site change, run bundle exec jekyll build and inspect the generated pages/assets. Keep maintenance sources such as the crawler and LaTeX source excluded from the public output.

## Commit messages

Follow the commit-message guidance in the referenced iThome article:
https://ithelp.ithome.com.tw/articles/10228738

~~~text
<type>(<scope>): <subject>

<body: explain why and what changed; wrap lines at about 72 characters>

<footer: issue reference and/or breaking-change note, when applicable>
~~~

- Use one of: feat, fix, docs, style, refactor, perf, test, chore, or revert.
- Scope is optional and should name a real area, such as site, content, publications, cv, style, build, or docs.
- Keep the subject concise (at most 50 characters), describe the intent, and omit the final period.
- Use the body to record both why the change was needed and what changed. Keep each body line within about 72 characters.
- Include an issue number only when one exists; do not invent issue references.
- For incompatible changes, add a BREAKING CHANGE: footer with the impact and migration note.
- Keep each commit focused on one logical change.

# Design-is-ALL Lab website — how to edit & update

This guide explains, in plain steps, how to change the content of your website
and re-publish it. You do **not** need to know how to code — almost every edit
is just finding some text and typing over it.

---

## 1. What each file is

Your site is a set of plain web pages. Each page is one file you can open and edit.

| File | What it controls (the tab on the site) |
|------|------------------------------------------|
| `index.html` | **Home** page — big title, intro line, About, project cards, latest news, contact |
| `research.html` | **Research** page — the 5 project write-ups |
| `people.html` | **People** page — you (PI), collaborators, students, alumni |
| `publications.html` | **Publications** page — journal + conference lists |
| `news.html` | **News** page — the news items |
| `contact.html` | **Contact** page — address, office, phone, email |
| `assets/css/style.css` | The **look** — all colors, fonts, spacing (shared by every page) |
| `assets/js/main.js` | Small behaviors — mobile menu, "back to top", the year in the footer |
| `assets/images/` | Every picture used on the site |
| `.nojekyll` | A required empty file — leave it alone, don't delete it |

**Golden rule:** the words you see on the site live *inside* the `.html` files.
To change text, you edit the matching `.html` file. To change how things
*look* (a color, a font size), you edit `style.css`.

---

## 2. How to edit any page

1. Open the `.html` file in a plain text editor.
   - On Mac: right-click the file → **Open With → TextEdit** (or download the
     free **VS Code**, which is nicer and color-codes everything).
2. Use **Find** (`Cmd + F`) to jump to the words you want to change.
3. Type your new text **between** the `>` and `<` symbols. For example, in

   ```html
   <h3>CSU Chancellor's Early-Career Faculty Fellowship</h3>
   ```

   only change the middle part:

   ```html
   <h3>Your new headline here</h3>
   ```

   Leave the `<h3>` and `</h3>` tags in place — those are the labels that keep
   the styling correct.
4. **Save** the file (`Cmd + S`).
5. Re-publish (see section 9).

> Tip: work on a copy first if you're nervous. Duplicate the file, edit the
> copy, and only swap it in once it looks right.

A few symbols you'll see in the text — type them exactly like this:
`&amp;` means "&", `&rarr;` means "→", `&copy;` means "©". If you just need a
plain ampersand in a sentence, use `&amp;`.

---

## 3. Editing the Home page (`index.html`)

- **Intro line under the title** — find the sentence that starts
  `We use learning-based methods…` and edit it.
- **About the Lab** — find `About the Lab`; the two paragraphs right below it are
  the About text.
- **Latest News on the home page** — the home page keeps its **own** short copy
  of the 5 news items (they are not pulled automatically from the News page).
  If you change the News page and want the home page to match, update these here
  too.
- **Project cards** — each card links to the matching project on the Research
  page. You normally don't need to touch these unless you rename a project.

---

## 4. Editing the Research page (`research.html`)

Each project is one block. To **edit** a project, find its title and change the
title and paragraph. To **add a new project**, copy an existing block and paste
it in. Here is the shape of a standard project block:

```html
<!-- 06 My New Project -->
<section class="section" id="my-new-project">
  <div class="container">
    <div class="rproj-body">
      <h2>My New Project — Short Descriptive Title</h2>
      <p>One or two paragraphs describing the project go here.</p>
      <figure class="rfig"><img src="assets/images/research-myproject.png" alt="Short description of the image" /></figure>
      <p class="meta">Collaborator — Prof. Name, University</p>
    </div>
  </div>
</section>
```

Notes:
- Alternate `class="section"` and `class="section band"` between projects — the
  `band` version has a slightly different background, which makes them easier to
  tell apart as you scroll. (Look at how the existing five alternate.)
- `id="my-new-project"` is the project's anchor. If you want a card on the Home
  page to link to it, that card's link on `index.html` should end with the same
  `#my-new-project`.
- The `<p class="meta">…</p>` line is the collaborator/sponsor credit.
- To put the figure **beside** the text (a tall, narrow figure) instead of
  below it, use the two-column layout — copy the "Physics-Informed RL" block
  (the one that uses `rproj-split` and `rfig rfig-side`).

---

## 5. Editing the People page (`people.html`)

**To add a student** (grad, undergrad, joint, or alumni) — find the right
heading (e.g. `GRADUATE RESEARCHERS`) and copy one line:

```html
<div class="person"><div class="n">Full Name</div><div class="d">ME</div></div>
```

Change the name; `ME`/`CS`/etc. is their field. Paste it among the others.

**To add a collaborator** (with a round photo):

```html
<div class="collab"><img class="collab-photo" src="assets/images/people-firstname.jpg" alt="Dr. Name" /><div class="collab-text"><div class="n"><a href="https://their-website.com">Dr. Name</a></div><div class="d">Title, Department, University</div></div></div>
```

Put their photo in `assets/images/` first (see section 8), and point `src` at it.

**To edit your bio** — find `Bingling Huang, Ph.D.`; each `<p>…</p>` below it is
one paragraph of the bio. Edit the words inside.

---

## 6. Editing the Publications page (`publications.html`)

Papers are numbered **automatically** — you never type a number. Just add the
paper in the right list and everything renumbers itself (the two lists number
continuously, so the conference list keeps counting up from where the journal
list ended).

There are two lists: `REFEREED JOURNALS` and `CONFERENCE PROCEEDINGS &amp;
ABSTRACTS`. To add a paper, copy one line into the right list:

```html
<li class="pub"><div><p class="t"><a href="https://link-to-paper.com">Paper Title Goes Here</a></p><p class="m">Authors — <em>Venue / Journal</em>, Year.</p></div></li>
```

- The `<a href="…">` is the link; put the paper's URL between the quotes.
- If a paper has **no** link yet, drop the `<a>` part and just keep the title:
  `<p class="t">Paper Title Goes Here</p>`.
- `<em>…</em>` italicizes the venue name.
- New papers usually go at the **top** of their list (newest first).

---

## 7. Editing the News page (`news.html`)

Each item is one line. Copy one to add a new item:

```html
<div class="news-item"><div class="date">2026</div><div><h3>Headline of the news</h3><p>A sentence or two with the details.</p></div></div>
```

Newest items go at the top. Change the year in `<div class="date">2026</div>`.

Remember: the Home page shows its own copy of the latest news, so update those
lines in `index.html` too if you want them to match.

---

## 8. Adding images

1. Put the image file into the `assets/images/` folder.
2. Give it a clear, simple name — all lowercase, no spaces (use hyphens).
   Examples: `research-newproject.png`, `people-jane-doe.jpg`.
3. In the page, point the `src` at it: `src="assets/images/your-file-name.png"`.
4. Always fill in the `alt="…"` with a short description (used by screen readers
   and shown if the image fails to load).

Keep images reasonably small (under ~1–2 MB each) so pages load fast. JPG is
best for photos, PNG for diagrams/logos with sharp edges or transparency.

---

## 9. Re-publishing your changes (GitHub Pages)

After you save an edited file, the live site does **not** change until you
upload the new file to GitHub. No command line needed:

1. Go to your repository on **github.com** and sign in.
2. Click **Add file → Upload files** (top right).
3. Drag in the file(s) you changed.
   - If you edited `research.html`, drag in `research.html`.
   - If you added an image, drag that image into the repo's `assets/images`
     folder (dragging the whole `assets` folder also works).
4. Scroll down, click **Commit changes**.
5. Wait about a minute — GitHub rebuilds the site automatically.

> **Uploading a file with the same name replaces the old one** — that's exactly
> how you update a page. You don't need to delete the old one first.

Full first-time setup (creating the repo, turning Pages on) is in
`PUBLISHING-STEPS.md` in this same folder.

---

## 10. If a change doesn't show up

Your browser caches (remembers) the old page. After re-publishing:

- Do a **hard refresh**: `Cmd + Shift + R`.
- Or open the site in a **private/incognito** window.
- Give it a minute or two after committing — publishing isn't instant.

If a page still looks wrong, double-check you actually **uploaded** the file you
edited (a common slip is editing the file on your computer but forgetting the
upload step).

---

## 11. Keep these files OUT of the public repo

Your GitHub repository is **public** — anyone can see whatever you upload. Do
**not** upload these:

- `Website-Content.docx` (your source content doc)
- your CV / résumé
- the `figures/` and `figure-People/` source folders
- any drafts or private notes

Only these belong in the repo: the six `.html` pages, the `assets` folder
(`css`, `js`, `images`), the `.nojekyll` file, and — if you like — this
`README.md` and `PUBLISHING-STEPS.md` (both are harmless and helpful to keep).

---

## Quick reference

- **Change wording** → edit the matching `.html` file, save, upload it to GitHub.
- **Change a color or font** → edit `assets/css/style.css`, upload it.
- **Add a person / paper / news item / project** → copy an existing block on that
  page, edit it, upload the page.
- **Add a picture** → drop it in `assets/images/`, point `src` at it, upload both.
- **Don't see your change?** → hard refresh (`Cmd + Shift + R`) and confirm you
  uploaded the file.

That's everything. Small edits are safe — change the words between the tags,
save, upload. When in doubt, keep a backup copy of a file before you edit it.

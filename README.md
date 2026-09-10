# Viss Family Stories

This repo holds the source files for [stories.vissfamily.com](https://stories.vissfamily.com/) — the website where we're collecting family stories. You don't need to be a programmer to add a story here; this guide walks through it step by step.

## Clone the repo

"Cloning" just means downloading a copy of this project onto your computer.

1. Install [Git](https://git-scm.com/downloads) if you don't already have it.
2. Open a terminal and run:

   ```
   git clone https://github.com/lviss/stories.vissfamily.com.git
   ```

3. This creates a `stories.vissfamily.com` folder with everything in it.

If you'd rather not touch the terminal at all, [GitHub Desktop](https://desktop.github.com) does the same thing with buttons and windows instead of typed commands — it's a friendlier way to clone the repo, make changes, and open pull requests (see [Submit a PR](#submit-a-pr) below).

## Install Hugo

This site is built with [Hugo](https://gohugo.io), a tool that turns simple text files into the actual website. To preview your changes before they go live, you'll need it installed locally.

1. Go to the [official Hugo install instructions](https://gohugo.io/installation/) and follow the steps for your operating system.
2. **Important:** install the **extended** version — the site's theme needs it to work correctly. The install docs make it clear which download or command gives you the extended edition.
3. Try to match version **0.166.0**, since that's the version used to build the live site (check `.github/workflows/hugo.yml` if it's ever updated) — this keeps your local preview looking the same as what actually gets published.

On a Mac, the quickest way is:

```
brew install hugo
```

On Windows or Linux, follow the [official docs](https://gohugo.io/installation/) for the option that matches your system.

## Add a new story

Stories are organized by person. Here's the pattern to follow, based on how existing stories are set up:

1. Find (or create) the folder for the storyteller under `content/`, e.g. `content/lane/` or `content/max/`. If it doesn't exist yet, create the folder along with an `_index.md` file inside it that looks like:

   ```
   ---
   title: "YourName"
   ---
   ```

2. Inside that person's folder, create a new folder for your story, e.g. `content/lane/my_new_story/`. Use lowercase words separated by underscores for the folder name.
3. Inside your new story folder, create a file named `index.md` with this format at the top (this is called "front matter" — it's metadata Hugo reads before the story text):

   ```
   +++
   date = '2026-09-10T08:01:51-07:00'
   draft = false
   title = 'My new story'
   +++
   Your story text goes here!
   ```

   - `date` — when the story was added (any reasonable date/time works).
   - `draft` — set to `false` so the story actually appears on the live site. (If you leave it as `true`, it stays hidden from everyone except you previewing locally.)
   - `title` — the story's headline, shown on the site.

4. To add a photo, drop the image file (e.g. `beach.jpg`) into the same story folder as `index.md`, then reference it in the story text like this:

   ```
   ![A short description of the photo](beach.jpg "A short description of the photo")
   ```

## Preview locally

Before sharing your changes, you can see exactly how they'll look on the real site:

1. Open a terminal in the repo folder.
2. Run:

   ```
   hugo server -D
   ```

   The `-D` flag also shows any stories still marked `draft = true`, so you can preview your work before you're ready to make it public.
3. Hugo will print a local address, usually `http://localhost:1313/` — open that in your browser to see the site.
4. Leave the command running while you edit; the preview updates automatically as you save changes. Press `Ctrl+C` in the terminal to stop it when you're done.

## Submit a PR

Once your story looks good, it needs to be reviewed before it goes live. This happens through a "pull request" (or "PR") — a request to merge your changes into the live site, which the repo owner (Lane) reviews and approves before anything is published.

**Easiest way — no terminal needed:**

1. On GitHub, navigate to the file or folder you want to add or change (or use "Add file" to create a new one).
2. Click the pencil (✏️) icon to edit, or use "Add file" to upload a new story and its image.
3. Make your changes, then scroll down and save. GitHub will automatically offer to open a pull request for you (usually labeled "Propose changes") — just follow the prompts.

This is the quickest option for a small text fix or a straightforward new story.

**Local way — if you're previewing your story first (per the steps above):**

1. Create a new branch — think of this as a separate workspace for your changes so you don't affect the live site directly:

   ```
   git checkout -b my-story-branch
   ```

2. Add and commit your changes:

   ```
   git add .
   git commit -m "Add my story"
   ```

3. Push your branch and open a pull request:

   ```
   git push -u origin my-story-branch
   ```

   Then go to GitHub, and it will offer to open a pull request from your new branch.

If you're using GitHub Desktop instead of the terminal, it has the same steps as clickable buttons: create a branch, commit your changes, push, and click "Create Pull Request."

Either way, once your pull request is open, Lane will review it and merge it — and your story will go live on the site.

# Project

The marketing website. It is plain HTML and CSS. GitHub Pages serves the repository root from `main`.

- Keep the site free of a build step, unless a task asks for one.
- `index.html` is the marketing page. `legal.html` lists the legal documents. `privacy.html` is the privacy notice. `styles.css` holds the shared styles.

## Legal documents

The privacy notice is the page `privacy.html`. Its master copy is the Word file `Privacy Notice.docx` in Google Drive, in `03 Compliance & Security/05 Privacy Notices & Terms/Website`.

The complaints procedure and the accessibility statement are Word files in `documents/`. The site links to them as downloads.

To change the privacy notice, do these steps:

1. Change the Word master first.
2. Make `privacy.html` repeat the same text, sentence for sentence.
3. Set the "Last updated" date on the page.
4. Keep the heading ids, because other apps link to them, for example `privacy.html#symly-administrators`.
5. Set the `<lastmod>` of `privacy.html` in `sitemap.xml`.

To change a Word file in `documents/`, do these steps:

1. Get the new version of the Word file from the owner.
2. Replace the file in `documents/`. Keep the same file name.
3. Commit the file.

- Do not edit the Word files here. Change only the master copy.
- Do not write the privacy notice in a different text from its Word master.
- Do not write the complaints procedure or the accessibility statement as an HTML page.
- Keep the file names in `documents/`, because other pages and documents link to them.

## How to work

Do these steps for each change:

1. Create a branch and a worktree in `../worktrees/dental-website/`. Do not work in the main checkout.
2. Make the change. Follow the rules in the sections below.
3. Run the checks in [Verification](#verification).
4. Start two adversarial review agents to review the change. Fix each issue that they find.
5. Do an aggressive cleanup pass on the changes.
6. Report what you ran, what failed, what is not finished, and what you skipped and why.
7. After the merge, clean up as [Branches and worktrees](#branches-and-worktrees) says.

- Change only what the task needs. Leave other work alone, and commit only your files.
- When you replace markup or styles, delete the old markup or styles.
- After a CSS change, update the `styles.css?v=` hash in every page. The hash is the first 10 characters of the SHA-256 of `styles.css`. Run this command:

  ```sh
  H=$(shasum -a 256 styles.css | cut -c1-10); sed -i '' "s/styles\.css?v=[0-9a-f]*/styles.css?v=$H/" *.html
  ```

- When a page changes, set its `<lastmod>` in `sitemap.xml` to the date of the change.
- When you move an asset, update its references.

## Branches and worktrees

Put each worktree in `../worktrees/dental-website/<name>`. The shared `worktrees` folder is next to the main checkout. Do not put a worktree in the repo folder, because tools scan it. Do not put a worktree loose next to the repo folder.

- In the main checkout, create one with `git worktree add -b <branch> ../worktrees/dental-website/<name> main`.

When your work merges into `main`, clean up after it at once. Do not ask the user first:

1. Delete the branch locally and on the remote.
2. Remove each worktree that you made.
3. Run `git worktree prune`.

- Do not delete a branch or worktree that has unmerged commits or uncommitted changes.
- Do not remove a locked worktree. Another session uses it.
- Do not delete `main`. GitHub Pages serves the site from it.

## Destructive actions

Ask the user before each destructive action. Do it only after a clear yes, or when the request already allows it.

- Destructive actions include: delete a branch, force-push, rewrite or amend pushed history, `git reset --hard`, delete files, worktrees or data, and drop or change a database.
- Name the action and its targets. Say if you can undo it.
- A yes for one action does not apply to the next action.
- The cleanup after a merge needs no yes. [Branches and worktrees](#branches-and-worktrees) gives its steps and limits.

## Writing

Write docs, code comments, commit messages and PR descriptions in ASD-STE100 Simplified Technical English:

- Write one topic in each sentence.
- Keep instructions to 20 words or fewer, and descriptions to 25 words or fewer.
- Use the active voice and simple tenses.
- Use each word with one meaning only. Give a technical name its meaning the first time you use it.
- Do not leave out "a", "an" or "the".
- Put steps in a list, with one instruction in each step.

Code, commands, file names and page copy are not in this rule.

## Design and content

- Use the CSS variables and shared styles that exist. Do not make new ones for the same purpose.
- Keep the warm paper, plum and mint palette, the system fonts and the responsive product illustrations consistent.
- Use `favicon.svg` for the purple brand mark and `assets/symly-wordmark.svg` for the wordmark. Keep other artwork in `assets/`.
- When you edit `assets/symly-dental-social.svg`, generate the 1200×630 sharing PNG again.
- Keep illustrations true to the app, and use fictional data only. Never include secrets or real patient data.
- The primary action is "Book a demo" through `hello@symlydental.com`. Pricing is by enquiry.
- Wrap the `<body>` content of every page in `<!--email_off-->` … `<!--/email_off-->`.
- The CSP blocks the email-decoding script of Cloudflare. Without the wrapper, addresses show as "[email protected]".
- `.well-known/security.txt` gives the security contact. `.nojekyll` lets GitHub Pages serve the dot-folder.
- The owner renews `security.txt` each year.
- `security.html` may only repeat the security measures in the data processing agreement. Change the agreement first, then the page.
- Do not use absolute words such as "never", "every" or "at any time" on `security.html` unless the measure is verified in production.
- The Cyber Essentials certificate expires on 18 November 2027. Renew it before then, or remove the claim from `security.html`.
- The company is Symly Ltd. The product is Symly. Do not use "Symly Dental" as a name.
- Check new product claims with the owner.
- Do not invent prices, testimonials, guarantees or certifications.
- Keep the company details and the privacy link.
- When data collection or providers change, update the privacy notice.
- Keep the metadata, canonical URLs and the sitemap consistent with `https://symlydental.com/`.
- Keep `data-nosnippet` on fictional previews.

## Verification

- Check the changed layouts at desktop and mobile widths. Also check the links and assets.
- Run `git diff --check`.
- A change to documentation only needs a review of the diff.
- Do not report a blocked check as passed.

# Ten and a Half · 十点半

A small static website for the Lab Westhafen card deck: searchable trivia answers and special-card explanations. No server, database, API keys, or build step is needed to publish the included HTML files.

## Files to upload

```text
.
├── index.html                 # Lab Westhafen homepage
├── ten-and-a-half/
│   └── index.html             # Searchable answers and card explanations
├── CNAME                      # Custom domain: labwesthafen.com
├── .nojekyll                  # Publish plain files without Jekyll
└── README.md
```

The repository can be named `ten-and-a-half`. With the custom domain configured, the folder above provides the permanent QR destination:

**https://labwesthafen.com/ten-and-a-half/**

## Publish with GitHub Pages

1. Create the public repository and upload these files at its root. Upload the extracted files, not the ZIP archive or an extra enclosing folder.
2. Open **Settings → Pages**.
3. Choose **Deploy from a branch**, branch **main**, folder **/(root)**, then save.
4. Set the custom domain to **labwesthafen.com**, without a URL path.
5. At the domain's DNS provider, set these website records. Preserve unrelated email MX/TXT records.

| Type | Host | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | gravellent.github.io |

The `www` value assumes the repository belongs to **Gravellent**. Use the actual owner's `<username>.github.io` if the repository is under another account.

6. Once GitHub's DNS check passes and a certificate is available, enable **Enforce HTTPS**.
7. Open the full QR destination on a phone and verify an answer before sending the cards to print.

References: [GitHub Pages setup](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site) · [Custom-domain DNS](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

## Update the page

Edit `ten-and-a-half/index.html` and commit to `main`. GitHub Pages will republish it. Keep the `/ten-and-a-half/` path stable because it is encoded in the printed QR.

Each trivia card is an `<article data-card>` containing three visible statements and a collapsed `<details>` answer. If statement order changes, update both the displayed list and the answer number. Do not assume the third statement is the lie: the current deck deliberately varies the answer position.

The sample includes the reviewed 29-card answer key, Seattle at −4, and the current One-Way Ticket effect. Fictional character stories and Habramqi are identified separately. Search and answer reveals run entirely in the browser.

## Preview locally

From this directory:

```sh
python -m http.server 8000
```

Then visit `http://localhost:8000/ten-and-a-half/`.

No tracking or third-party fonts are loaded. The pages currently request search engines not to index them; this is a preference, not access control. The published website and its answer key are public.

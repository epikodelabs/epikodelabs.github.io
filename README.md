# epikodelabs — License & Pricing Page

This directory contains the **epikodelabs** landing page (`index.html`) — a pricing and licensing portal for the [streamix](https://epikodelabs.github.io/streamix) and [actionstack](https://epikodelabs.github.io/actionstack) libraries.

## How it works

1. **User signs in with GitHub** — clicking "Sign in with GitHub" (in the header or on any pricing card) redirects to the [license-server](../license-server/) which handles the OAuth flow. After successful authentication, the user is redirected back and their GitHub avatar appears in the header.

2. **User purchases a license** — once signed in, the purchase buttons become enabled. Clicking one opens a [Paddle](https://paddle.com) checkout overlay. The user pays for a commercial license (one-time fee).

3. **User gets access to private repos** — after a successful purchase, the license-server grants the user's GitHub account access to the private repositories for the purchased library. This is done via GitHub API (adding the user as a collaborator or inviting them to the private repo).

## Directory structure

```
index/
├── index.html          # Landing / pricing page
├── README.md           # This file
├── streamix/           # Streamix documentation site (VitePress build)
│   ├── index.html
│   ├── PRICING.html
│   └── ...
└── actionstack/        # Actionstack documentation site (VitePress build)
    ├── index.html
    ├── PRICING.html
    └── ...
```

## Key flow: payment before repo access

The critical design principle is **payment before access**:

- The documentation sites (`streamix/`, `actionstack/`) are **public** — anyone can read the docs.
- The **source code repositories** on GitHub are **private** — only paying customers get access.
- The pricing page (`index.html`) is the bridge: users authenticate, purchase, and then the license-server provisions their GitHub access automatically.

This means:
- A user cannot clone/fork the repos without purchasing a license.
- After purchase, the license-server adds their GitHub account as a collaborator to the relevant private repo.
- The user receives an email confirmation and can immediately access the repository.

## Local development

Open `index.html` directly in a browser to preview the page. The GitHub OAuth flow requires the license-server to be deployed (it uses a Firebase Cloud Functions URL).

## Related

- [Streamix docs](https://epikodelabs.github.io/streamix) — public documentation.
- [Actionstack docs](https://epikodelabs.github.io/actionstack) — public documentation.

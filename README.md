# The Usual Spot

A privacy-first social media prototype made with plain **HTML, CSS and JavaScript**.
No backend, no database, no API, no frameworks. Everything is saved in your own browser.

## How to run
Unzip the folder and double-click `index.html`. That's it.

## Folder structure
```
.
├── index.html          Home page
├── pages/
│   ├── login.html      Log in
│   ├── signup.html     Create an account
│   ├── feed.html       Main feed (write, like, delete posts)
│   ├── profile.html    Your profile (add ?u=ada to see someone else's)
│   ├── privacy.html    Privacy center (export / delete your data)
│   └── about.html      About us
├── src/
│   ├── css/style.css   All the styling
│   └── js/main.js      All the JavaScript
├── assets/img/
│   ├── logo.svg
│   └── party.jpg       Photo used in the demo post
└── README.md
```

## How it works
- Every page has `<body data-page="...">`. At the bottom of `main.js`, the code reads that name and runs the matching `setup...()` function.
- **Saving data:** users and posts go in `localStorage`. The "who is logged in" info goes in `sessionStorage`, so you get logged out when you close the tab.
- **Page protection:** feed, profile and privacy send you to the login page if you are not logged in (`protectPage()`).
- **Navbar:** links with class `guest-only` show when logged out, and `user-only` when logged in (`setupNavbar()`).
- **Demo data:** `addDemoData()` adds Ada, Marco and Luz on the first visit so the feed isn't empty. They can't be logged into.

## Privacy and security stuff
- Nothing is sent over the internet and there are no trackers, cookies or external fonts.
- Passwords are scrambled with `hashPassword()` before saving. Real passwords are never stored.
- `safe()` cleans all user text so people can't inject scripts (XSS).
- The Privacy center lets you export or delete your data.

## Colors
Blue (main), gray (backgrounds and text), green (only for "private / safe" things).

## Limits (being honest)
- Accounts only exist in the browser they were made in.
- My `hashPassword()` is a simple homemade function. A real app needs a server with bcrypt or argon2.
- Anyone with access to the browser could read localStorage.

## Ideas for later
Dark mode, edit posts, followers, encrypted messages, a real backend.

## Photo post
`addPhotoPost()` in `main.js` adds one demo post with a photo. Posts can have an optional `image` path, and `postHtml()` shows it with an `<img>` tag.

# Copy and Share (Kopyala ve Paylaş) Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Implement a translatable "Copy and share" section right after the post content in `post.hbs` that dynamically displays the clean, protocol-stripped URL of the current page and copies the full URL to the clipboard on click with a transient success notification.

**Architecture:** We will insert a `.copy-share-link` HTML container in `post.hbs` below the post content block. The container will utilize the Ghost translation helper `{{t}}`. A DOMContentLoaded listener will dynamically strip the protocol from the page location and inject the clean URL as the link's anchor text. A standard helper function `copyToClipboard` will copy the absolute URL to the clipboard, injecting a localized notification with a 3-second fadeout style.

**Tech Stack:** Handlebars (`.hbs`), CSS, Vanilla JavaScript, Ghost Theme Engine.

---

### Task 1: Add localization strings

**Files:**
- Modify: `locales/tr.json:1`
- Modify: `locales/en.json:1`

- [ ] **Step 1: Add Turkish translation keys**
  Add the keys for `"Copy and share"` and `"Link copied!"` inside `locales/tr.json`.

  ```json
  "Copy and share": "Kopyala ve paylaş",
  "Link copied!": "Bağlantı kopyalandı!"
  ```

- [ ] **Step 2: Add English translation keys**
  Add the keys for `"Copy and share"` and `"Link copied!"` inside `locales/en.json`.

  ```json
  "Copy and share": "Copy and share",
  "Link copied!": "Link copied!"
  ```

- [ ] **Step 3: Verify locales syntax is valid JSON**
  Check that both files are valid JSON.

---

### Task 2: Implement post.hbs markup, styling, and logic

**Files:**
- Modify: `post.hbs:7-16`

- [ ] **Step 1: Add HTML markup, CSS, and JS script in post.hbs**
  Insert the copy-share container, styling, and script in `post.hbs` right after the post content is closed.

  ```html
  {{!< default}}

  <main class="site-main">

      {{#post}}
          {{> "content" width="wide"}}
      {{/post}}

      <div class="copy-share-link">
          {{t "Copy and share"}}: <a href="#" id="copy-share-link" onclick="copyToClipboard(event, '{{url absolute='true'}}')"></a>
      </div>

      <style>
      .copy-share-link {
          width: 70%;
          margin: 20px auto;
          padding: 20px;
          font-size: 2rem;
          text-align: center;
      }

      .copy-share-link a {
          color: var(--brand-color);
      }

      @keyframes fadeinout {
          0% { opacity: 0; }
          10% { opacity: 1; }
          90% { opacity: 1; }
          100% { opacity: 0; }
      }
      </style>

      <script>
          document.addEventListener('DOMContentLoaded', () => {
              const link = document.getElementById('copy-share-link');
              if (link) {
                  link.textContent = window.location.host + window.location.pathname;
              }
          });

          function copyToClipboard(event, text) {
              event.preventDefault();
              const dummyInput = document.createElement('input');
              dummyInput.value = text;
              document.body.appendChild(dummyInput);
              dummyInput.select();
              document.execCommand('copy');
              document.body.removeChild(dummyInput);

              const notification = document.createElement('div');
              notification.textContent = '{{t "Link copied!"}}';
              notification.style.cssText = `
                  position: fixed;
                  bottom: 1rem;
                  right: 1rem;
                  padding: 1rem;
                  background-color: #333;
                  color: #fff;
                  border-radius: 0.5rem;
                  opacity: 0;
                  z-index: 9999;
                  animation: fadeinout 3s forwards;
              `;
              document.body.appendChild(notification);

              setTimeout(() => {
                  document.body.removeChild(notification);
              }, 3000);
          }
      </script>

      {{#if @custom.show_related_posts}}
          {{> "related-posts"}}
      {{/if}}

      {{#post}}
          {{> "comments"}}
      {{/post}}

  </main>
  ```

---

### Task 3: Theme validation and compilation check

- [ ] **Step 1: Install dependencies**
  Run `npm install` to make sure all build dependencies (like gulp and gscan) are installed.

- [ ] **Step 2: Run theme validation tests**
  Run `npm run test` (which triggers `gscan .`) to verify that the theme has no validation errors or syntax issues.

- [ ] **Step 3: Run development build**
  Run `npm run dev` or `npx gulp` to verify that assets compile successfully.

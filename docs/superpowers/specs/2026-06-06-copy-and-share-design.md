# Design Spec: Copy and Share Feature (Kopyala ve Paylaş)

**Date:** 2026-06-06  
**Status:** Approved  

---

## 1. Requirements & Goals
The goal is to port the "Kopyala ve paylaş" (Copy and Share) feature from the `@old-version/` codebase to the current version of the Ghost theme.

### Functional Requirements:
- Display a "Copy and share" link on individual post pages.
- Place the link section right after the post content but before related posts and comments.
- Dynamically detect and display the clean, protocol-stripped URL (e.g. `domain.com/post-slug/`) as the visible link text on page load.
- When clicked, copy the absolute URL (including `https://` protocol) to the user's clipboard and show a temporary floating notification reading "Link copied!".
- Make all user-facing text translatable using Ghost's native localization system `{{t}}`.

---

## 2. Architecture & Components

### 2.1 Markup & Placement (`post.hbs`)
We will place the container in `post.hbs` right after the post content renders:
```html
<div class="copy-share-link">
    {{t "Copy and share"}}: <a href="#" id="copy-share-link" onclick="copyToClipboard(event, '{{url absolute='true'}}')"></a>
</div>
```

### 2.2 Styles (`post.hbs`)
We will place the CSS styles within `<style>` tags scoped to the template:
```css
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
```

### 2.3 Client-Side Logic (`post.hbs`)
We will inject JS to:
1. Dynamic URL Clean Text: On page load, strip protocol from browser location and render it.
2. `copyToClipboard(event, text)`: Write the full URL to the clipboard using a transient input element, then inject a floating notification with a 3-second fadeout.

```javascript
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
```

---

## 3. Localization Translations

### `locales/tr.json`
```json
"Copy and share": "Kopyala ve paylaş",
"Link copied!": "Bağlantı kopyalandı!"
```

### `locales/en.json`
```json
"Copy and share": "Copy and share",
"Link copied!": "Link copied!"
```

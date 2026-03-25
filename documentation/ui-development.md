# UI Development: Navigation

The ESD Suite Framework uses a standard Webview for its frontend. This means you can use standard web technologies (HTML, CSS, and JavaScript) to build your pages.

## 1. Navigation Between Pages

Navigating between different views works exactly like a traditional website. Since your files are loaded locally, you use relative paths to link pages together.

### Using HTML Links
If your `MAIN_PAGE` is set to `ui/pages/index.html` and you create a second page at `ui/pages/settings.html`, you can navigate to it using a standard anchor tag:

```html
<!-- Inside index.html -->
<a href="settings.html">Go to Settings</a>
```

### Using JavaScript
You can also trigger navigation programmatically using JavaScript's `window.location`:

```javascript
// Navigate to another page in the same folder
window.location.href = "settings.html";

// Navigate to a page in a different folder
window.location.href = "../other/example.html";
```

> **Note on Paths:** All relative paths are evaluated from the location of the *currently loaded* HTML file. 

---

## 2. Advanced: Web Components
If you want encapsulated styles and custom tags like `<my-widget>`, you can use native browser Web Components:

```html
<script>
    class MyWidget extends HTMLElement {
        connectedCallback() {
            this.innerHTML = `<div style="border: 1px solid #333; padding: 10px;">I am a custom widget!</div>`;
        }
    }
    customElements.define('my-widget', MyWidget);
</script>

<!-- Now use it anywhere in the HTML -->
<my-widget></my-widget>
```

---

## 3. Best Practices
* **Keep assets relative:** Use `./` or `../` for images, CSS, and JS files so they resolve correctly regardless of absolute deployment locations.
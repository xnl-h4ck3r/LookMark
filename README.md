# LookMark
A browser bookmark to show hidden and disabled elements on a targets page.

This was made with the help of ChatGPT in responses to this [tweet](https://x.com/ctbbpodcast/status/1717151268622233614?s=20) from [@ctbbpodcast](https://twitter.com/ctbbpodcast) and taking inspiration from an example by [@joaxcar](https://twitter.com/joaxcar)

Just create a browser bookmark, setting the URL to the code below.
Then go to a target page and click the bookmark. Hidden elements will be shown and highlighted in red with an identifier, and Disabled fields will be enabled and highlighted in blue with an identifier.

```javascript
javascript:document.querySelectorAll('[type=hidden],[hidden]').forEach(e => { e.type = 'text'; e.style.cssText = 'border-color: red; border-width: 3px'; const d = document.createElement('div'); d.innerHTML = `<span style="color: red;">Hidden field [${e.name}]</span>`; e.parentNode.insertBefore(d, e).appendChild(e); });document.querySelectorAll('[style*="display: none;"]').forEach(e => { e.type = 'text'; e.style.cssText = 'border-color: red; border-width: 3px'; e.style.display = 'block'; const d = document.createElement('div'); d.innerHTML = `<span style="color: red;">Hidden field [${e.name}]</span>`; e.parentNode.insertBefore(d, e).appendChild(e); });document.querySelectorAll('[style*="visibility: hidden;"]').forEach(e => { e.type = 'text'; e.style.cssText = 'border-color: red; border-width: 3px'; e.style.visibility = 'visible'; const d = document.createElement('div'); d.innerHTML = `<span style="color: red;">Hidden field [${e.name}]</span>`; e.parentNode.insertBefore(d, e).appendChild(e); });document.querySelectorAll('[disabled]').forEach(e => { e.disabled = false; e.style.cssText = 'border-color: blue; border-width: 3px'; const d = document.createElement('div'); const fieldName = e.getAttribute('name') || e.getAttribute('id'); d.innerHTML = `<span style="color: blue;">Disabled [${fieldName}]</span>`; e.parentNode.insertBefore(d, e).appendChild(e); });
```

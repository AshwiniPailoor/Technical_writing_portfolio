# DevDocs Style Guide
### Writing Standards for Developer Documentation

**Version:** 1.3 | **Maintained by:** Documentation Team

---

## 1. Voice and Tone

Developer documentation should feel like a knowledgeable colleague 
helping you get something done — not a legal document.

| ✅ Do this | ❌ Not this |
|-----------|------------|
| "Click **Save**." | "The user should proceed to click the Save button." |
| "This returns a JSON object." | "This functionality returns a JSON-formatted object." |
| "If the request fails..." | "In the event that the request should fail..." |

**Use second person ("you").** Address the reader directly.

**Use active voice.** "The API returns a token." Not "A token is returned by the API."

**Use present tense.** "This function takes two arguments." Not "This function will take two arguments."

---

## 2. Formatting Code

### Inline code

Use backtick formatting for: file names, functions, parameters, 
command-line input, and values that appear literally in code.

> The `config.json` file controls all environment settings.  
> Set `debug` to `true` to enable verbose logging.

### Code blocks

Use fenced code blocks with a language identifier for all multi-line code.

````markdown
```javascript
const client = new APIClient({
  apiKey: process.env.API_KEY,
  timeout: 5000,
});
```
````

Always test code samples before publishing. Non-working examples are 
worse than no examples.

---

## 3. Headings

Use sentence case for all headings (capitalize only the first word 
and proper nouns).

| ✅ Correct | ❌ Incorrect |
|-----------|-------------|
| Set up authentication | Set Up Authentication |
| API rate limits | API Rate Limits |
| Troubleshoot connection errors | Troubleshoot Connection Errors |

Use H2 (`##`) for major sections. Use H3 (`###`) for subsections. 
Avoid H4 and deeper — restructure the content instead.

---

## 4. UI Element Naming

When referring to UI elements, match the label exactly as it appears 
in the product, and bold it.

> Click **New Project**.  
> Select **Settings → Integrations → Webhooks**.

Use these terms consistently:

| UI element | Use this term |
|------------|---------------|
| ☰ (hamburger) | Menu icon |
| … (overflow) | More options |
| The top bar | Navigation bar |
| Pop-up window | Dialog |

---

## 5. Notes and Warnings

Use callout boxes to draw attention to important information.

**Note:** For general information the reader might find useful.

**Important:** For information that affects the outcome if missed.

**Warning:** For information about potential data loss or irreversible actions.

> ⚠️ **Warning:** Deleting a workspace is permanent. All associated 
> projects and integrations will be removed immediately.

---

*This is a writing sample created for portfolio purposes.*

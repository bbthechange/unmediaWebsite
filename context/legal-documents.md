# Legal Documents System

This site hosts privacy policies and terms & conditions for multiple apps. Each app can have multiple versioned documents.

## Directory Structure

```
legal/
  {app-name}/
    privacy-policy/
      v1.html
      v2.html
      latest.html       ← always a copy of the highest version
    terms-and-conditions/
      v1.html
      latest.html
```

- `{app-name}`: lowercase, hyphenated (e.g., `hangout`, `my-other-app`)
- Document types: `privacy-policy` and `terms-and-conditions`
- Versions: `v1.html`, `v2.html`, etc. (sequential integers)
- `latest.html`: always an exact copy of the highest-numbered version file

## URL Pattern

Documents are accessed at:
```
/legal/{app-name}/privacy-policy/latest.html
/legal/{app-name}/privacy-policy/v1.html
/legal/{app-name}/terms-and-conditions/latest.html
/legal/{app-name}/terms-and-conditions/v2.html
```

Apps should link to `/legal/{app-name}/{doc-type}/latest.html` so users always see the current version.

## Adding a New App

1. Create the directory tree:
   ```
   legal/{app-name}/privacy-policy/
   legal/{app-name}/terms-and-conditions/
   ```

2. Create `v1.html` for each document type using the HTML template below.

3. Copy each `v1.html` to `latest.html` in the same directory.

## Adding a New Version of an Existing Document

1. Determine the next version number by checking the existing `v*.html` files in the document's directory.

2. Create the new `v{N}.html` file using the HTML template below. Update the effective date and content as needed.

3. **Replace** `latest.html` with an exact copy of the new version file.

Previous versions are kept as-is for historical reference.

## HTML Template

All legal documents use this template. The document body content must be preserved exactly as provided — do not add, remove, or modify any language in the legal text.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{Document Title} - {App Display Name}</title>
    <link rel="icon" type="image/png" href="/favicon.ico">
    <link rel="shortcut icon" href="/favicon.ico">
    <style>
        body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; line-height: 1.6; max-width: 700px; margin: 40px auto; padding: 0 20px; color: #333; }
        h1 { font-size: 24px; margin-bottom: 4px; }
        h2 { font-size: 20px; margin-top: 32px; }
        h3 { font-size: 17px; margin-top: 24px; }
        h4 { font-size: 15px; margin-top: 20px; }
        footer { margin-top: 40px; font-size: 14px; color: #888; border-top: 1px solid #eee; padding-top: 20px; text-align: center; }
    </style>
</head>
<body>

    <!-- Paste the document body content here exactly as provided. -->

    <footer>
        <p>&copy; 2025 Unmedia Social LLC. All rights reserved.</p>
        <p><a href="/">unmediasocial.com</a></p>
    </footer>
</body>
</html>
```

### Template Field Reference

| Placeholder | Example | Notes |
|---|---|---|
| `{Document Title}` | `Privacy Policy` or `Terms and Conditions` | Used in `<title>` only |
| `{App Display Name}` | `Slanga` | The user-facing app name |

### Notes

- Do not add, remove, or rephrase any language in the legal document body. Only wrap it in the HTML template.
- If the source document has Cloudflare email obfuscation (`class="__cf_email__"`, `/cdn-cgi/` scripts), decode the emails back to plain `mailto:` links and remove the Cloudflare script tags.

# PDFix SDK Template Examples

This repository contains practical examples of **Template Layout configurations** used for auto-tagging non-tagged PDFs with the [PDFix SDK](https://pdfix.net/products/pdfix-sdk/) and [PDFix Desktop](https://pdfix.net/products/pdfix-desktop-pro/).

Templates describe how to detect visual patterns in PDFs (tables, headers, footers, text blocks, etc.) and map them to accessible tagged structures (like headings, paragraphs, and tables) — all through a flexible, human-readable JSON format.

---

## Repository Contents

Each example directory includes:

- `original.pdf` – Unstructured, non-tagged source PDF
- `original.json` – Template Layout file for structure detection
- `original_tagged.pdf` – Output PDF with semantic tagging

---

## Usage

### With PDFix SDK

You can use these templates programmatically in your SDK projects. See `AddTags` examples in official SDK sample repos:

- [Python – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_python/blob/master/src/AddTags.py)
- [Java – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_java/blob/master/src/main/java/net/pdfix/samples/AddTags.java)
- [C++ – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_cpp/blob/master/src/AddTags.cpp)
- [.NET – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_dotnet/blob/master/src/AddTags.cs)

Typical workflow:
```python
pdfix = GetPdfix()
doc = pdfix.OpenDoc("original.pdf", "")
tmpl = doc.GetTemplate()
tmplStm = pdfix.CreateFileStream("original.json", kPsReadOnly)
tmpl.LoadFromStream(tmplStm, kDataFormatJson)
tmplStm.Destroy()
tagsParams = PdfTagsParams()
doc.AddTags(tagsParams)
doc.Save("original_tagged.pdf", kSaveFull)
doc.Close()
````

---

### With PDFix Command-Line (CLI)

Use PDFix CLI to apply templates without writing any code.

**Basic command:**

```bash
pdfix_app add-tags -i original.pdf -o original_tagged.pdf -c original.json
```

Full CLI documentation:
[PDFix CLI: AddTags Command](https://pdfix.net/support/pdfix-command-line/#add-tags)

---

### With PDFix Desktop

1. Open [PDFix Desktop](https://pdfix.net/pdfix-desktop/)
2. Load an `original.pdf` file
3. Run Accessibility -> AutoTag
4. Load the `original.json`
7. Click **Run** to generate a tagged PDF

For more information, visit the user's guide:
[Auto-Tag](https://pdfix.net/user-guide-workflow-for-creating-an-accessible-pdf/?ref=ref-auto-tag#Auto-tag)

---

## What Is a Template?

Read the [PDFix Template Layout Guide](https://pdfix.net/user-guide-template/) for syntax and design best practices.

---

## Contribute

Found a layout worth templating? Want to improve an example?

* Fork this repository
* Add your new folder with `original.pdf`, `template.json`, and `tagged.pdf`
* Include a short `README.md` for context
* Open a pull request!

---

Made with 💡 by the [PDFix Team](https://pdfix.net) and the community

# PDFix SDK Template Examples

This repository contains practical examples of **Template Layout configurations** used for auto-tagging non-tagged PDFs with the [PDFix SDK](https://pdfix.net/pdfix-sdk/) and [PDFix Desktop](https://pdfix.net/pdfix-desktop/).

Templates describe how to detect visual patterns in PDFs (tables, headers, footers, text blocks, etc.) and map them to accessible tagged structures (like headings, paragraphs, and tables) — all through a flexible, human-readable JSON format.

---

## Repository Contents

Each example directory includes:

- `original.pdf` – Unstructured, non-tagged source PDF
- `template.json` – Template Layout file for structure detection
- `tagged.pdf` – Output PDF with semantic tagging

---

## Usage

### With PDFix SDK

You can use these templates programmatically in your SDK projects. See `AddTags` examples in official SDK sample repos:

- [Python – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_python/blob/master/samples/add_tags.py)
- [Java – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_java/blob/master/src/AddTags.java)
- [C++ – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_cpp/blob/master/src/AddTags.cpp)
- [.NET – AddTags Example](https://github.com/pdfix/pdfix_sdk_example_dotnet/blob/master/AddTags.cs)

Typical workflow:
```python
pdfix = GetPdfix()
doc = pdfix.OpenDoc("original.pdf", "")
tmplStm = pdfix.CreateFileStream("template.json", kPsReadOnly)
tmpl.LoadFromStream(tmplStm, kDataFormatJson)
tmplStm.Destroy()
tagsParams = PdfTagsParams()
doc.AddTags(tagsParams)
doc.Save("output.pdf", kSaveFull)
doc.Close()
````

---

### With PDFix Command-Line (CLI)

Use PDFix CLI to apply templates without writing any code.

**Basic command:**

```bash
pdfix_app add-tags -i original.pdf -o tagged.pdf -c template.json
```

Full CLI documentation:
[PDFix CLI: AddTags Command](https://pdfix.net/support/pdfix-command-line/#add-tags)

---

### With PDFix Desktop

1. Open [PDFix Desktop](https://pdfix.net/pdfix-desktop/)
2. Load an `original.pdf` file
3. Run Accessibility -> AutoTag
4. Load the `template.json`
7. Click **Run** to generate a tagged PDF

For more information, visit user's guide:
[Auto-Tag](https://pdfix.net/user-guide-workflow-for-creating-an-accessible-pdf/?ref=ref-auto-tag#Auto-tag)

---

## 🧩 What Is a Template?

Templates are JSON files that describe:

* Visual **anchors** and **initial elements**
* **Bounding boxes** and **neighbor rules**
* Custom **tag mappings** (`<Table>`, `<P>`, `<H1>`, etc.)
* Priority-based **layout detection logic**
* Optional **thresholds** and conditional behavior

Read the [PDFix Template Layout Guide](https://pdfix.net/template-layout-guide) for syntax and design best practices.

---

## Example Scenarios

| Folder                | Description                                                       |
| --------------------- | ----------------------------------------------------------------- |
| `invoice_basic`       | Identifies tables and headers in a basic invoice layout           |
| `catalog_layout`      | Detects product blocks, titles, images, and descriptions          |
| `report_multi_column` | Handles multi-column reading order with headers and footnotes     |
| `table_split_merge`   | Demonstrates text splitting and row recognition in complex tables |
| `form_like_structure` | Tags label-field patterns in simulated form layouts               |

> More examples will be added regularly — contributions welcome!

---

## License

All templates and configs: [MIT License](LICENSE)
Sample PDFs: for **educational/demo purposes only**

---

## Contribute

Found a layout worth templating? Want to improve an example?

* Fork this repository
* Add your new folder with `original.pdf`, `template.json`, and `tagged.pdf`
* Include a short `README.md` for context
* Open a pull request!

---

Made with 💡 by the [PDFix Team](https://pdfix.net) and the community

```

---

Let me know if you'd like badges (like GitHub stars, PDFix SDK versions, etc.) or a GitHub Pages site for browsing examples online.
```

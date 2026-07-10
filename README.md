# JSONPath Tester

Paste JSON and a JSONPath expression, see the matched values and their paths live, in your browser. No server, no tracking, no third-party scripts.

**Live demo:** https://0xelitesystem.github.io/json-path-tester/

## Use

Open `index.html` in any modern browser, or visit the GitHub Pages link in the repo description.

Paste JSON on the left and a JSONPath expression on the right. As you type, the tool evaluates the path locally and shows:

- Each matched value, formatted
- The concrete path to each match (for example `$.store.book[0].title`)
- A match count
- A clear error message when the JSON is invalid or the path cannot be parsed

Preset buttons load common expressions against the built-in sample so you can see how each selector behaves.

This is a practical JSONPath **subset**, not full jq or a complete JSONPath implementation. Supported:

- Root `$`
- Dot child access `$.store.book`
- Bracket child access `$['store']['book']`
- Array index including negative `$.book[0]`, `$.book[-1]`
- Wildcard `*` over arrays and objects
- Recursive descent `..`
- Unions such as `[0,2]` and `['title','author']`
- Comparison filters `[?(@.price<10)]` with operators `== != < <= > >=`
- Existence filters `[?(@.isbn)]`

Not supported: array slices like `[1:3]`, script expressions, regex filters, and function extensions. If you need those, reach for a full jq or a server-side JSONPath library.

## Why this exists

Most online JSONPath testers either ship a heavy framework, phone home with your data, or bury the tool under ads. This is a single HTML file: paste, query, read the result, close the tab. The engine is written in plain JavaScript so you can read exactly what it does.

## Privacy

Everything runs in your browser. The JSON you paste and the expressions you write never leave your machine. Verify by viewing the page source or by opening DevTools and watching the network tab. No requests are made.

## Run locally

```bash
git clone https://github.com/0xelitesystem/json-path-tester
cd json-path-tester
# Open index.html in your browser, or:
python -m http.server 8000
```

## Build

There is no build. It is a single HTML file with inline CSS and JavaScript.

## License

MIT.

## Related

- [json-formatter-and-validator](https://github.com/0xelitesystem/json-formatter-and-validator)
- [jwt-inspector](https://github.com/0xelitesystem/jwt-inspector)
- [gradient-generator](https://github.com/0xelitesystem/gradient-generator)

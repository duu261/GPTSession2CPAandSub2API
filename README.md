# ChatGPT Session Converter

A browser-only utility that converts ChatGPT Web session JSON and supported Codex OAuth JSON into importable formats for CPA, sub2api, Cockpit Tools, 9router, Codex, AxonHub, and Codex-Manager.

## Online use

Open `docs/index.html` directly, or publish the `docs/` directory as a static site.

## Important security note

This tool handles sensitive login credentials, including `accessToken` and `sessionToken`.

- Parsing and conversion happen locally in the browser.
- No token is uploaded.
- Nothing is written to browser storage.
- Never paste credentials into chat, issues, or shared documents.
- Prefer hosting this as a private operator tool, not as a public customer endpoint.

This tool only converts JSON formats. It cannot bypass Codex OAuth add-phone verification. ChatGPT Web sessions usually do not contain an OAuth `refresh_token`, so converted accounts may stop working when their access token expires.

## Supported input

The converter accepts pasted JSON or one or more JSON files, including:

- ChatGPT Web session JSON with `user.email`, `accessToken`, `sessionToken`, `expires`, `account.id`, or `account.planType`
- 9router Codex OAuth JSON
- Native Codex `auth.json`
- AxonHub Codex `auth.json`
- Codex-Manager batch import JSON

The converter also tries to recover email, account ID, user ID, plan type, and expiry from the `accessToken` JWT payload.

## Output formats

- `CPA`
- `sub2api`
- `Cockpit`
- `9router`
- `Codex`
- `AxonHub`
- `Codex-Manager`

## Local use

Open:

```text
docs/index.html
```

No build step or dependency installation is required.

## Tests

The conversion logic is covered by the Node.js test file:

```bash
node --test tests/convert-session.test.js
```

## License

MIT. Original copyright notice is preserved in `LICENSE`.

# Points API Documentation

Official documentation for the **Points API** — Saudi Arabia's unified loyalty rewards platform.

**Live at:** [docs.papp.sa](https://docs.papp.sa)

## Local development

```bash
# Install Mintlify CLI
npm install -g mintlify

# Run dev server
mintlify dev
```

Open [http://localhost:3000](http://localhost:3000) to view the docs.

## Structure

```
├── introduction/      Getting-started guides
├── authentication/    API keys & security
├── integration/       Integration walkthroughs
├── webhooks/          Webhook documentation
├── testing/           Sandbox + go-live guides
├── openapi/           OpenAPI spec (API reference)
├── logo/              Brand assets
└── docs.json          Mintlify configuration
```

## Deployment

Docs are auto-deployed via [Mintlify](https://mintlify.com). Any push to the `master` branch triggers a redeploy of [docs.papp.sa](https://docs.papp.sa).

```bash
# Standard update flow
git add .
git commit -m "docs: short description"
git push origin master
```

## Support

- Email: [support@papp.sa](mailto:support@papp.sa)
- Business dashboard: [business.papp.sa](https://business.papp.sa)

---

© 2026 Points — Ibtikarat. All rights reserved.

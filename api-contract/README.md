# Data Registry API reference

Edit [`src/openapi.yaml`](src/openapi.yaml) and its reusable components under
[`src/components/`](src/components/). The bundled
[`data-registry-api.yaml`](data-registry-api.yaml) is the published OpenAPI 3.1
contract, with
`info.version` set to `0.10.0`. The API is introduced in RHOAI 3.6; the contract
version and the RHOAI release version serve different purposes.

The contract includes Iceberg REST Catalog-shaped operations and RHOAI extensions
marked `x-rhoai-extension: true`; this does not imply full Iceberg REST
compatibility. OpenAPI-generated clients may help with experimentation, but are
not supported product SDKs.

[Browse the rendered API reference](https://opendatahub-io.github.io/data-registry/).
[`data-registry-api.html`](data-registry-api.html) is its generated source. The
published page includes the adjacent YAML file for its specification download
link. Use Node.js 24.4.1 and npm 10 or later to regenerate and validate it with
the pinned Redocly CLI:

```bash
npm ci
npm run api:lint
npm run api:bundle
npm run api:docs
```

Run these commands from the repository root. CI checks that the committed YAML
and HTML match the source.

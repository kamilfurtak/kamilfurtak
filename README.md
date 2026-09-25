<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/profile-banner-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/profile-banner-light.svg">
  <img alt="Kamil Furtak — Senior Angular Engineer. Angular, TypeScript and geospatial UI." src="assets/profile-banner-light.svg" width="1440">
</picture>

**Senior Angular Engineer · UI modernization · Reusable libraries · Geospatial interfaces**

I build Angular interfaces for complex workflows and interactive maps. My focus is preserving user workflows during UI changes, designing reusable component APIs, and making state, lifecycle and integration behavior testable.

**Core toolkit:** Angular, TypeScript, RxJS, Nx and OpenLayers.

[Portfolio & demos](https://furtak.dev/) · [Engineering decisions & review guide](engineering-notes.md) · [LinkedIn / contact](https://linkedin.com/in/kamilfurtak)

## Selected engineering work

### [ng-openlayers](https://github.com/kamilfurtak/ng-openlayers)

**Role: maintainer.** A published Angular library with 27 interactive map examples. My work includes component and event lifecycle ownership, projection changes, API compatibility and release validation.

The engineering challenge is connecting imperative OpenLayers objects to Angular's component lifecycle. The repository includes regression tests and an independent consumer that installs the built npm package.

[Try drawing on a map](https://ng-openlayers.furtak.dev/examples/draw-polygon/) · [Source & validation](https://github.com/kamilfurtak/ng-openlayers/blob/master/docs/validation.md) · [npm package](https://www.npmjs.com/package/ng-openlayers)

### [Angular UI modernization](https://furtak.dev/angular-ui-modernization-case-study/)

**Focus: replacing a table renderer while preserving feature behavior.** This Angular workbench keeps its state and form outside the table renderer. Switching between native and PrimeNG tables retains filtering, sorting, selection and draft edits.

Try selecting a case, changing the filter and writing a draft, then switch tables. The source also covers failed requests, retry and unavailable browser storage.

[Try the workbench](https://furtak.dev/angular-ui-modernization-case-study/) · [Code & tests](https://github.com/kamilfurtak/kamilfurtak.github.io/tree/main/reference-sources/angular-ui-modernization-case-study/demo) · [Decisions & scope](engineering-notes.md#ui-modernization)

This is an independent portfolio sample with fictional data, developed with AI assistance.

### [Identity integration architecture](https://furtak.dev/epuap-login-gov-integration-portfolio/)

A written case study of browser/API responsibility, generated contracts and failure boundaries around SAML and SOAP/WSDL. It demonstrates how I explain integration tradeoffs from a frontend perspective. The public artifact is a static architecture walkthrough.

[Read the architecture](https://furtak.dev/epuap-login-gov-integration-portfolio/docs/architecture.html)

## Accepted open-source contributions

Selected changes accepted by other open-source projects:

- **[bolt.diy #1322](https://github.com/stackblitz-labs/bolt.diy/pull/1322)** — added model search and keyboard navigation to the model selector, including focus handling and filtering.
- **[Hindsight #3656](https://github.com/vectorize-io/hindsight/pull/3656)** — fixed disagreement between schema generation and the batch retain configuration; added regression tests for both conflicting settings.

## How I work

I keep feature state separate from rendering, define resource ownership, and test failure paths alongside successful flows. I document the limits of each example so reviewers can distinguish demonstrated behavior from a design proposal.

I use AI tools to support implementation; design decisions, source review and verification remain my responsibility.

For Angular application, component-library or geospatial UI work, [get in touch on LinkedIn](https://linkedin.com/in/kamilfurtak).

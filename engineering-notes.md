# Engineering decisions and review guide

These notes connect my public work to the engineering decisions behind it.
Start with the demo for behavior, then follow the source and tests for detail.

## Angular library maintenance

**Project:** [ng-openlayers](https://github.com/kamilfurtak/ng-openlayers)
**My role:** maintainer of a library that builds on the existing Angular/OpenLayers wrapper work credited in its README.

**Problem.** OpenLayers creates maps, listeners and other mutable objects outside Angular. A declarative wrapper needs clear ownership when components are updated, replaced or destroyed. A successful demo alone does not establish that consumers can install and use the released package.

**My work.** Lifecycle and projection handling, compatibility work, examples and validation of the distributed package. Owned map resources and listeners have explicit teardown; consumer-supplied resources have a separate ownership boundary. The independent Angular consumer installs the built tarball rather than importing workspace source aliases.

**What to inspect.** The published site offers 27 examples, including drawing, selection and measurement. The regression suite exercises lifecycle and projection behavior; the package consumer checks the distribution boundary.

- [Interactive drawing example](https://ng-openlayers.furtak.dev/examples/draw-polygon/)
- [Map lifecycle tests](https://github.com/kamilfurtak/ng-openlayers/blob/master/libs/ng-openlayers/src/lib/map-lifecycle.spec.ts)
- [Projection state tests](https://github.com/kamilfurtak/ng-openlayers/blob/master/libs/ng-openlayers/src/lib/view-projection-state.spec.ts)
- [Independent package consumer](https://github.com/kamilfurtak/ng-openlayers/tree/master/compatibility/angular22)
- [Validation scope and limitations](https://github.com/kamilfurtak/ng-openlayers/blob/master/docs/validation.md)

**Boundary.** The wrapper has a documented API surface; it does not make every OpenLayers option dynamically mutable. Provider fixtures in browser tests and live provider behavior are separate checks.

## UI modernization

**Project:** [Angular migration workbench](https://furtak.dev/angular-ui-modernization-case-study/)
**My role:** the portfolio sample presents my approach to state ownership and adapter boundaries; it was developed with AI assistance.

**Problem.** Replacing a table widget can also replace the state that users rely on: filters, selected rows and unfinished form edits. A visually correct replacement can still break a workflow.

**Decision.** Keep the feature store and form outside both table renderers. Native and PrimeNG adapters receive the same typed inputs and emit domain events. Replacing the adapter destroys its view while preserving the feature state. PrimeNG loads on demand through Angular's deferred rendering.

**Demonstrated result.** Select `CASE-103`, filter for `map`, change the sort order and write a draft. Switch to PrimeNG and back: selection, filtering, ordering and draft edits survive. The existing browser tests also exercise retry after a simulated request failure, draft restoration and blocked storage.

**Tradeoff.** The sample uses a small in-memory dataset and client-side queries. A larger application would need a paged backend contract. The storage adapter preserves an unsaved form when persistence fails; local storage is not secure storage for sensitive data.

**Review path:** [domain and query functions](https://github.com/kamilfurtak/kamilfurtak.github.io/blob/main/reference-sources/angular-ui-modernization-case-study/demo/src/domain.ts) → [state owner](https://github.com/kamilfurtak/kamilfurtak.github.io/blob/main/reference-sources/angular-ui-modernization-case-study/demo/src/workbench.store.ts) → [renderer contracts](https://github.com/kamilfurtak/kamilfurtak.github.io/blob/main/reference-sources/angular-ui-modernization-case-study/demo/src/grid-adapters.ts) → [browser regressions](https://github.com/kamilfurtak/kamilfurtak.github.io/blob/main/reference-sources/angular-ui-modernization-case-study/demo/e2e/workbench.spec.ts).

**Scope.** This is an original public sample with fictional records. Its results establish the demonstrated workflow, not complete compatibility with a commercial grid or evidence about an employer's implementation.

## Contributions reviewed by other maintainers

- **[bolt.diy #1322](https://github.com/stackblitz-labs/bolt.diy/pull/1322), merged.** Replaced the model selector's static dropdown with search, filtered results, keyboard navigation and focus handling. Review the PR for the interaction changes.
- **[Hindsight #3656](https://github.com/vectorize-io/hindsight/pull/3656), merged.** The batch path built a schema from one configuration flag and sent its strictness setting from another. I aligned both decisions with the retain-scoped flag and added tests for both directions of the mismatch.

These are specific contributions to existing projects, alongside my maintained library and independent portfolio work.

## Integration communication

The [identity integration walkthrough](https://furtak.dev/epuap-login-gov-integration-portfolio/) explains browser/API responsibility, generated contracts and protocol-related failure modes. It is a written architecture artifact for a technical discussion; the public pages do not execute identity-provider authentication or demonstrate a production deployment.

[Back to my profile](README.md) · [Portfolio](https://furtak.dev/) · [Contact](https://linkedin.com/in/kamilfurtak)

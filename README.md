# EV_PNC_ocpi-emsp

OCPI eMSP server: Credentials, Versions, Locations, Tariffs, Tokens, Commands, Sessions and CDRs, real-time authorization with policy hook and consent gate. Bilateral OCPI with corridor CPOs.

Part of the **EV_PNC** platform: a neutral eMSP integration layer for Turkey-first, Europe-ready Plug&Charge, navigation and payments. The platform is neither a CPO nor a payment institution.

> Plug in, charging starts, payment completes in the background.

## Scope

- OCPI 2.2.1 first, 2.3.0 upgrade path; party ID from TR-03
- Real-time token authorization (EMAID tokens are not pushed); calls the policy API and the consent decision SDK, fails closed
- Selective token push gated by the consent decision (RC-GATE-001, RC-GATE-004)
- Publishes canonical events; payments, telemetry and analytics subscribe
- Seed from COPUR/ocpi (spec source)

## Tech stack

Java, Spring Boot 4, PostgreSQL, Kafka

## Packaging

- Published components: ocpi-emsp-server
- Depends on: EV_PNC_ocpi-model, EV_PNC_policy-engine, EV_PnC_Consent_contracts
- Depended on by: no repo
- Dependency rules: no cycles (ADP); depend towards more stable components (SDP); published `*-api` components hold abstractions, deployables hold concrete code (SAP). CI runs `tools/packaging_check.py --strict` from `EV_PNC_docs`.
- Owner: Backend agent · Wave 1 (now, before the 2026-12-07 gate) · Visibility: public

## Proposed layout

```
app/
modules/{credentials,locations,tariffs,tokens,commands,sessions,cdrs,authorize}
```

## Related

- Plan: `repo-plan/v2/README.md` (project files); consent repos: `EV_PnC_Consent_*` (`repo-plan/consent/README.md`)
- Docs: [EV_PNC_docs](https://github.com/COPUR/EV_PNC_docs)

## Status

Scaffold only. Not production ready.

## License

Apache-2.0 (proposed)

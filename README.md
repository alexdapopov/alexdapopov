<!--
Profile README for: github.com/alexdapopov
Paste this into alexdapopov/alexdapopov/README.md
-->

<div align="center">

# Alex Popov — Software Engineer

<img src="https://img.shields.io/badge/Systems-Engineer-0B1B16?style=for-the-badge&labelColor=0B1B16&color=073B2A">
<img src="https://img.shields.io/badge/Backend-Architecture-0B1B16?style=for-the-badge&labelColor=0B1B16&color=0E5A46">
<img src="https://img.shields.io/badge/AI%20Tooling-Infra-0B1B16?style=for-the-badge&labelColor=0B1B16&color=157A5F">

**I design and ship production systems** — typed APIs, resilient services, and clean developer workflows.  
_Principles: correctness ➝ observability ➝ performance ➝ ergonomics._

</div>

---

## 🧭 About
I’m a builder focused on **high-signal engineering**: small surfaces, strong invariants, and measurable outcomes.  
Recent interests: **agentic backends**, **multi-tenant SaaS**, **real-time event pipelines**, **perf-minded UI**.

- 🔭 **Now:** event-driven SaaS primitives (auth, orgs/roles, usage metering, billing, audit trails)
- 🧪 **Approach:** RFC ➝ ADR ➝ reference impl ➝ benchmarks ➝ docs
- 🧱 **Non-negotiables:** typed boundaries, idempotent ops, tracing first, zero-downtime deploys

---

## 🧰 Toolbox
<div align="center">

| Languages | Backend & RPC | Frontend | Data & Infra | DevX & QA |
|---|---|---|---|---|
| TypeScript, Python, Go, C++ | Node/Fastify, tRPC, gRPC, REST | React/Next.js, Tailwind, Radix UI | Postgres, Prisma, Redis, ClickHouse, Kafka | GitHub Actions, Docker, Vercel, AWS, pnpm, Vitest/Playwright |
| Patterns: DDD, CQRS (when needed), Outbox, Saga | AuthZ: RBAC/ABAC, JWT + PASETO | State: Zustand/Server Actions | Caching: layered (app + CDN + DB) | Observability: OpenTelemetry, Prometheus, Grafana |

</div>

---

## 🧩 Selected Engineering Work
> Swap links to public repos when ready.

- **Webzy** — agent platform + actions runtime, multi-tenant, usage-metered  
  _Next.js • tRPC • Prisma • Postgres • Redis • OTel tracing • GitHub Actions_
- **Ludus Works** — real-time ops for games/CRM; websockets, job queues, audit trails  
  _Fastify • BullMQ • Redis Streams • ClickHouse analytics_
- **Primal Tour** — evented pot logic + anti-cheat hooks, black-chrome UI kit  
  _Design system • rate-limited APIs • deterministic simulations_

---

## 🧪 Example: Service Contract (tiny slice)
```ts
// src/contracts/invoices.ts
import { z } from "zod";

export const InvoiceId = z.string().uuid();
export const CreateInvoiceInput = z.object({
  orgId: z.string().uuid(),
  amountCents: z.number().int().positive(),
  currency: z.enum(["USD","EUR","AED"]),
  memo: z.string().max(140).optional(),
});

export type CreateInvoiceInput = z.infer<typeof CreateInvoiceInput>;

export const createInvoice = procedure
  .input(CreateInvoiceInput)
  .mutation(async ({ input, ctx }) => {
    // idempotent by requestId
    await ctx.db.$transaction(async (tx) => {
      await tx.invoice.create({ data: { ...input }});
      await tx.outbox.create({ data: { type: "invoice.created", payload: input }});
    });
    return { ok: true };
  });

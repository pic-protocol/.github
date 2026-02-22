# PIC Model

> **Attribution Notice**  
> The **Provenance Identity Continuity (PIC) Model** is a theoretical framework  
> created by **Nicola Gallo**.  
>  
> The **PIC Specification** and all related official documents are published,  
> maintained, and governed by **Nitro Agility S.r.l.** as the Specification Steward.

The PIC Model organization is an effort to define and implement  
**PIC (Provenance Identity Continuity)** for distributed execution systems.

PIC is a formal execution model that prevents confused-deputy failures by
making **authority a property of execution continuity**, not of possessed
artifacts.

[PIC Website](https://www.pic-protocol.org) | [PIC Specification](https://github.com/pic-model/pic-spec)

---

## Why PIC?

🧠 **PIC is a guardrail for distributed execution — including AI systems.**  
Here's a simple example 👇

---

### Cache with Proof-of-Possession (PoP)

Cache key = URL  

```
/report → HTML

```

1. Admin hits first → admin page cached  
2. Next user → receives admin page  

✅ Works  
❌ Secure? No → **Confused deputy**

---

### Cache with PIC

Cache key =:

```
(URL, hash(authority-continuity))

```

- User ≠ Admin authority  
- Different continuity → different cache entry  

A request can only reuse results derived from **its own execution continuity**.

No token parsing.  
No role checks.  
No edge-side policy guessing.

---

### Why it works

🔐 **Authority is enforced by continuity, not possession.**

📉 **Monotonicity**  
Reuse is allowed only if:

```
ops₁ ⊆ ops₀

```

Never by authority expansion.

🚫 **PoP is the root cause**  
OAuth tokens, sealed credentials, capability replay →  
the deputy is structurally unavoidable.

The same applies to AI "guardrails" built on possession or role prompts.

---

### Change the ontology

Change what authority *is* →  
you change the gravity of distributed systems.

**PIC.**

---

## Specification and Protocols

- The **PIC Model** defines the core execution invariants.
- The **PIC Spec** defines the normative semantics.
- **PIC Protocol** documents (when published) define concrete protocol
  encodings and interoperability profiles.

Authorship, attribution, and normative authority are defined in the
official PIC Specification (Appendix B).

---

## License

Content is published under  
**Creative Commons Attribution 4.0 International (CC BY 4.0)**.

---

## Organization

This GitHub organization is operated by **Nitro Agility S.r.l.**

For governance, attribution, and legal context, see the 
[PIC Specification](https://github.com/pic-protocol/pic-spec).

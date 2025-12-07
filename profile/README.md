# PIC Model

The PIC Model organization is an effort to define and implement PIC (Provenance Identity Continuity) for distributed execution systems.

## Adopters

The following organizations and products are adopting or experimenting with
the PIC Model.

| Organization / Product          | Link                          |
|---------------------------------|-------------------------------|
| Nitro Agility                   | https://www.nitroagility.com  |
| Permguard                       | https://www.permguard.com     |
| Amla Labs                       | https://amlalabs.com/         |

## Why PIC?


🧠 **PIC is the only real guardrail for AI.**  
One simple example 👇

🗂 **Cache with Proof-of-Possession (PoP)**  
Cache key = URL  

`/report → HTML`

Admin hits first → admin page cached  
Next user → gets admin page  

✅ Works  
❌ Secure? No. **Confused deputy.**

🔗 **Cache with PIC**  
Cache key = `(URL, hash(authority-continuity))`

- user ≠ admin authority  
- different continuity → different cache entry  

A request can only reuse results derived from its **own execution continuity**.  
No token parsing. No role checks. No edge policies.

🔐 **Why it works**  
Authority is enforced by **continuity**, not by PoP.

📉 **Monotonicity**  
Reuse only if authority shrinks `(ops₁ ⊆ ops₀)`.  
Never by expansion.

🚫 **PoP is the problem**  
OAuth, sealed tokens, capabilities → the deputy is unavoidable.  
Same for AI guardrails built on possession.

---

Change the ontology → new gravity for distributed systems.  
**PIC.**

<div align="center">

# ⚗️ EbonHold Labs

<img src="https://img.shields.io/badge/site-nextaction.guide-3fbf4a?style=flat-square" alt=""> <img src="https://img.shields.io/badge/discord-the_EbonHold-6a5acd?style=flat-square" alt=""> <img src="https://img.shields.io/badge/store-nag.tebex.io-8fce00?style=flat-square" alt="">

**We make [NextActionGuide](https://nextaction.guide)** — a World of Warcraft addon that
tells you what to press next, on every flavor from Vanilla to Mists.

*"Good news, everyone! The slime is flowing again!"*

**[@Rakizi](https://github.com/Rakizi)** &nbsp;·&nbsp; **[@afonsohfontes](https://github.com/afonsohfontes)** &nbsp;·&nbsp; **[@Smufrik](https://github.com/Smufrik)**

</div>

---

## How it actually works

The addon doesn't decide what to recommend. It *reads* what to recommend, from
tables generated out of real game data — so a rotation change is a data change,
not a code change.

```mermaid
flowchart LR
  subgraph SRC["📚 reference data"]
    DBC["game DBC dumps<br/><i>spells · items · effects</i>"]
    SIM["sim projects<br/><i>vendored, read-only</i>"]
  end

  subgraph GEN["🐍 NextActionGuide-Tools"]
    G["generators<br/><i>python</i>"]
    V["gates<br/><i>every table checked<br/>before it ships</i>"]
    G --> V
  end

  subgraph ADDON["🎮 NextActionGuide"]
    T["generated tables<br/><i>lua</i>"]
    E["the engine<br/><i>reads a rotation,<br/>picks the next action</i>"]
    T --> E
  end

  P(["🧙 you, mid-pull"])

  DBC --> G
  SIM --> G
  V ==>|generated lua| T
  E ==>|next action| P

  classDef src fill:#241a2e,stroke:#8a5acd,color:#e0d0f2
  classDef gen fill:#0f2b1a,stroke:#3fbf4a,color:#c8f2d0
  classDef add fill:#1a2e12,stroke:#76b041,color:#d8f0c0
  classDef ply fill:#2e2410,stroke:#cd9a5a,color:#f2e4c0
  class DBC,SIM src
  class G,V gen
  class T,E add
  class P ply
```

⭐ **Everything downstream of a generator is disposable.** If a table is wrong we fix
the generator and regenerate — we don't hand-patch the output. That one rule is why
seven game flavors stay in step instead of drifting apart.

---

## The repos

| repo | what it is |
|---|---|
| **NextActionGuide** | the addon — Lua, ships to players |
| **NextActionGuide-Tools** | the generators, the services, the gates — Python |
| **extern-deps** | a manifest of the sim projects we read from. Vendored, never patched |
| **NAG-pub** | the public-facing slice |

## Where to find us

| | |
|---|---|
| 🌐 Site | [nextaction.guide](https://nextaction.guide) |
| 💬 Discord | [discord.gg/ebonhold](https://discord.gg/ebonhold) |
| 🛒 Store | [nag.tebex.io](https://nag.tebex.io) |
| 🐛 Found a bug? | [Rakizi/NAG-issues](https://github.com/Rakizi/NAG-issues) |

---

<div align="center">
<i>Three people, a pile of spell data, and a rule that a check which cannot fail isn't a check.</i>
</div>

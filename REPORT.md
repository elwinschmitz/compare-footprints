# Report: Carbon & Energy Footprint of Everyday, Food and Digital Activities

> _An order-of-magnitude comparison_
> Compiled: _12 November 2026_
> **How to read this:** every number is a **central estimate with a low–high range**. Only differences of about **×10 or more** are meaningful. Differences of ×2 are within the uncertainty.

---

## 1. Summary table (D2)

Sorted by central CO₂e per functional unit, highest first. "🤖-equiv." = CO₂e ÷ one simple chat query (0.12 g).

| Item | Functional unit | CO₂e central | CO₂e range | Final energy | Primary energy | Order of magnitude (g / Wh primary) | 🤖-equiv. | Conf. |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ⛽️🚗 Petrol car | 1 car, ~1,000 km AMS→GVA, 1 occupant | **170 kg** | 130–210 kg | 620 kWh | 740 kWh | 10⁵ / 10⁶ | ~1,400,000 | H |
| ✈️ Flight | 1 pax, AMS→GVA one way (incl. RF) | **110 kg** (60 kg excl. RF) | 70–150 kg | 230 kWh | 280 kWh | 10⁵ / 10⁵ | ~900,000 | H |
| 🔋🚙 EV | 1 car, ~1,000 km, NL grid | **54 kg** | 45–70 kg | 180 kWh | 340 kWh | 10⁴ / 10⁵ | ~450,000 | H |
| 🍔 Beef burger | 1 burger (113 g patty + bun) | **7 kg** | 4–12 kg | — | 1.5 kWh (CED) | 10⁴ / 10³ | ~58,000 | M |
| 🍗 Chicken | 1 portion (150 g) | **1.5 kg** | 0.9–2.2 kg | — | 1.0 kWh (CED) | 10³ / 10³ | ~12,500 | M |
| 🧀 Cheese | 1 portion (50 g) | **1.2 kg** | 0.5–1.5 kg | — | 0.7 kWh (CED) | 10³ / 10³ | ~10,000 | M |
| 🦾🦾 Agent task, large | ~1 h, 100+ tool calls, ~10 M tokens | **210 g** | 70–600 g | 545 Wh | 1,040 Wh | 10² / 10³ | ~1,750 | L |
| 📦 Parcel, next-day | 1 parcel, NL, ~150 km | **150 g** | 80–350 g | 780 Wh | 1,000 Wh | 10² / 10³ | ~1,250 | M |
| 🧑‍🧑‍🧒‍🧒 Teams + recording | 1 meeting-hour, 4 people, recording kept 1 yr | **60 g** (≈15 g/person) | 40–400 g | 200 Wh | 380 Wh | 10¹–10² / 10² | ~500 | L |
| 📺 Video streaming | 1 hour, HD | **50 g** | 20–100 g | 100 Wh | 190 Wh | 10¹ / 10² | ~420 | M |
| 🦾 Agent task, medium | ~10 min, ~20 tool calls, ~600k tokens | **18 g** | 6–50 g | 48 Wh | 90 Wh | 10¹ / 10² | ~150 | L |
| 🧑‍💻 Computer work | 1 hour, laptop + monitor | **14 g** | 8–27 g | 45 Wh | 86 Wh | 10¹ / 10² | ~115 | H |
| 🎧 Music streaming | 1 hour, smartphone | **1.5 g** | 0.5–8 g | 5 Wh | 10 Wh | 10⁰ / 10¹ | ~12 | L |
| 🗄️ GitHub Actions CI | 5 min, Linux runner, CPU only | **0.6 g** | 0.2–1.6 g | 1.5 Wh | 2.9 Wh | 10⁰ / 10⁰ | ~5 | M |
| 🔍 Google search | 1 query, no AI | **0.2 g** | 0.05–0.5 g | 0.3 Wh | 0.6 Wh | 10⁻¹ / 10⁰ | ~2 | L (2009 data) |
| 🤖 Chat query | 1 short prompt + answer | **0.12 g** | 0.03–0.4 g | 0.3 Wh | 0.6 Wh | 10⁻¹ / 10⁰ | 1 | M |

### *Key assumptions (one line each)
- **Grid:** NL 300 g CO₂e/kWh for home, office, EV and warehouses; data centres 400 g CO₂e/kWh (global average, location-based).
- **Primary energy:** electricity × 1.9; fuels × 1.2 (well-to-tank uplift). Food energy is cumulative energy demand (CED), which is already primary.
- **Flight:** non-CO₂ effects (radiative forcing, RF) are included in the table (DESNZ method, ~1.9×); the value without RF is in brackets.

### Key takeaways
1. **Transport and beef dominate everything.** One one-way flight to Geneva ≈ **500 large agent sessions** ≈ **16 burgers**. Driving alone in a petrol car is worse than flying for this trip, while an EV is about 3× better than either.
2. **One burger ≈ 35 large agent tasks ≈ 400 medium agent tasks ≈ 140 hours of video.**
3. **A single chat query is tiny** (≈ a Google search). **Agent tasks are a different category**: a medium task ≈ 150 chat queries, and a large one ≈ 1,750. In energy, a large agent session ≈ a next-day parcel delivery.
4. **A medium agent task ≈ one hour of working on your own laptop.** A large one ≈ 15 hours of laptop work.
5. **Food: energy and CO₂e are only loosely related.** A burger takes only ~1.5 kWh of production energy, the same as ~1.5 large agent tasks, yet it emits ~35× more CO₂e. That is because most food emissions are methane (cattle) and nitrous oxide (fertiliser and manure), not energy use.

---

## 2. Global parameters & assumptions register (D5)

| # | Parameter | Value used | Source / note |
| --- | --- | --- | --- |
| G1 | NL grid intensity | **300 g CO₂e/kWh** (range 260–390) | Electricity Maps 2025 yearly average 262 g CO₂eq/kWh; Nowtricity 2025 388 g. Rounded midpoint |
| G2 | Data-centre grid intensity | **400 g CO₂e/kWh** (range 100–500) | IEA: global 445 g/kWh (2024) → ~400 (2027). Company renewable-energy claims (market-based) are not used |
| G3 | Low / high grid sensitivity | 50 / 700 g/kWh | Brief §2.4 |
| G4 | PUE | Included in per-token figures; 1.185 for CI | Cloud Carbon Footprint (CCF) Azure coefficient |
| G5 | Primary-energy factor (electricity) | 1.9 | EU Energy Efficiency Directive (2023 recast) default; not re-verified this session |
| G6 | Well-to-tank uplift (fuels) | +20% | JEC / DESNZ WTT order of magnitude; not re-verified |
| G7 | RF multiplier (flights) | ~1.9 | DESNZ/DEFRA conversion-factor methodology |
| G8 | Fuel heating values | Petrol 8.9 kWh/L, diesel 10 kWh/L, kerosene 12 kWh/kg | Standard lower heating values |
| G9 | Food CO₂e statistic | **OWID means** (not medians) | **Deviation from the brief:** the median values could not be retrieved reliably in this session, so ranges span dairy-herd ↔ beef-herd beef |
| G10 | User device time for 🤖/🔍 | Excluded | A laptop running 30 s (≈0.4 Wh) would be **larger** than the query itself; noted as a caveat |
| G11 | Embodied emissions (devices, vehicles, servers, buildings) | Excluded | Qualitative caveat only |

---

## 3. Research dossier (D1)

### ✈️ Flight Amsterdam → Geneva
- **Functional unit:** 1 economy passenger, one way. Great-circle distance ≈ 685 km, ×1.08 path uplift ≈ 740 km.
- **Boundary:** operational (fuel burn); CO₂e with and without RF.
- **Sources:** DESNZ/DEFRA GHG Conversion Factors (short-haul economy ≈ 0.08 kg CO₂/pkm without RF, ≈ 0.15 with RF); ICAO Carbon Emissions Calculator (cross-check).
- **Calculation:** 740 × 0.08 ≈ **60 kg** without RF; ×~1.9 ≈ **110 kg** with RF. Fuel ≈ 60 / 3.16 kg CO₂ per kg fuel ≈ 19 kg kerosene × 12 kWh/kg ≈ **230 kWh**.
- **Result:** 110 kg CO₂e (70–150) | 230 kWh = 830 MJ | primary 280 kWh. **Per km:** ~150 g CO₂e/pkm, ~310 Wh/pkm.
- **Confidence:** High.
- **Caveats:** the RF multiplier is scientifically debated (×1.7–3). Load factor and aircraft type matter ±30%.

### ⛽️🚗 Petrol car
- **Functional unit:** 1 car, ~1,000 km by road, 1 occupant.
- **Sources:** EEA real-world fuel-consumption monitoring (~6.5–7.5 L/100 km for EU petrol cars); DESNZ. Thuiswinkel.org cites **204 g CO₂/km** for an average petrol car (likely including well-to-tank).
- **Calculation:** 7 L/100 km × 1,000 km = 70 L. × 2.3 kg CO₂/L (tank-to-wheel) ≈ **160–170 kg**. 70 L × 8.9 kWh/L ≈ **620 kWh**.
- **Result:** 170 kg (130–210) | 620 kWh = 2.2 GJ | primary 740 kWh. **Per km:** ~170 g/km, ~620 Wh/km. With **4 occupants:** ~43 kg per person.
- **Confidence:** High.

### 🔋🚙 Electric car
- **Assumption:** 18 kWh/100 km at the plug, including charging losses (ICCT/EEA real-world order of magnitude).
- **Calculation:** 180 kWh × 300 g = **54 kg**. Sensitivity: 9 kg on a 50 g/kWh grid; 126 kg on a 700 g/kWh grid.
- **Result:** 54 kg (45–70) | 180 kWh = 650 MJ | primary 340 kWh. **Per km:** 54 g, 180 Wh.
- **Confidence:** High. **Caveat:** battery manufacturing (embodied) is excluded and would add roughly 10–20 g/km if amortised.

### 📦 Online order, next-day home delivery (NL)
- **Functional unit:** 1 parcel of ~1–2 kg, NL webshop → door, ~150 km.
- **Boundary:** operations of the delivery chain only. Product, packaging, ordering and returns are excluded.
- **Sources:**
  1. Thuiswinkel.org / research reported by Supply Chain Movement: home delivery averages **~100 g CO₂** per parcel; pick-up points are ~10% lower; emissions per parcel fell 56% in five years. Self-reported by the industry association; scope (last mile only or the whole chain) is unclear.
  2. TNO 2020 (Davydenko & Hopman): an illustrative last-mile round of 100 parcels over 90 km = 30 kg CO₂ → **300 g/parcel**. This is a worked example, not a measurement.
  3. HvA/TNO factsheet: the average NL **return rate is ~6%**, and returns have little transport impact.
- **Bottom-up build (GLEC-style), by leg:**

| Leg | Assumption | Final energy | CO₂e |
| --- | --- | --- | --- |
| Warehouse + sorting hubs | ~0.05 kWh/parcel, NL grid | 50 Wh | 15 g |
| Linehaul truck, 150 km | 33 L/100 km, ~2,000 parcels on board | 250 Wh | 60 g |
| Last-mile van | ~80 km round, ~130 parcels; 70% diesel (9.5 L/100 km) / 30% electric (20 kWh/100 km); +7% failed deliveries | 480 Wh | 125 g |
| **Total** | | **~780 Wh** | **~200 g** |

- **Result:** central **150 g** (80–350), the midpoint between the industry figure (100 g) and the bottom-up build (200 g) | 780 Wh = 2.8 MJ | primary ~1,000 Wh.
- **Where the emissions sit:** the **last mile is ~60%** of the total; the 150 km of linehaul is ~30%.
- **Sensitivity:** an all-electric last mile → ~90 g; a pick-up point → about −10% (more if the customer walks or cycles to collect it).
- **Confidence:** Medium.

### 🍔 Beef burger · 🍗 Chicken · 🧀 Cheese
- **Sources:**
  - **CO₂e:** Poore & Nemecek (2018), _Science_, via Our World in Data, in kg CO₂e per kg product: beef from beef herds ≈ 99.5, beef from dairy herds ≈ 33, cheese ≈ 23.9, poultry ≈ 9.9.
  - **Energy (CED):** de Vries & de Boer (2010), _Livestock Science_, review: beef ~35–55, chicken ~15–30 MJ/kg. Cheese is derived as about 10 kg of milk per kg of cheese, giving ~40–60 MJ/kg. Agribalyse is recommended as a cross-check.
- **Calculations:**

| Item | CO₂e | CED (energy) |
| --- | --- | --- |
| 🍔 113 g beef | 113 g × ~60 kg/kg (dairy–beef herd blend) ≈ 6.8 kg + bun/garnish 0.2 kg ≈ **7 kg**. Range 4 kg (dairy herd) to 12 kg (beef herd) | 45 MJ/kg × 0.113 ≈ 5.1 MJ + bun ≈ **1.5 kWh** (1–2.5) |
| 🍗 150 g chicken | 0.15 × 9.9 ≈ **1.5 kg** (0.9–2.2) | 25 MJ/kg × 0.15 ≈ 3.75 MJ ≈ **1.0 kWh** (0.6–1.5) |
| 🧀 50 g cheese | 0.05 × 23.9 ≈ **1.2 kg** (0.5–1.5; hard cheese at the high end) | 50 MJ/kg × 0.05 ≈ 2.5 MJ ≈ **0.7 kWh** (0.4–1.0) |

- **Insight:** the burger's CO₂e-to-energy ratio is ~4.7 kg CO₂e per kWh, ~15× that of grid electricity. The excess is methane and nitrous oxide, not energy use.
- **Confidence:** Medium for CO₂e (well established); Low–Medium for CED (older sources, different studies from the CO₂e figures).
- **Out of scope:** home cooking; food calories.

### 🔍 Google search (no AI)
- **Sources:** Google (2009): 0.0003 kWh = **0.3 Wh** and ~0.2 g CO₂ per search. No newer official figure was found.
- **Result:** 0.3 Wh | **0.2 g** (0.05–0.5).
- **Confidence:** Low, because the data is 17 years old. Efficiency gains suggest it is lower now, but AI Overviews push it higher.

### 📺 Video streaming, 1 hour
- **Sources:**
  - IEA (Kamiya, 2020): ~0.077 kWh per hour, ~36 g CO₂ per hour (2019, global).
  - Carbon Trust (2021): ~55 g CO₂e per hour (Europe); the viewing device dominates.
  - The Shift Project's 2019 estimate (~400 g/h) is widely regarded as far too high.
- **Result:** ~100 Wh (40–250, depending on TV vs. laptop) | **50 g** (20–100).
- **Confidence:** Medium.

### 🎧 Music streaming, 1 hour _(Derived)_
- **Calculation:** smartphone ~2 Wh + Wi-Fi router share ~2 Wh + network (~70 MB/h × 0.006–0.06 kWh/GB ≈ 0.4–4 Wh) + data centre (negligible) ≈ **5 Wh** (2–20). × NL grid ≈ **1.5 g** (0.5–8). Playing through a laptop and speakers is ~10× higher.
- **Confidence:** Low. No dedicated peer-reviewed per-hour figure was found this session.

### 🧑‍💻 Computer work, 1 hour
- **Calculation:** laptop ~20 W + 24″ monitor ~25 W (Energy Star order of magnitude) = **45 Wh** × 300 g = **14 g** (8–27).
- **Confidence:** High. **Caveat:** embodied emissions of the laptop typically exceed its lifetime use-phase emissions.

### 🧑‍🧑‍🧒‍🧒 Teams meeting + recording, 1 hour, 4 people _(Derived)_
- **Calculation:** 4 laptops ~100 Wh + routers ~24 Wh + network (~5 GB total at a power-model intensity) ~20–60 Wh + Microsoft servers ~10 Wh + recording (~0.5 GB, 3 replicas, 1 year) ~5 Wh ≈ **200 Wh** → **~60 g** (≈15 g per participant).
- **Comparison source:** Obringer et al. (2021), _Resources, Conservation & Recycling_: 150–1,000 g per hour. Their method uses average network intensities per GB, which explains why it sits at the high end. Range: 40–400 g.
- **Finding:** keeping the recording adds <5%; the cameras (data volume) and the devices dominate.
- **Confidence:** Low.

### 🤖 Simple chat query
- **Sources (four independent routes, all ≈ 0.3 Wh):**
  - Google (2025, arXiv 2508.15734): median Gemini text prompt **0.24 Wh**. Self-reported, but the method is published.
  - Epoch AI (2025): ~0.3 Wh (GPT-4o).
  - OpenAI CEO (2025): 0.34 Wh. No method given.
  - Jegham et al. (2025), "How Hungry is AI?": GPT-4o ~0.42 Wh; reasoning models such as o3 ~7 Wh and DeepSeek-R1 ~24 Wh per short prompt.
- **Result:** **0.3 Wh** (0.1–1) × 400 g = **0.12 g** (0.03–0.4). Google's market-based figure is ~0.03 g.
- **Confidence:** Medium. **Caveat:** reasoning or "thinking" modes are 10–70× higher.

### 🦾 Agent task, medium (~10 min, ~20 tool calls) _(Derived)_
- **Per-token energy** (tokenatlas methodology, mid estimates for Opus-class models, in Wh per 1k tokens): fresh input 0.39, output 1.4, cache read 0.015, cache write 0.49. The stated uncertainty is ÷3 to ×3. Sonnet-class ≈ 0.6×.
- **Token profile:** ~550k cache read, ~30k cache write, ~5k fresh input, ~10k output (≈600k tokens in total, ~20 model turns).
- **Calculation:**

| Token type | Tokens | Energy |
| --- | --- | --- |
| Cache read | 550k | 8 Wh |
| Cache write | 30k | 15 Wh |
| Fresh input | 5k | 2 Wh |
| Output | 10k | 14 Wh |
| **Server side** | | **≈ 40 Wh** |
| Laptop, 10 min | | 7.5 Wh |

- **Cross-check:** Simon Couch (Jan 2026) estimated **41 Wh** for his median Claude Code session (24 model calls, 592k tokens).
- **Result:** 48 Wh | 40 Wh × 400 g + 7.5 Wh × 300 g ≈ **18 g** (6–50).
- **Confidence:** Low. The method and the cross-check agree, but per-token energy is not disclosed by any lab.

### 🦾🦾 Agent task, large (~1 h, 100+ tool calls) _(Derived)_
- **Token profile:** ~9.5 M cache read, ~300k cache write, ~50k fresh input, ~100k output (~10 M tokens).
- **Calculation:**

| Token type | Tokens | Energy |
| --- | --- | --- |
| Cache read | 9.5 M | 143 Wh |
| Cache write | 300k | 147 Wh |
| Fresh input | 50k | 20 Wh |
| Output | 100k | 140 Wh |
| **Server side** | | **≈ 450–500 Wh** |
| Laptop, 1 h | | 45 Wh |

- **Cross-check:** Zeke Hausfather (2026) measured a median Claude Code session of **~600 Wh** (250–1,200), with 100+ calls and ~10 M tokens. Over 8 weeks his average was **~150 Wh per prompt, ≈600× a chat prompt**.
- **Result:** 545 Wh | ≈ **210 g** (70–600).
- **Confidence:** Low. **Caveat:** sub-agents or agent teams can multiply token use (Anthropic's documentation says agent teams use ~7× more tokens).

### 🗄️ GitHub Actions CI, 5 min _(Derived)_
- **Runner:** standard Linux runner, 4 vCPU / 16 GB RAM (public repositories; private runners are smaller). Not re-verified this session.
- **CCF Azure coefficients:** 0.78–3.76 W per vCPU, 0.392 W per GB of RAM, PUE 1.185.
- **Calculation:** 4 × (0.78 + 0.5 × 2.98) + 16 × 0.392 ≈ 15.4 W × 1.185 ≈ 18 W × 5/60 h ≈ **1.5 Wh** × 400 g ≈ **0.6 g** (0.2–1.6).
- **Confidence:** Medium. **Caveat:** CCF coefficients ignore VM provisioning and idle overhead, and runner hardware is embodied-heavy.

---

## 4. Bibliography (D4)
Accessed 2026-11-12 unless marked †. † = established source used from prior knowledge and **not re-fetched in this session**; verify before publishing.

- Ember (2026). The Netherlands country profile. <https://ember-energy.org/countries-and-regions/the-netherlands>
- Electricity Maps (2026). Electricity Grid Review 2025: Netherlands. <https://www.electricitymaps.com/grid-in-review-2025/the-netherlands>
- Nowtricity. CO₂ emissions per kWh in Netherlands. <https://www.nowtricity.com/country/netherlands>
- IEA (2025). Electricity 2025 – Emissions. <https://www.iea.org/reports/electricity-2025/emissions>
- Google / Elsworth et al. (2025). Measuring the environmental impact of delivering AI at Google scale. arXiv:2508.15734 (via Ritchie 2025)
- Ritchie, H. (2025). What's the carbon footprint of using ChatGPT or Gemini? [Aug 2025 update]. <https://hannahritchie.substack.com/p/ai-footprint-august-2025>
- EcoGPT (2026). How much energy does AI use? <https://ecogpt.com/blog/how-much-energy-does-ai-use> (pointer to primary sources)
- Devera (2026), summarising Jegham et al. (2025), arXiv:2505.09598. <https://devera.ai/resources/environmental-impact-ai-energy-carbon>
- Couch, S. P. (2026). Electricity use of AI coding agents. <https://simonpcouch.com/blog/2026-01-20-cc-impact>
- Hausfather, Z. (2026). The real energy use of agentic AI. <https://www.theclimatebrink.com/p/the-real-energy-use-of-agentic-ai>
- Gille, M. tokenatlas – energy estimation methodology. <https://github.com/Magnus-Gille/tokenatlas>
- Anthropic. Claude Code docs – Manage costs effectively. <https://code.claude.com/docs/en/costs>
- Supply Chain Movement. CO₂ emissions per parcel down 56% over last five years (Thuiswinkel.org). <https://www.supplychainmovement.com/co2-emissions-per-parcel-down-56-over-last-five-years>
- Davydenko & Hopman (2020). Effect of pick-up points and returns on CO₂ emissions in last mile parcel delivery networks. TNO 2020 R10909. <https://topsectorlogistiek.nl/wp-content/uploads/2020/09/TNO-2020-R10909.pdf>
- Ploos van Amstel, Weltevreden, Quak & Hopman (2021). Bezorgeconomie (factsheet). <https://www.retailinsiders.nl/docs/f3c568d7-7545-4891-8ec8-4862933262a1.pdf>
- † Poore, J. & Nemecek, T. (2018). Reducing food's environmental impacts through producers and consumers. _Science_ 360:987. Data via Our World in Data.
- † de Vries, M. & de Boer, I. J. M. (2010). Comparing environmental impacts for livestock products. _Livestock Science_ 128:1–11.
- † UK DESNZ (2024/2025). Greenhouse gas reporting: conversion factors.
- † EEA. Monitoring of CO₂ emissions from passenger cars (real-world data).
- † IEA / Kamiya, G. (2020). The carbon footprint of streaming video: fact-checking the headlines.
- † Carbon Trust (2021). Carbon impact of video streaming.
- † Obringer, R. et al. (2021). The overlooked environmental footprint of increasing Internet use. _Resources, Conservation & Recycling_ 167.
- † Google (2009). Powering a Google search (official blog).
- † Cloud Carbon Footprint – methodology & coefficients. <https://www.cloudcarbonfootprint.org>

---

## 5. CSV (D2, machine-readable)

```csv
item,functional_unit,co2e_g_central,co2e_g_low,co2e_g_high,final_energy_Wh,primary_energy_Wh,energy_basis,confidence
petrol_car,"1 car ~1000 km 1 occupant",170000,130000,210000,620000,744000,final,H
flight,"1 pax AMS-GVA one way incl RF",110000,70000,150000,230000,276000,final,H
ev_car,"1 car ~1000 km NL grid",54000,45000,70000,180000,342000,final,H
beef_burger,"1 burger 113 g patty",7000,4000,12000,,1500,primary_CED,M
chicken,"1 portion 150 g",1500,900,2200,,1000,primary_CED,M
cheese,"1 portion 50 g",1200,500,1500,,700,primary_CED,M
agent_large,"~1 h 100+ tool calls",210,70,600,545,1036,final,L
parcel_nextday,"1 parcel NL ~150 km",150,80,350,780,1000,final,M
teams_meeting,"1 h 4 people + recording",60,40,400,200,380,final,L
video_stream,"1 h HD",50,20,100,100,190,final,M
agent_medium,"~10 min ~20 tool calls",18,6,50,48,90,final,L
computer_work,"1 h laptop+monitor",14,8,27,45,86,final,H
music_stream,"1 h smartphone",1.5,0.5,8,5,9.5,final,L
ci_run,"5 min Linux runner",0.6,0.2,1.6,1.5,2.9,final,M
google_search,"1 query",0.2,0.05,0.5,0.3,0.57,final,L
chat_query,"1 short prompt",0.12,0.03,0.4,0.3,0.57,final,M
```

---

## 6. Footnote: footprint of producing this report (D6)

_Self-estimate using the same method as 🦾/🦾🦾. The token counts are **estimates**: the assistant has no access to its own usage metadata.*

| Component | Basis | Energy |
| --- | --- | --- |
| Planning turns (3 earlier briefs) | ~30k input + ~20k output tokens | ~40 Wh |
| This research turn | 6 web searches; ~4 model calls; ~180k input tokens (large search results) + ~15k output | ~90 Wh |
| Web searches | 6 × 🔍 | ~2 Wh |
| Human briefing + review | ~30 min × 🧑‍💻 | ~22 Wh |
| **Total** | | **≈ 150 Wh** (50–450) |

**CO₂e: ≈ 60 g** (20–180). That is about one Teams meeting, ~300 Google searches, or **~1% of one burger**.

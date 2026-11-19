# Materiality of a Prompt — Data sources

Decision (17 Nov 2026): the route is shown **schematically**, in three levels. Each level has its own data source.

## Data certainty — visual legend
Every line, node and number in the piece gets one of three states (design: Jasmin, 17 Nov 2026). The current visual form is in `visual-legend.md`.

| State | Meaning |
|---|---|
| **Certain** | Published or measured by the company or an official source |
| **Uncertain** | Independent estimate, or a dataset tag of #likely / #speculative |
| **NoData** | Nothing public — the gap itself is shown |

### Classification so far
| Item | Euria (Infomaniak) | Lumo (Proton) | Gemini (Google) | Claude (Anthropic) |
|---|---|---|---|---|
| Data center location | Certain (Plan-les-Ouates GE; address not public) | Uncertain (Germany, city not public) | NoData (which site serves a Swiss user) | Uncertain (US sites; tagged confident / likely / speculative) |
| Data center power, chips | Chips Certain (L4/A100/H100, DCD); power NoData (1.25 MW only on Datacenter Map, not published by Infomaniak) | NoData | Uncertain per site (Epoch AI = independent estimates); PUE per site Certain (Google) | Uncertain per site (Epoch AI = independent estimates), use by Anthropic varies |
| Energy per prompt | NoData | NoData | Certain (0.24 Wh, Google, May 2025 data, not independently verified) | Uncertain (independent estimates only) |
| Water per prompt | Certain-ish: no water used for cooling (company claim) | NoData | Certain (0.26 mL, Google) | NoData |
| Route land segments | Certain (schematic) | Uncertain | Uncertain | Uncertain |
| Route sea segment | — | — | Uncertain (if US) | Uncertain (schematic cable) |

## Energy per prompt (researched 17 Nov 2026)
- **Gemini (Google)** — published Aug 2025: median Gemini Apps text prompt = **0.24 Wh**, **0.03 gCO2e**, **0.26 mL** water. Includes accelerators, host CPU/RAM, idle machines, data center overhead. Excludes network, end-user device and **training**. Narrow method (accelerators only): 0.10 Wh. → **Certain** (company-measured, but only one company's method).
- **ChatGPT (OpenAI)** — for reference: Sam Altman blog, June 2025, ~0.34 Wh per average query. No technical report.
- **Claude (Anthropic)** — no official figure; Anthropic has published no per-prompt or emissions data. Its IPO filing (S-1, 26 Oct 2026) confirms the contract for all of Colossus 1 (>300 MW, >220,000 GPUs) and plans for data centres with on-site gas generation, but gives no per-prompt figures. Independent estimates: CLEER method by the Sustainable AI Group (29 Sep 2026), applied by Projet Celsius (2 Nov 2026, updated 12 Nov 2026), assuming a typical US data centre: 0.08 Wh (Haiku 4.5) to 2.8 Wh (Fable 5, extrapolated) per conversation. **On the website: Sonnet 5 ≈ 0.83 Wh per conversation.** Simple question: Sonnet 5 ≈ 0.24 Wh, Opus 5 ≈ 0.46 Wh. The 5.5 models are not estimated yet. Agentic use (Claude Code) much higher: Hausfather 2026 ≈ 150 Wh per human prompt. → **Uncertain**.
- **Euria (Infomaniak)** — no per-prompt figure. Possible estimate from model size + D4 data. → **NoData** (or Uncertain if we estimate).
- **Lumo (Proton)** — no figure. → **NoData**.

## Material per km of cable (researched 17 Nov 2026)
Mass per km of route, by cable type. Source = manufacturer datasheets / EPDs; material splits partly derived from cable geometry × material density (marked Uncertain). Excludes trench, concrete conduits, manholes, splice closures, amplifiers/repeaters.

| Type | Where on the route | Total kg/km | Material (kg/km) | State |
|---|---|---|---|---|
| **Fiber, underground in duct** (backbone, 144 fibers) | Exchange → exchange, land; also antenna site → exchange | **≈ 485** (cable ≈ 110 + HDPE duct 40 mm ≈ 375) | HDPE duct 375 · HDPE sheath 40–50 · PBT tubes 15–25 · GRP rod ≈ 12 · yarns/tape/gel 15–25 · optical fiber ≈ 10 (of which glass 3.9, acrylate 5.8) | Cable weight + duct: Certain (datasheets). Split: Uncertain (derived). Number of ducts per trench: NoData |
| **Fiber, armoured / direct buried** | Land, without duct | ≈ 184 | as above + corrugated steel tape (≈ 70 by difference) | Uncertain |
| **Fiber, aerial ADSS** | On poles / pylons | ≈ 85–260 (typ. ~150) | HDPE sheath, aramid yarns, GRP, optical fiber | Certain (weights), split Uncertain |
| **Fiber in power-line ground wire (OPGW)** | On high-voltage lines (e.g. Swissgrid) | 850 | steel 604 · aluminium 217 · PBT 14.5 · gel 6.8 · optical fiber 3.4 | Certain (EPD, CUNEXT OPGW). Exists in CH: BGer 1C_417/2017 — Lachmatt–Gösgen line (220/380 kV), fibre in the ground wire fitted in 1994 by ATEL, owned by Swissgrid since 2013; Swissgrid stated it has been rented out since Dec 1997 (the court did not establish whether this still runs). Which Swiss lines carry fiber: NoData. Allocation telecom vs. power grid: Uncertain |
| **Copper twisted pair** | Last mile (local exchange → home), where still copper | 3.5 kg copper per pair per km at 0.5 mm. Swisscom diameters 0.4 / 0.5 / 0.6 / 0.8 / 1.0 mm → 2.3 / 3.5 / 5.1 / 9.0 / 14.1 kg/km per pair; one line can mix diameters. Whole 2-pair cable ≈ 40 kg/km (Cu 7.0 + PE) | copper, PE insulation/sheath | Per diameter: Certain (geometry). Share of each diameter in CH: NoData → average 0.5 mm Uncertain (cross-check BT: 390,000 t / 121 M pair-km ≈ 3.2 kg/km) |
| **Submarine fiber** | Sea segment (Claude, maybe Gemini) | 650 (deep sea, light) – 1,100–1,700 (single armoured, shallow) | galvanized steel armour, stainless steel tube, HDPE, bitumen, optional copper | Weights Certain (datasheets); mix along a real route Uncertain; repeaters NoData |

Key observation: of ≈ 485 kg per km of underground route, the glass that carries the light is ≈ 4 kg (< 1 %). ~85–90 % is polyethylene (duct + sheath).

Notes:
- A 144-fiber cable is shared: one connection uses one fiber pair (≈ 0.05 kg glass per km). Decide whether to attribute the whole cable or a share per prompt.
- Thin copper (0.4–0.5 mm) is typical in the distribution network near homes, thicker (0.6–0.9 mm) for long-distance lines.
- Swisscom has already replaced copper with fiber between exchanges and distribution points; copper only remains on the last stretch to the home.

## Mobile network (researched 17 Nov 2026)
Only relevant if the user connects via mobile; with fiber/copper at home (BAKOM atlas) there is no antenna in the path.

### How the route works
1. **Phone → nearest antenna, by radio.** The only radio hop. City: a few hundred metres; rural: a few km. Antennas do **not** relay data to each other.
2. **Antenna site → exchange, usually fiber in the ground.** Swisscom: connection is "in der Regel" by fiber; every new site needs a fiber connection. Exception (mountains, remote): microwave link (dish antenna) to another site with fiber. Which site uses which: **NoData**.
3. **From the exchange:** same route as fixed network (backbone → Internet Exchange → data center).
- Return path comes back through the same antenna → **distance ×2, antenna material ×1**.
- In the piece: location → nearest antenna (BAKOM map of transmitter sites, map.geo.admin.ch) → fiber to exchange → rest of the route.

### A Swisscom site
- Typical site: **3 directions** (e.g. azimuth +40° / +180° / +300°) × **2–3 frequency bands** (700–900, 1400/1800–2600, 3600 MHz) = **6–9 antennas** (building-permit site data sheets, St. Gallen and Baden). Swisscom's radio equipment vendor: Ericsson.
- A prompt uses **one direction (sector)** ≈ ⅓ of the site → ≈ 1–3 antennas of 12–57 kg + share of mast.

| Part | Weight | Material | State |
|---|---|---|---|
| **Panel antenna** (4G/5G bands < 2.6 GHz) | 15–57 kg each | aluminium reflector, fiberglass radome, PCB or tin-plated zinc radiators, brass/copper connectors | Weight Certain (datasheets) · split per material NoData |
| **5G active antenna** 3.6 GHz (e.g. Ericsson AIR 3268, 32 transceivers) | ≈ 12 kg | antenna + radio electronics in one housing: PCBs, chips, aluminium housing as heat sink | Weight Certain · material NoData |
| **Radio units + baseband** | ≈ 10–30 kg per unit | electronics, aluminium housings | Uncertain |
| **Brackets / clamps** | ≈ 5–7 kg per antenna | galvanized steel | Certain (datasheets) |
| **Mast** | rooftop mast ≈ 100 kg … lattice tower several tonnes | steel; concrete foundation if free-standing | NoData |
| **Backup batteries** | — | lead or lithium | NoData |
| **Cable to the site** | ≈ 485 kg/km | see cable table (fiber in duct) | Uncertain (length) |

No manufacturer has published a teardown by material (UCLouvain base-station LCA has restricted access) → show the material split as **NoData**.

### Dense cities (Lausanne / Renens)
- Same large rooftop antennas as elsewhere — not smaller, but **more sites, closer together** (shorter radio hop).
- Plus **small cells** where many people gather: in manholes (Swisscom since 2015/16 with Ericsson and Kathrein; must withstand the weight of a 40-tonne truck, Swisscom press release 8 Oct 2015), on façades or street lamps. Bern: concession for up to 100 microcells in public space.
- Small cells do not replace macro antennas: Swisscom's simulation for St. Gallen city centre found a small-cell-only network would mean worse indoor coverage, more faults and much higher costs.
- For Renens: most likely a rooftop macro antenna a few hundred metres away. Number and weight of small cells in Lausanne: **NoData**.

## Route levels → data

| Level | Path segment | Source | Use | Access / license |
|---|---|---|---|---|
| 1 Local | User location → grid square → local exchange → provider backbone | **BAKOM Breitbandatlas** (map.geo.admin.ch) | Connection type and coverage at the user's location (fiber, copper, cable) | Swiss federal geodata, open |
| 1 Local (mobile) | User location → nearest antenna site | **BAKOM, transmitter sites** (map.geo.admin.ch) + building-permit site data sheets (Standortdatenblatt) | Antenna location, bands, directions | Swiss federal geodata, open |
| 2 Hub | Backbone → Internet Exchange (SwissIX Zurich, CIXP Geneva) | **PeeringDB** (peeringdb.com) + own traceroutes | Internet Exchange locations, which networks meet there | Free, open API |
| 2 Hub (reference) | International Internet Exchange nodes | **TeleGeography Internet Exchange Map** (internetexchangemap.com) | Visual reference for the international hub network | Credit TeleGeography, CC BY-SA 4.0 for references/screenshots; raw data needs a license |
| 3 International, land | Exchange → exchange over land | **ITU Broadband Maps** (bbmaps.itu.int) | Terrestrial fiber backbone as a reference for the schematic land links | Viewing free; export/license unclear |
| 3 International, sea | Landing point → landing point | **TeleGeography Submarine Cable Map** | Sea links, if a data center is overseas | Stylized data; credit TeleGeography, non-commercial |
| 4 Destination | Data center (Anthropic, Google) | **Epoch AI – AI data centers** (epoch.ai/data/ai-data-centers, Nov 2026) | Location (address), power (MW), chips (type + count, H100 equivalents), capital cost, water use, construction timeline | CC BY 4.0, credit Epoch AI |
| 4 Destination | Data center (Infomaniak, Proton) | Company publications + press (see below) | Location, power, cooling, GPUs | Cite each source |

## Epoch AI dataset — what's in it
- 96 large AI data centers (77 in the US, the nearest to Switzerland in the UK, Portugal, Norway, Sweden, Finland, Iceland). No Swiss sites.
- Anthropic: 8 sites, all in the US (Colossus 1, Colossus 2, Anthropic-Amazon New Carlisle IN, Lake Mariner NY, Madison Mega Site, Ridgeland, Berwick, Barber Lake). Users carry tags #confident / #likely / #speculative.
- All Epoch figures (power, chips, cost) are Epoch's own estimates (satellite images, permits) → **Uncertain** (EXT on the website). "Current power" = IT power; whole-site power is in the timelines.
- On the website: Colossus 1 (default), Colossus 2, New Carlisle, Lake Mariner.
- Mistral: EcoDataCenter 2, Borlänge (Sweden), owner and user Mistral AI #confident, 0 MW (not running yet).
- Google: many US sites; nearest European one: Google Waltham Cross (UK, TPU v6e).
- Infomaniak / Proton: not included → researched separately (below).
- 82 of 96 entries have an address. Water use only for some sites.
- Extra tables: chip types (power per chip, FLOP/s), chip quantities per site, chillers and cooling towers (sizes, capacity).
- Measures **capacity**, not use per prompt. No data on building materials.

## Infomaniak — Euria (researched 17 Nov 2026)
- AI assistant **Euria** (launched Dec 2025); all processing in Infomaniak's own data centers in Switzerland.
- Data center **D4**, underground in the La Bistoquette housing cooperative, **Plan-les-Ouates (Geneva)**; first servers Dec 2023, heat recovery since 11 Nov 2024, inaugurated 27 Jan 2025. Exact address not public.
- IT power: **not published by Infomaniak** (1.25 MW appears only on Datacenter Map; D4 ran at 25 % of capacity in Jan 2025). About **1.7 MW** heat at full capacity into Geneva's district heating (~6,000 homes); PUE 1.09 (DCD); no water used for cooling.
- GPUs: Nvidia **L4, A100, H100**. Built for ~10,000 servers on 1,800 m².
- Traceroutes from ÉCAL (Wi-Fi), home in Lausanne (Wi-Fi) and mobile all end at Infomaniak routers named "plo" (Plan-les-Ouates) — see Traceroutes below.

## Proton — Lumo (researched 17 Nov 2026)
- AI assistant **Lumo** (launched July 2025), runs on open-source models on Proton-owned servers.
- Lumo servers are in **Germany** (city not public; CEO Andy Yen to Keystone-SDA / swissinfo); Proton also builds facilities in **Norway**; CHF 100 million for Germany and Norway together. Reason given: planned Swiss surveillance law reform (VÜPF). Proton's own blog says only "European datacenters".
- No public figures on power or GPUs.

## Perplexity (researched 19 Nov 2026)
- No own data centres. AWS = "preferred cloud infrastructure provider" (spokesperson, DCD); Microsoft: 3-year, $750 million cloud agreement (Azure / Foundry); CoreWeave: dedicated Nvidia GB200 NVL72 clusters for inference (Mar 2026); Crusoe: multi-year partnership (Sep 2026).
- No regions or countries published. → data centre: **NoData**; shown on the website as possible AWS regions (Northern Virginia, Frankfurt).
- Energy, water, emissions per query: **nothing published** (Projet Celsius). The 0.5 Wh / 0.9 ml estimates (know-your-compute.pages.dev, no method) were removed from the website.

## Mistral — Vibe, formerly Le Chat (researched 19 Nov 2026)
- Le Chat renamed **Vibe** on 28 May 2026 (AI Now Summit). Default model since 22 May 2026: Mistral Medium 3.5; Vibe's pages do not name the model.
- Life-cycle analysis (22 Jul 2025, with Carbone 4 and ADEME, Mistral Large 2 as of Jan 2025): per 400-token answer 1.14 gCO2e, **45 mL water**, **0.16 mg Sb eq**. No energy figure, no location. → Certain for 2025 / Mistral Large 2, does not cover the current model.
- Data centres: **Bruyères-le-Châtel** (Essonne, run by Eclairion): 44 MW, 13,800 Nvidia GB300, training and inference, from end of June 2026 (Mistral, Mar 2026). **Les Ulis** (Essonne): 10 MW, inference only, due Q3 2026 (Mistral, AI Now Summit). **Borlänge** (Sweden): in Epoch AI, not running yet.
- Which site answers a prompt: NoData.

## Data centres outside Epoch AI — published facts (researched 19 Nov 2026)
| Site | Fact | Source |
|---|---|---|
| AWS US East (Northern Virginia) | PUE 1.15 (2023–25), WUE 0.06 L/kWh (2025), 996,204,576 L withdrawn 2025; 22 AWS sites in Loudoun County | AWS Virginia sustainability fact sheet |
| AWS Europe (Frankfurt) | PUE 1.24 (2025), WUE 0.17 L/kWh (2025), 416,264,483 L withdrawn in Germany 2025 | AWS Germany sustainability fact sheet |
| Google St. Ghislain / Eemshaven / Hamina | PUE Q2 2026: 1.08 / 1.07 / 1.09 | datacenters.google/efficiency |
| Google per-site water 2025 | only via third-party sites quoting Google's 2026 Environmental Report → not on the website until checked in Google's data tables | — |
| Power and chips of AWS and Google sites | not published → NoData | — |

## Traceroutes (17–18 Nov 2026, 12 runs)
| Connection | Network | Claude | Gemini | Perplexity | Euria | Mistral |
|---|---|---|---|---|---|---|
| ÉCAL Wi-Fi (10.192.232.1) | HES-SO → SWITCH: Yverdon (swiyv2) → Lausanne (swils1) | → CERN (swice1) → CIXP, Cloudflare | → Fribourg → Bern → Basel → Zurich (swiez2, swiix3) → Google | → same SWITCH path → Equinix ZH4, Cloudflare | → CIXP → Infomaniak CERN → bdb → plo | → CIXP, Cloudflare; then hidden |
| Home Wi-Fi, Lausanne (fritz.box) | Swisscom (138.187.x) → green.ch (146.228.x), no place names | SwissIX (Cloudflare) | Google directly | SwissIX (Cloudflare) | SwissIX at CERN → Infomaniak → plo | Cloudflare; hub not shown |
| Mobile hotspot (172.20.10.1) | **Sunrise** (sunrise.net) → Liberty Global (aorta.net) | Liberty Global → Anthropic IP; hub not shown | Sunrise Zurich (zur01) → Google | Liberty Global → Cloudflare | Hopus Geneva (gv1) → Infomaniak gv1 → plo | stops after Liberty Global |

Notes: claude.ai answers from 160.79.104.10, reached via Cloudflare. Mobile traces run over **Sunrise**, not Swisscom — the antenna data on the website (Swisscom building-permit sheets) describes a Swisscom site.

## Still missing
- Training share per prompt — training compute/energy of the models (e.g. Epoch AI "Notable AI Models").
- Material composition of chips, servers, cooling, data-centre buildings (LCA sources).
- Small cells in Lausanne: NoData.
- Open decision: attribute whole cable / whole antenna, or only the share used by one prompt?
- Open decision: add concrete cable conduits as an extra category?

## Sources / credits

### Route and data centers
- **Epoch AI**, "AI data centers", https://epoch.ai/data/ai-data-centers (November 2026). License: CC BY 4.0.
- **TeleGeography**, Submarine Cable Map, https://www.submarinecablemap.com. CC BY-SA 4.0 (references/screenshots).
- **TeleGeography**, Internet Exchange Map, https://www.internetexchangemap.com. CC BY-SA 4.0 (references/screenshots).
- **ITU**, Broadband Maps, https://bbmaps.itu.int/bbmaps
- **PeeringDB**, https://www.peeringdb.com
- **BAKOM / OFCOM**, Breitbandatlas and transmitter sites, https://map.geo.admin.ch
- **Infomaniak**, D4 inauguration (28 Jan 2025), https://news.infomaniak.com/en/infomaniak-inaugurates-a-revolutionary-data-center-that-recovers-100-of-its-energy-for-building-heating
- **Infomaniak**, Euria launch (Dec 2025), https://www.generation-nt.com/communiques-presse/infomaniak-launches-euria-free-and-sovereign-ai-that-respects-2067456
- **Datacenter Map**, Infomaniak D4, https://www.datacentermap.com/switzerland/geneva/infomaniak-d4/
- **DatacenterDynamics**, Infomaniak launches Geneva data center, https://datacenterdynamics.com/en/news/infomaniak-launches-geneva-data-center
- **The Energyst**, Large-scale heat recovery for Geneva data centre, https://theenergyst.com/large-scale-heat-recovery-for-geneva-data-centre/
- **D4 open-source documentation** (EPFL, IMD, UNIL / E4S), https://d4project.org
- **swissinfo**, Proton does not trust Switzerland to host its AI servers, https://www.swissinfo.ch/eng/ai-governance/proton-does-not-trust-switzerland-to-host-its-ai-servers/89727842
- **heise online**, Proton relocates parts of its infrastructure from Switzerland, https://heise.de/-10538664
- **Tom's Guide**, Proton refuses to be 'held hostage' by Swiss surveillance law, https://www.tomsguide.com/computing/vpns/proton-refuses-to-be-held-hostage-by-controversial-swiss-surveillance-law
- **Proton**, Introducing Lumo, https://proton.me/blog/lumo-ai

### IP address owners (traceroutes, 18 Nov 2026)
- **ipregistry.co**, AS3303 Swisscom (138.187.0.0/16 Swisscom-Infra), https://ipregistry.co/AS3303/193.134.33.0/24
- **nerd.liberouter.org**, 146.228.0.0/16 green.ch AG (CH-VIANETWORKS-BACKBONE), https://nerd.liberouter.org/nerd/ipblock/146.228.0.0%20-%20146.228.255.255

### Perplexity, Mistral, AWS, Google (added 19 Nov 2026)
- **DatacenterDynamics**, Perplexity signs $750m cloud agreement with Microsoft, https://www.datacenterdynamics.com/en/news/perplexity-signs-750m-cloud-agreement-with-microsoft/
- **Projet Celsius**, Perplexity profile, https://projetcelsius.com/en/ai/ranking/assistants/perplexity/
- **HPCwire**, Crusoe and Perplexity partnership (16 Sep 2026), https://www.hpcwire.com/aiwire/2026/09/16/crusoe-and-perplexity-announce-multi-year-partnership-across-full-model-lifecycle
- **Mistral AI**, AI Now Summit 2026, https://mistral.ai/news/ai-now-summit-2026
- **DatacenterDynamics**, Mistral AI raises $830m for data center in Paris, https://datacenterdynamics.com/en/news/mistral-ai-raises-830m-in-debt-financing-for-data-center-in-paris-france
- **Mistral AI**, Our contribution to a global environmental standard for AI (22 Jul 2025), https://mistral.ai/news/our-contribution-to-a-global-environmental-standard-for-ai
- **AWS**, Virginia sustainability fact sheet, https://sustainability.aboutamazon.com/aws-sustainability-fact-sheets/aws-fact-sheet-virginia.pdf
- **AWS**, Germany sustainability fact sheet, https://sustainability.aboutamazon.com/aws-sustainability-fact-sheets/aws-fact-sheet-germany.pdf
- **Google**, Power usage effectiveness per site, https://datacenters.google/efficiency/
- **Swisscom**, Swisscom rüstet ihr Mobilfunknetz für die Zukunft (8 Oct 2015), see Mobile network
- **Fortune**, Anthropic's S-1 (26 Oct 2026), https://fortune.com/2026/10/26/anthropics-s1-ipo-reveals-the-inner-workings-of-its-fast-evolving-compute-strategy/

### Energy per prompt
- **Google Cloud**, Measuring the environmental impact of AI inference (Aug 2025), https://cloud.google.com/blog/products/infrastructure/measuring-the-environmental-impact-of-ai-inference
- **Google**, Measuring the environmental impact of delivering AI at Google scale (paper), https://arxiv.org/abs/2508.15734
- **DatacenterDynamics**, Google: median Gemini prompt uses 0.24 Wh, https://www.datacenterdynamics.com/en/news/google-median-gemini-prompt-uses-024-watt-hours-of-power-and-consumes-026ml-of-water/
- **Projet Celsius**, What is Claude's carbon footprint? (Nov 2026), https://projetcelsius.com/en/blog/claude-carbon-footprint/
- **tech-insider.org**, ChatGPT vs Gemini vs Claude energy use 2026, https://tech-insider.org/ie/chatgpt-vs-gemini-vs-claude-energy-use-2026/
- **Hausfather (2026)**, The real energy use of agentic AI, https://skepticalscience.com/print.php?n=6600

### Materials — fiber cables and ducts
- **CUNEXT / AENOR GlobalEPD**, OPGW-A003A-48A01D0 EPD (850 kg/km), https://www.aenor.com/documents/d/guest/globalepd-en15804-209-cunext-opgw-a003a-260119
- **Corning**, ALTOS 144ZR4-Y3F20DDE (62 kg/km), https://ecatalog.corning.com/optical-communications/EMEA/en_GB/Fibre-Optic-Cables/Outdoor/Outdoor-Duct-Cables/ALTOS%C2%AE-Loose-Tube%2C-Gel-Free%2C-All-Dielectric%2C-Non-Armoured-Cables-with-Binderless-FastAccess%E2%84%A2-Technology/p/144ZR4-Y3F20DDE
- **Corning**, ALTOS 144ZP4-T3F20D20 (111 kg/km), https://ecatalog.corning.com/optical-communications/AU/en/Fiber-Optic-Cables/Outdoor/Outdoor-Duct-Cables/ALTOS%C2%AE-Loose-Tube%2C-Gel-Free%2C-All-Dielectric%2C-Non-Armored-Cables-with-Binderless-FastAccess%E2%84%A2-Technology/p/144ZP4-T3F20D20
- **Corning**, ALTOS 144EP4-T3122PDE (115 kg/km), https://ecatalog.corning.com/optical-communications/SEA/en/Fiber-Optic-Cables/Ext%C3%A9rieur/Outdoor-Duct-Cables/ALTOS%C2%AE-Loose-Tube-Outdoor-Duct-Cable-LT-2-0-HDPE/p/144EP4-T3122PDE
- **Corning**, ALTOS steel armour 144FPC-T3101P20 (184 kg/km), https://ecatalog.corning.com/optical-communications/AU/en/Fiber-Optic-Cables/Outdoor/Outdoor-Direct-Buried-Cables/ALTOS%C2%AE-Loose-Tube-Steel-Armor-Outdoor-Cable-LT-2-0-HDPE/p/144FPC-T3101P20
- **OFS**, Loose tube outdoor cable, standard duct (155 kg/km), https://fiber-optic-catalog.ofsoptics.com/documents/pdf/200-AD.12.01.PE.0_Standard%20Duct_12el.pdf
- **Datwyler**, FO Outdoor wbKT HP A-DQ(ZN)2Y, https://static.datwyler-itinfra.com/assets/ProductImages/FO-Outdoor-wbKT-HP_A-DQZN2YSTEP_PRODUCT_100606220724_EN.pdf
- **Legrand**, PEP ecopassport LGRP-02008, https://assets.legrand.com/pim/DOCUMENT/LGRP-02008-V01.01-EN.pdf
- **efobasen**, HDPE duct 40 mm (0.375 kg/m), https://efobasen.efo.no/API/Produktfiler/LastNed?id=1337038
- **Faberkabel**, HDPE sub-duct 50 mm (670 kg per 1000 m), https://shop.faberkabel.de/en/Microducts-Multiducts-and-accessories/HDPE-Sub-Ducts-and-accessories/Sub-Duct-Broadband-Telecom-Energy-PE-HD/073810.html
- **Emtelle**, HDPE duct specification, https://www.emtelle.com/Content/Uploads/MHT2639.pdf
- **Prysmian**, ADSS TC09376 (92–170 kg/km), https://ro.prysmian.com/sites/ro.prysmian.com/files/media/documents/TC09376-en%20v3.pdf
- **Hexatronic**, ADSS 144 fibers (260 kg/km), https://www.hexatronic.com/hubfs/datasheets/28701-TOL4032003%2BC_en-au_Hexatronic.pdf
- **Corning**, ADSS aramid single jacket (84–165 kg/km), https://www.corning.com/catalog/coc/documents/product-family-specifications/pfss/a/en-US/adss-aramid-single-jacket-cable-up-to-100m-span-lt-2.3_China_AEN.pdf

### Materials — fiber on power lines (Switzerland)
- **Swiss Federal Supreme Court**, judgment 1C_417/2017 (28 Mar 2019), https://servat.unibe.ch/dfr/bger/2019/190328_1C_417-2017.html
- **Swissgrid**, Overhead line and underground cabling, https://www.swissgrid.ch/dam/swissgrid/about-us/newsroom/publications/overhead-line-underground-cabling-de.pdf

### Materials — copper
- **Swisscom**, Handbuch Technik Teilnehmeranschlussleitung V2-0 (2010), https://www.swisscom.ch/content/dam/swisscom/de/ws/documents/D_FMG-Dokumente/TAL/D_TAL_HB_Technik_V2-0.pdf
- **Swisscom**, Abschaltung des Kupfernetzes, https://www.swisscom.ch/de/about/netz/kupferanschluss.html
- **Outdoor telephone cable datasheet**, https://storage.mtender.gov.md/get/483cb213-0210-4f50-986b-4e0cccd79ef2-1724051631042
- **Analysys Mason**, Recovering copper (BT: 121 M km of pairs ≈ 390,000 t copper), https://www.analysysmason.com/research/content/articles/recovering-copper-emissions-rma08-rdfi0/

### Materials — submarine cables
- **Nexans**, URC-1 Light Weight (650 kg/km), https://www.nexans.no/en/products/Fiberoptic-Cables-and-Components/Submarine-Fiber-Cables/URC-1-Ligh10763.html
- **Nexans**, URC-1 single armoured (1,700 kg/km), https://www.nexans.no/en/products/Fiberoptic-Cables-and-Components/Submarine-Fiber-Cables/URC-1-Sing10764/product~10212113~.html
- **Hexatronic**, Submarine Cable Single Armored 10 ton SA (1,100 kg/km), https://www.hexatronic.com/hubfs/datasheets/28701-10_ton_SA_en_Hexatronic.pdf

### Mobile network
- **BAFU**, Mobil telefonieren: wie funktioniert das?, https://www.bafu.admin.ch/de/mobil-telefonieren-wie-funktioniert-das
- **Swisscom**, Informationen zur Mobilfunkinfrastruktur, https://www.swisscom.ch/content/dam/swisscom/de/about/verantwortung/flexibles-arbeiten/documents/Informationen-zur-Mobilfunkinfrastruktur.pdf
- **Swisscom**, Wie Swisscom Antennenstandorte findet (2023), https://www.swisscom.ch/de/about/news/2023/11/29-standorte.html
- **Swisscom**, Investitionen in die Zukunft, https://www.swisscom.com/content/dam/assets/about/netz/mobilfunk-antennen-gesundheit/documents/investitionen-in-die-zukunft.pdf
- **horizont.net**, Swisscom arbeitet mit Ericsson zusammen, https://www.horizont.net/schweiz/nachrichten/swisscom-arbeitet-mit-ericsson-zusammen-hard--und-software-fuer-ein-wettbewerbfaehiges-mobilnetz-219215
- **Stadt St. Gallen**, Standortdatenblatt Lukasstrasse 30, https://www.stadt.sg.ch/content/dam/dokument_library/dpb/abb/baubewilligungen/63023-lukasstrasse-30/01%20Standortdatenbl%C3%A4tter.pdf
- **Stadt St. Gallen**, Standortdatenblatt Hechtackerstrasse 9, https://www.stadt.sg.ch/content/dam/dokument_library/dpb/abb/baubewilligungen/63022-hechtackerstrasse-9/01%20Standortdatenbl%C3%A4tter.pdf
- **Stadt Baden**, Standortdatenblatt Stadtturmstrasse 5, https://www.baden.ch/public/upload/assets/217851/AA20211213_Standortdatenblatt.pdf?fp=1
- **Stadt St. Gallen**, Standortdatenblatt Teufen, https://www.stadt.sg.ch/content/dam/dokument_library/dpb/abb/baubewilligungen/63014-wattbachstrasse-40-ca-/02%20Standortdatenblatt.pdf
- **Ericsson**, AIR 3268 (12 kg), https://www.ericsson.com/en/news/2021/9/ericsson-launches-ultra-lightweight-air-3268-radio
- **Mobile World Live**, Ericsson, BT unveil compact radio, https://www.mobileworldlive.com/bt/ericsson-bt-unveil-compact-radio/
- **Kathrein**, base station antenna datasheet (31 kg), https://www.scribd.com/document/403397354/9364271
- **CommScope / Andrew**, RRZZVVQ4Q4-65D-R8 (56.5 kg), https://de.andrew.com/products/base-station-antennas/antennas/itemrrzzvvq4q4-65dr8
- **CommScope / Andrew**, RRZZVVT4S4-65B-R8 (48 kg), https://es.andrew.com/products/base-station-antennas/antennas/itemrrzzvvt4s4-65b-r8
- **CommScope**, NNH4S4-65B-R7 (41.3 kg), https://de.commscope.com/product-type/antennas/base-station-antennas-equipment/base-station-antennas/itemnnh4s4-65b-r7
- **CommScope / Andrew**, RRV4Q4-65A-R7, https://www.andrew.com/products/base-station-antennas/antennas/itemrrv4q4-65a-r7
- **Huawei Agisson**, base station antennas, https://www.scribd.com/document/483686353/Huawei-Agisson-pdf
- **FiberHome**, base station antenna (38.8 kg), https://www.scribd.com/document/559873125/FiberHome-HXPM12X37QBYW1618065T2FT2C
- **Golard & Dethienne, UCLouvain**, parametric LCA model for 4G/5G base stations (restricted access), https://research.dial.uclouvain.be/bitstreams/28a3a27d-0890-4c03-b73e-559d5aacfb56/download
- **Swisscom**, Mobilfunkantenne im Kabelschacht (2015), https://www.swisscom.ch/dam/swisscom/de/about/medien/medienmitteilung/2015/20151008-MM-Swisscom-ruestet-ihr-Mobilfunknetz-fuer-die-Zukunft-DE.pdf.res/20151008-MM-Swisscom-ruestet-ihr-Mobilfunknetz-fuer-die-Zukunft-DE.pdf
- **Ericsson**, Swisscom and Ericsson plant LTE small cells underground (2016), https://www.ericsson.com/en/news/2016/3/swisscom-and-ericsson-plant-lte-small-cells-underground
- **Netzwoche**, Swisscom darf in Bern 100 Mikrozellen installieren (2017), https://www.netzwoche.ch/news/2017-03-06/swisscom-darf-in-bern-100-mikrozellen-installieren
- **Swisscom**, Simulation Mobilfunk-Kleinzellennetz St. Gallen (2020), https://www.swisscom.ch/de/about/news/2020/07/02-mobilfunk-kleinzellennetz.html

# Breakbulk Voyage Economics Model (TCE, Laytime & Demurrage)

An Excel voyage estimator for a multipurpose heavy-lift vessel carrying project cargo from Shanghai to Jebel Ali. It calculates what the voyage earns per day (TCE), whether it covers the cost of chartering the ship in, what freight rate to quote, and how demurrage and laytime play out at the load port. It also stress-tests the result against vessel speed, bunker prices and port delays.

Built on real market inputs (Singapore bunker prices, sea distances, published vessel specs) with an **illustrative** cargo and port-call scenario.

---

## Scenario

| | |
|---|---|
| **Vessel** | 12,500 dwt multipurpose heavy-lift vessel (MPP), chartered in on time charter |
| **Route** | Open Singapore → ballast to Shanghai (load) → laden to Jebel Ali (discharge) |
| **Cargo** | 6,000 t project cargo (steel modules) |
| **Commercial set-up** | Operator charters the ship in at a daily hire rate and carries the cargo on voyage terms (freight per tonne), acting as **disponent owner** |

---

## Workbook structure

| Sheet | What it does |
|---|---|
| **Inputs** | Every assumption in one place, with a source or note for each. Blue = input, black = formula, green = link from another sheet. All inputs are named cells (e.g. `LadenSpeed`, `VLSFO`, `HireRate`). |
| **Voyage** | Voyage estimate: sea and port days → bunker consumption and cost → voyage costs → gross and net freight → net voyage result → **TCE**. Compares TCE against hire, and solves for the freight rate needed to hit a target TCE and the breakeven rate. Includes a key-results panel and an accept / marginal / reject verdict. |
| **Laytime & Demurrage** | Laytime allowance from cargo and load rate, an illustrative **Statement of Facts** for the Shanghai load port, hours counted against laytime, and the resulting demurrage or despatch. |
| **Sensitivity** | (1) TCE grid across laden speed (11–14 kn) and VLSFO price ($650–$1,050/t), with fuel consumption scaled by the cube law. (2) Port-delay table showing TCE and profit with and without demurrage recovery. |

---

## Key results (base case)

| Metric | Value |
|---|---|
| Total voyage days | 33.97 |
| VLSFO consumed | 596 t |
| Total voyage costs | $658,513 |
| Net freight (after 5% commissions) | $1,140,000 |
| **TCE** | **$14,176 / day** |
| Market hire rate (assumed) | $14,000 / day |
| Voyage profit after hire | $5,965 (≈ $176 / day) |
| **Required freight rate @ $16,000/day target TCE** | **$210.87 / t** |
| Breakeven freight rate @ hire | $198.95 / t |
| Load port laytime: allowed vs used | 96 h vs 107 h |
| Demurrage payable to operator | $6,875 |

**Reading:** at the quoted $200/t the voyage only just covers hire. A $1/t margin over breakeven is too thin to absorb a single day's delay, so the model points to countering at about $211/t.

---

## Insights from the sensitivity analysis

1. **Slow steaming pays at current fuel prices.** At $839/t VLSFO, slowing the laden leg from 13 to 11 knots raises TCE from $14,176 to $15,780/day. Daily consumption falls with the cube of speed, and at 13 kn the ship burns about $20,100/day of fuel, more than the $14,000/day hire. So the fuel saved outweighs the hire paid for the extra 3.5 days.
2. **Bunker prices decide whether the voyage works.** At 13 kn, TCE drops below hire once VLSFO passes roughly $850/t. At $950/t it falls to $12,229/day, a loss of about $1,800/day.
3. **Going faster only pays when fuel is cheap or hire is expensive.** Speeding up makes sense when daily hire costs more than the extra fuel needed to save a day.
4. **Demurrage protects the operator from delays.** Each extra port day costs about $17,600 in hire and fuel. Without demurrage, one day of delay turns the voyage loss-making (−$11,614). With demurrage at $15,000/day, the voyage still makes money after two days of delay. This is why the demurrage rate is set above the hire rate.
5. **Slow steaming has a cost the model doesn't capture.** The cargo arrives about 3.5 days later, which may break the customer's delivery window or cost the next cargo.

---

## Data sources

| Input | Source |
|---|---|
| VLSFO $839/t, LSMGO $1,193/t | ENGINE, Singapore bunker prices, 16 Nov 2026 |
| Shanghai–Singapore 2,190 nm; Singapore–Jebel Ali 3,492 nm | Fluent Cargo sea distances (port codes CNSHG, SGSIN, AEJEA) |
| Vessel speeds (14 kn ballast / 13 kn laden) | BBC Chartering 12K multipurpose heavylifter spec sheet |
| Consumption, port costs, cargo, freight, hire, laytime terms | Assumptions (see Inputs sheet notes) |

---

## Assumptions and limitations

- **Illustrative scenario.** The cargo, freight rate, hire rate and the Statement of Facts are constructed to demonstrate the method. This is not a real fixture.
- No waiting time at anchorage at the discharge port, no canal transit, and no bunkering detour.
- The ballast leg burns VLSFO only; MGO is used in port only.
- Cube law applied to laden consumption only. Real speed–consumption curves depend on draft, hull condition and weather.
- The port-delay table assumes the whole delay is the charterer's fault and beyond laytime, and adds no extra port dues.
- Commissions: 3.75% address commission + 1.25% brokerage, both deducted from gross freight.

---

## How to use

1. Open the **Inputs** sheet and change any blue cell, for example the VLSFO price, the freight rate or the hire rate.
2. The **Voyage** sheet's key-results panel and verdict update automatically.
3. Use the **Sensitivity** sheet to see how far the result moves when speed, bunker price or port time changes.

---

## Skills demonstrated

Voyage estimation and TCE · voyage vs time charter economics · laytime, demurrage and despatch · bunker cost and slow-steaming analysis · freight rate solving · Excel modelling (named ranges, mixed references, sensitivity grids, conditional formatting)

---

**Author:** Reuben Tay, Operations & Supply Chain Management, National University of Singapore
[LinkedIn](https://linkedin.com/in/reuben-tay)

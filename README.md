# Leo DDR4 Reuse Calculator

A one-page sales and FAE tool for Astera Labs' Leo CXL Smart Memory Controllers. A buyer enters their server refresh, and the page shows how much retired DDR4 can come back as CXL-attached memory, what new DDR5 they avoid buying, and the net savings after CXL cards and testing.

**Live page:** https://tp433-star.github.io/leo-ddr4-reuse-calculator/

Concept by Tanisha John. Not an official Astera Labs tool.

## What it does

- **Fleet inputs:** new servers, memory target per server, native DDR5, retired servers, DDR4 per retired server, and the share that passes testing.
- **Cost inputs:** new DDR5 price per GB, CXL memory card cost per server, and test and redeploy cost per GB.
- **Results:** net savings, TB of DDR4 reused, share of the memory gap filled, savings per server, and a cost breakdown.
- **Inside one server:** how memory splits between native DDR5, reused DDR4 behind Leo, and any gap still bought new.
- **Honest loss state:** when the cards cost more than the DDR5 they replace, the result turns red and says so.
- **Positioning brief:** who buys, the first objection (CXL latency) and how to answer it with tiering, and what proof to bring.

## The math

```
memory gap      = (target per server - native DDR5 per server) x new servers
DDR4 available  = retired servers x DDR4 per retired server x pass rate
DDR4 reused     = min(DDR4 available, memory gap)
net savings     = DDR4 reused x DDR5 $/GB
                  - new servers x CXL card cost
                  - DDR4 reused x test $/GB
```

Default example: 1,000 new servers, 800 retired. About 340 TB of DDR4 reused and roughly $1.1M saved. At $3,000 per card, the same fleet loses about $389K.

## Assumptions

Every default is illustrative and editable on the page. None of it is Astera Labs data. Swap in real quotes before using the numbers in a customer conversation.

## Run it

Open `index.html` in a browser. No build step and no dependencies beyond Google Fonts.

Built around the Leo launch at AI Infra Summit, Sep 15, 2026.

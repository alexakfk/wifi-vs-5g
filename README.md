# Wi-Fi vs. 5G Cellular — Columbia Campus Network Performance

An interactive data visualization comparing Wi-Fi and 5G cellular network performance across Columbia University's Morningside Heights campus. Built as a supplementary companion to a literature review for **COMS 4419 — Internet Economics, Policy, and Technology**.

**Authors:** Alexa Kafka & Theo Zaritsky

## About

This project presents original empirical data collected on Columbia's campus to investigate a question at the intersection of internet economics and policy: **can institutional Wi-Fi reliably substitute for cellular connectivity, or do 5G networks outperform in key scenarios?**

The visualization is designed to make the raw data explorable and to surface findings that support the arguments in our literature review — particularly around the assumptions policymakers and institutions make about Wi-Fi offloading cellular demand.

## Dataset

All data was collected in-person across the Columbia campus using speed test measurements.

| Parameter       | Detail                                                  |
| --------------- | ------------------------------------------------------- |
| Total readings  | 144                                                     |
| Networks tested | Columbia Wi-Fi, 5G Cellular                             |
| Locations       | 6 campus quadrants (Q1–Q6)                              |
| Environments    | Indoor and Outdoor at each quadrant                     |
| Time sessions   | AM (~8:30–11:30 a.m.) and PM (~5:00–6:30 p.m.)         |
| Repetitions     | 3 per condition                                         |
| Metrics         | Download speed (Mbps), Upload speed (Mbps), Latency (ms)|

### Campus Quadrants

| Quadrant | Location(s)              |
| -------- | ------------------------ |
| Q1       | Pupin Hall / Shapiro     |
| Q2       | Mudd Building            |
| Q3       | Earl Hall / Low Library  |
| Q4       | Avery Library            |
| Q5       | Lerner Hall              |
| Q6       | John Jay / Hamilton      |

## Visualization Tabs

The dashboard is organized into six interactive tabs:

- **Overview** — Aggregate statistics (average download, upload, latency) and per-quadrant bar charts for download speed, upload speed, latency, and a speed distribution histogram.
- **Campus Map** — An SVG map of Columbia's campus. Click any quadrant to view a detailed breakdown (indoor vs. outdoor, Wi-Fi vs. 5G) with a radar chart comparing download, upload, and inverse-latency across conditions.
- **Indoor vs Outdoor** — Side-by-side comparison of how each network performs indoors versus outdoors, including a delta chart showing the magnitude of the indoor-outdoor gap.
- **AM vs PM** — Time-of-day analysis showing how network congestion (particularly on Wi-Fi) affects performance between morning and evening sessions.
- **Reliability** — Coefficient of variation and standard deviation charts per quadrant, a scatter plot of all 144 observations, and a summary table with mean, std dev, CV%, and range for every quadrant-network pair.
- **Findings** — Eight data-driven insight cards summarizing the key takeaways, including the Q5/Q6 reversal where 5G dominates Wi-Fi indoors, 5G's consistent latency disadvantage, and policy implications for campus network planning.

## Key Findings

1. **Wi-Fi wins on aggregate download speed**, but this masks significant per-building variation.
2. **Latency: Wi-Fi wins everywhere** — ~4–5x lower latency than 5G across every quadrant and condition.
3. **5G dominates in Lerner Hall (Q5) and John Jay (Q6)**, where campus Wi-Fi appears under-provisioned.
4. **Outdoors, 5G closes the gap** and wins outright in Q4–Q6, suggesting denser tower deployment near lower campus.
5. **Wi-Fi speeds drop ~15 Mbps in PM sessions** due to campus congestion; 5G is more time-stable.
6. **5G upload collapses in Avery Library (Q4)** — averaging ~8 Mbps vs. Wi-Fi's 157 Mbps, indicating deep indoor signal degradation.

## Tech Stack

- **Single-file architecture** — The entire application is a self-contained `index.html` with no build step.
- **[Chart.js 4.4.1](https://www.chartjs.org/)** — All charts (bar, scatter, radar, histogram) rendered via CDN.
- **Fonts** — [Space Mono](https://fonts.google.com/specimen/Space+Mono) (headings, data labels) and [DM Sans](https://fonts.google.com/specimen/DM+Sans) (body text) via Google Fonts.
- **No frameworks or bundlers** — Pure HTML, CSS, and vanilla JavaScript.

## Running Locally

No build step is required. Open `index.html` directly in a browser:

```bash
open index.html
```

Or serve it locally to avoid any CORS issues with fonts:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Project Structure

```
wifi-vs-5g/
├── index.html   # Entire application (HTML + CSS + JS + embedded data)
└── README.md    # This file
```

## License

This project was created for academic purposes as part of Columbia University's COMS 4419 course. The data and visualizations are original work by the authors.

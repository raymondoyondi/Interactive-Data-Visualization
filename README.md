# Interactive & Animated Data Visualizations 📊

Building beautiful, performant, and reactive data visualizations by combining the declarative power of **Svelte** with the mathematical precision of **D3.js**.

This repository serves as a comprehensive learning resource and a collection of production-ready patterns for modern web-based data storytelling.

---

## 🚀 The Philosophy: "Svelte for DOM, D3 for Math"

Traditional D3 manipulation often fights against modern framework reactivity. This project demonstrates the "Hybrid Approach":

* **Svelte Handles:** DOM elements (`<svg>`, `<rect>`, `<path>`), lifecycle transitions, state management, and user interactions.
* **D3 Handles:** Mathematical scaling (`d3-scale`), shape generation (`d3-shape`), geographic projections (`d3-geo`), and complex data parsing.



---

## 🛠️ Tech Stack

* **Svelte / SvelteKit:** Component-based UI and reactive state management.
* **D3.js:** The mathematical engine for visualization logic.
* **LayerCake:** (Optional) A graphics framework for Svelte.
* **Tailwind CSS:** For styling chart UI, legends, and tooltips.

---

## 📈 Featured Visualizations

| Visualization | Key Concepts | Features |
| :--- | :--- | :--- |
| **Animated Bar Chart** | `d3-scaleLinear`, Svelte `tweened` | Racing animations, sorted updates, and rank transitions. |
| **Global Choropleth** | `d3-geo`, GeoJSON, `d3-scaleThreshold` | Interactive tooltips, zoom-to-country, and color choropleths. |
| **Reactive Scatter Plot** | `d3-extent`, Axis components | Dynamic resizing, color encoding, and Voronoi overlays. |
| **Real-time Line Graph** | `d3-line`, `d3-time-scale` | Streaming data visualization with smooth path transitions. |

---

## 💡 Implementation Patterns

### 1. Reactive Scales
Instead of manual updates, we use Svelte's reactive declarations (`$:`) to update scales automatically whenever data or container dimensions change.

```javascript
// Scale remains reactive to both data updates and chart resizing
$: xScale = d3.scaleLinear()
    .domain([0, d3.max(data, d => d.value)])
    .range([0, width]);
```

2. **The Reusable Axis Component**
A key pattern in this repo is separating the **Axis** into its own component. We pass the D3 scale as a prop, allowing Svelte to iterate through the ticks.

```
<script>
  export let xScale;
  $: ticks = xScale.ticks();
</script>

{#each ticks as tick}
  <g transform="translate({xScale(tick)}, 0)">
    <line y2="6" stroke="currentColor" />
    <text y="20" text-anchor="middle">{tick}</text>
  </g>
{/each}
```

---

# 📂 Project Structure

`
src/
├── components/
│   ├── charts/          # Core chart components (BarChart.svelte, LineChart.svelte)
│   ├── elements/        # Reusable SVG parts (Axis.svelte, Tooltip.svelte)
│   └── layout/          # Chart containers and responsive wrappers
├── data/                # Sample datasets (CSV, JSON, GeoJSON)
└── utils/               # D3 formatters, color schemes, and data parsers
`

---

# 🏃 Getting Started

1. **Clone the repository:**
   ```
   git clone [https://github.com/raymondoyondi/Interactive-Data-Visualization.git](https://github.com/raymondoyondi/Interactive-Data-Visualization.git)
   ```

2. **Install dependencies:**
   ```
   npm install
   ```

3. **Run the development server:**
   ```
   npm run dev
   ```

---

# 🤝 Contributing

Contributions make the open-source community an amazing place to learn and create.

1. **Fork** the Project.
2. **Create** your Feature Branch (`git checkout -b feature/AmazingFeature)`.
3. **Commit** your Changes (`git commit -m 'Add some AmazingFeature`).
4. **Push** to the Branch (`git push origin feature/AmazingFeature`).
5. **Open** a Pull Request.

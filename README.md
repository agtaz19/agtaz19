<!DOCTYPE html>
<html>
<body style="margin:0; background:transparent; display:flex; justify-content:center; align-items:center; height:100vh;">
<canvas id="torus" width="800" height="450"></canvas>
<script>
const canvas = document.getElementById('torus');
const ctx = canvas.getContext('2d');
let A = 0, B = 0;

function render() {
    ctx.clearRect(0, 0, 800, 450);
    ctx.font = "12px monospace";
    
    let b = [];
    let z = [];
    A += 0.07; B += 0.03;
    
    // Sunset color palette
    const colors = ["#FF5E5B", "#FF8C42", "#FFC15E", "#F9F871"];

    for (let j = 0; j < 6.28; j += 0.3) {
        for (let i = 0; i < 6.28; i += 0.1) {
            let c = Math.sin(i), d = Math.cos(j), e = Math.sin(A), f = Math.sin(j), g = Math.cos(A),
                h = d + 2, D = 1 / (c * h * e + f * g + 5), l = Math.cos(i), m = Math.cos(B), n = Math.sin(B),
                t = c * h * g - f * e;
            let x = 0 | (40 + 30 * D * (l * h * m - t * n));
            let y = 0 | (12 + 15 * D * (l * h * n + t * m));
            let o = 0 | (40 + 80 * D * (c * h * g - f * e));
            if (y < 22 && y >= 0 && x >= 0 && x < 80 && D > (z[x + 80 * y] || 0)) {
                z[x + 80 * y] = D;
                b[x + 80 * y] = ".:-=+*#%@"[o % 9];
            }
        }
    }

    // Draw with Shadow and Sunset Colors
    ctx.shadowBlur = 10;
    ctx.shadowColor = "#FF5E5B";
    ctx.fillStyle = "#FFC15E";
    for (let i = 0; i < 80 * 22; i++) {
        let x = (i % 80) * 10;
        let y = (Math.floor(i / 80)) * 20;
        if (b[i]) ctx.fillText(b[i], x, y);
    }
    requestAnimationFrame(render);
}
render();
</script>
</body>
</html>


![Matrix SVG](https://raw.githubusercontent.com/rodrigograca31/rodrigograca31/master/matrix.svg)

<p align="center">
  <a href="https://www.linkedin.com/in/alexandre-tilly"><img src="https://img.shields.io/badge/linkedin-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>&nbsp;
  <a href="mailto:agtaz19@gmail.com"><img src="https://img.shields.io/badge/gmail-%23D14836.svg?&style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"/></a>&nbsp;
  <a href="https://agtaz19.github.io/"><img alt="Website" src="https://img.shields.io/website?style=for-the-badge&up_message=portfolio&url=https%3A%2F%2Fkkvanonymous.github.io%2F"></a>&nbsp;
</p>

---

# Alexandre Tilly &nbsp; <img src="https://komarev.com/ghpvc/?username=agtaz19&label=Profile%20views&color=0e75b6&style=flat" alt="agtaz19" /> ![GitHub followers](https://img.shields.io/github/followers/agtaz19) ![GitHub User's stars](https://img.shields.io/github/stars/agtaz19)
Quantitative Finance | Systematic Investing | Enterprise Transformation

<br>

I design and implement data-driven systems for financial decision-making — 
from crisis-investing frameworks and trading simulations to large-scale 
business transformation initiatives in financial institutions.

## Focus Areas

- Systematic trading and portfolio construction
- Quantitative research and financial modeling
- Market simulation and competition design
- Alternative investments and prime services
- Enterprise transformation in financial services
- Data pipelines and decision systems

## Featured Projects

### Crisis-Investing Framework (IBKR Integration)
Systematic equity strategy implementing post-dislocation recovery signals.

- Operationalized academic crisis-investing research into screening rules
- Built Python pipeline for fundamentals, signal generation, and execution
- Tested across historical market dislocations
- Integrated with Interactive Brokers paper trading environment

---

### Trading Competition Simulation Platform
Designed a multi-style simulated trading environment for quant, technical, 
and discretionary participants.

- Synthetic market data generation
- Strategy-agnostic scoring system
- Team-based competition architecture
- Performance analytics dashboard

---

### Election Analytics Dashboard Prototype
Multi-page dashboard for hierarchical election reporting.

- Built with Dash + Plotly
- Supports state, county, and city-level views
- Real-time data ingestion from structured sources

## Professional Experience

**FTI Consulting — Business Transformation**
- Enterprise process optimization and operating model design
- Financial services engagements including prime services initiatives

**State Street — Alternative Investments**
- Business transformation across investment operations
- Focus on scalability, risk controls, and operational efficiency

## Research & Competitions

- Organizer of quantitative research competitions
- Developed problem sets spanning mathematics, CS, and finance
- Designed evaluation frameworks for heterogeneous approaches

## Contact

<p align="center" > 
  <i>Thanks for passing by</i><br><br>
  <i>Feel free to connect with me</i><br><br>
  <a href="https://www.linkedin.com/in/alexandre-tilly/">
  <code><img alt="My linkedin" width="32" src="./images/linkedin.svg" /></code>
</a>
</p>

## Planned Updates:
I am planning on updating somethings to this read me:

1. Torus in the header
2. Update content to reflect current activity and highlight personal projects
3. Talk about organizations and involvement

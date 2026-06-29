<svg viewBox="0 0 1600 900" width="100%" height="100%" xmlns="http://www.w3.org/2000/svg">
  <foreignObject x="0" y="0" width="1600" height="900">
    <div xmlns="http://www.w3.org/1999/xhtml" style="width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; background: transparent; overflow: hidden; font-family: monospace;">
      <pre id="torus-render" style="font-size: 14px; line-height: 12px; font-weight: bold; cursor: default;"></pre>
    </div>

    <script>
      (function() {
        const pre = document.getElementById('torus-render');
        let A = 1, B = 1;
        
        // Sunset color palette cycle
        const colors = ["#FF4500", "#FF8C00", "#FFD700", "#FF6347", "#8B0000"];
        
        function render() {
          let b = [];
          let z = [];
          let [x, y] = [80, 40]; // Canvas size for ASCII
          A += 0.07; B += 0.03;
          let cA = Math.cos(A), sA = Math.sin(A), cB = Math.cos(B), sB = Math.sin(B);
          
          for (let k = 0; k < 3200; k++) {
            b[k] = ' ';
            z[k] = 0;
          }

          for (let j = 0; j < 6.28; j += 0.3) {
            let ct = Math.cos(j), st = Math.sin(j);
            for (let i = 0; i < 6.28; i += 0.1) {
              let sp = Math.sin(i), cp = Math.cos(i), h = ct + 2;
              let D = 1 / (sp * h * sA + st * cA + 5);
              let t = sp * h * cA - st * sA;
              let px = Math.floor(40 + 30 * D * (cp * h * cB - t * sB));
              let py = Math.floor(20 + 15 * D * (cp * h * sB + t * cB));
              let o = px + 80 * py;
              let N = Math.floor(8 * ((st * sA - sp * ct * cA) * cB - sp * ct * sA - st * cA - cp * ct * sB));
              
              if (py >= 0 && py < 40 && px >= 0 && px < 80 && D > z[o]) {
                z[o] = D;
                b[o] = ".,-~:;=!*#$@"[N > 0 ? N : 0];
              }
            }
          }
          
          pre.innerHTML = b.join('');
          pre.style.color = colors[Math.floor(Date.now() / 1000 % colors.length)];
          pre.style.textShadow = "2px 2px 5px rgba(255, 69, 0, 0.5)";
          requestAnimationFrame(render);
        }
        render();
      })();
    </script>
  </foreignObject>
</svg>
---



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

(function() {
var _onload = function() {
  var pretag = document.getElementById('d');
  var canvastag = document.getElementById('canvasdonut');

  var tmr1 = undefined, tmr2 = undefined;
  var A=1, B=1;

  // This is copied, pasted, reformatted, and ported directly from my original
  // donut.c code
  var asciiframe=function() {
    var b=[];
    var z=[];
    A += 0.07;
    B += 0.03;
    var cA=Math.cos(A), sA=Math.sin(A),
        cB=Math.cos(B), sB=Math.sin(B);
    for(var k=0;k<1760;k++) {
      b[k]=k%80 == 79 ? "\n" : " ";
      z[k]=0;
    }
    for(var j=0;j<6.28;j+=0.07) { // j <=> theta
      var ct=Math.cos(j),st=Math.sin(j);
      for(i=0;i<6.28;i+=0.02) {   // i <=> phi
        var sp=Math.sin(i),cp=Math.cos(i),
            h=ct+2, // R1 + R2*cos(theta)
            D=1/(sp*h*sA+st*cA+5), // this is 1/z
            t=sp*h*cA-st*sA; // this is a clever factoring of some of the terms in x' and y'

        var x=0|(40+30*D*(cp*h*cB-t*sB)),
            y=0|(12+15*D*(cp*h*sB+t*cB)),
            o=x+80*y,
            N=0|(8*((st*sA-sp*ct*cA)*cB-sp*ct*sA-st*cA-cp*ct*sB));
        if(y<22 && y>=0 && x>=0 && x<79 && D>z[o])
        {
          z[o]=D;
          b[o]=".,-~:;=!*#$@"[N>0?N:0];
        }
      }
    }
    pretag.innerHTML = b.join("");
  };

  window.anim1 = function() {
    if(tmr1 === undefined) {
      tmr1 = setInterval(asciiframe, 50);
    } else {
      clearInterval(tmr1);
      tmr1 = undefined;
    }
  };

  // This is a reimplementation according to my math derivation on the page
  var R1 = 1;
  var R2 = 2;
  var K1 = 150;
  var K2 = 5;
  var canvasframe=function() {
    var ctx = canvastag.getContext('2d');
    ctx.fillStyle='#000';
    ctx.fillRect(0, 0, ctx.canvas.width, ctx.canvas.height);

    if(tmr1 === undefined) { // only update A and B if the first animation isn't doing it already
      A += 0.07;
      B += 0.03;
    }
    // precompute cosines and sines of A, B, theta, phi, same as before
    var cA=Math.cos(A), sA=Math.sin(A),
        cB=Math.cos(B), sB=Math.sin(B);
    for(var j=0;j<6.28;j+=0.3) { // j <=> theta
      var ct=Math.cos(j),st=Math.sin(j); // cosine theta, sine theta
      for(i=0;i<6.28;i+=0.1) {   // i <=> phi
        var sp=Math.sin(i),cp=Math.cos(i); // cosine phi, sine phi
        var ox = R2 + R1*ct, // object x, y = (R2,0,0) + (R1 cos theta, R1 sin theta, 0)
            oy = R1*st;

        var x = ox*(cB*cp + sA*sB*sp) - oy*cA*sB; // final 3D x coordinate
        var y = ox*(sB*cp - sA*cB*sp) + oy*cA*cB; // final 3D y
        var ooz = 1/(K2 + cA*ox*sp + sA*oy); // one over z
        var xp=(150+K1*ooz*x); // x' = screen space coordinate, translated and scaled to fit our 320x240 canvas element
        var yp=(120-K1*ooz*y); // y' (it's negative here because in our output, positive y goes down but in our 3D space, positive y goes up)
        // luminance, scaled back to 0 to 1
        var L=0.7*(cp*ct*sB - cA*ct*sp - sA*st + cB*(cA*st - ct*sA*sp));
        if(L > 0) {
          ctx.fillStyle = 'rgba(255,255,255,'+L+')';
          ctx.fillRect(xp, yp, 1.5, 1.5);
        }
      }
    }
  }


  window.anim2 = function() {
    if(tmr2 === undefined) {
      tmr2 = setInterval(canvasframe, 50);
    } else {
      clearInterval(tmr2);
      tmr2 = undefined;
    }
  };

  if (pretag !== undefined) {
    asciiframe();
    window.anim1();
  }
  if (canvastag !== undefined) {
    canvasframe();
  }
}

if(document.all)
  window.attachEvent('onload',_onload);
else
  window.addEventListener("load",_onload,false);
})();


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

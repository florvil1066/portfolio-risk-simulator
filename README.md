# 📊 Portfolio Risk Simulator - Monte Carlo Analysis

A comprehensive Monte Carlo simulation tool for assessing stock portfolio risk and returns, built for data-driven investment decision-making.

**Course:** CAP4767 - AI-Driven Business Innovation  
**Assignment:** Monte Carlo Analysis & Decision Support Application  
**Author:** Florvil Occean  
**Date:** November 5, 2025

---

## 🎯 Project Overview

This project uses Monte Carlo simulation to quantify uncertainty in stock portfolio returns, helping investors and financial advisors make data-driven decisions. By simulating 10,000+ possible market scenarios, the tool provides:

- **Expected portfolio value** with confidence intervals
- **Probability of profit** and various return targets
- **Value at Risk (VaR)** for downside protection
- **Interactive visualizations** for stakeholder communication
- **Risk-based recommendations** for position sizing

---

## 🚀 Live Demo

**Web Application:** (https://rad-salamander-c12ce1.netlify.app/)  
**Google Colab Analysis:** https://colab.research.google.com/drive/1wkjO78zNk65R2JdVXP40QdNGULHgBRw-?usp=sharing

---

## 📁 Repository Structure

```
portfolio-risk-simulator/
│
├── index.html                 # Interactive web application
├── colab_notebook.ipynb       # Google Colab Monte Carlo analysis
├── README.md                  # This file
├── executive_summary.pdf      # 1-page project summary
└── requirements.txt           # Python dependencies
```

---

## 🔍 Problem Statement

**Business Problem:**  
Investment advisors need to assess portfolio risk and potential returns over a 1-year horizon to provide clients with realistic expectations and appropriate risk management strategies.

**Stakeholders:**
- Investment advisors making allocation decisions
- Portfolio managers rebalancing assets
- Individual investors evaluating risk tolerance

**Why Monte Carlo?**  
Stock returns are inherently uncertain. Traditional point forecasts fail to capture the range of possible outcomes. Monte Carlo simulation quantifies this uncertainty by generating thousands of possible market scenarios.

---

## 📊 Dataset

**Source:** Yahoo Finance via `yfinance` library  
**Time Period:** 5 years of daily stock prices  
**Portfolio Composition:**

| Stock | Sector | Weight |
|-------|--------|--------|
| AAPL | Technology | 25% |
| MSFT | Technology | 25% |
| JPM | Finance | 20% |
| JNJ | Healthcare | 15% |
| XOM | Energy | 15% |

**Data Quality:** Clean daily adjusted closing prices, no preprocessing required

---

## 🧮 Monte Carlo Model

### Mathematical Framework

```
Portfolio_Return_daily = Σ(Weight_i × Stock_Return_i)
Portfolio_Value_final = Initial × ∏(1 + Return_day_t)
```

### Distribution Selection

Each stock's daily return modeled as:
```
Stock_Return ~ N(μ, σ)
```

Parameters estimated from 5 years of historical data with correlation matrix to account for inter-stock dependencies.

### Simulation Parameters

- **Simulations:** 10,000 iterations
- **Time Horizon:** 252 trading days (1 year)
- **Initial Investment:** $100,000 (customizable)
- **Random Seed:** 42 (for reproducibility)

---

## 📈 Key Results

### Expected Outcomes
- **Mean Portfolio Value:** $108,245
- **Expected Return:** +8.2%
- **Probability of Profit:** 72.3%

### Risk Metrics
- **Value at Risk (95%):** $11,850 max loss
- **90% Confidence Interval:** [$88,150, $131,420]
- **Worst Case (5th percentile):** $88,150
- **Best Case (95th percentile):** $131,420

### Recommendation
**Risk Level:** MEDIUM - Suitable for moderate risk tolerance investors with 1+ year time horizon

---

## 🛠️ Technologies Used

### Analysis (Google Colab)
- **Python 3.8+**
- **NumPy** - Array operations and random sampling
- **Pandas** - Data manipulation
- **Matplotlib & Seaborn** - Statistical visualizations
- **SciPy** - Statistical tests (Shapiro-Wilk, Q-Q plots)
- **yfinance** - Historical stock data retrieval

### Web Application
- **HTML5** - Structure
- **CSS3** - Styling with gradients and animations
- **JavaScript (Vanilla)** - Monte Carlo simulation engine
- **Chart.js** - Interactive charts and visualizations
- **Responsive Design** - Mobile-friendly interface

### Deployment
- **Netlify / GitHub Pages** - Web app hosting
- **GitHub** - Version control and collaboration
- **Google Colab** - Cloud-based Jupyter notebook

---

## 📦 Installation & Setup

### Option 1: Run Google Colab Analysis

1. Open the Colab notebook: [Insert Your Colab Link]
2. Click "Copy to Drive" to save your own copy
3. Run all cells (Runtime → Run all)
4. Modify parameters in Step 6 as needed

### Option 2: Run Locally (Python)

```bash
# Clone the repository
git clone https://github.com/florvil1066/portfolio-risk-simulator.git
cd portfolio-risk-simulator

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter notebook
jupyter notebook colab_notebook.ipynb
```

### Option 3: Deploy Web Application

#### GitHub Pages Deployment:
1. Upload `index.html` to your GitHub repository
2. Go to repository Settings → Pages
3. Source: Select "Deploy from main branch"
4. Your site will be live at: `https://florvil1066.github.io/portfolio-risk-simulator`

#### Netlify Deployment:
1. Sign up at [netlify.com](https://netlify.com)
2. Click "Add new site" → "Import an existing project"
3. Connect your GitHub repository
4. Deploy settings:
   - Build command: (leave empty)
   - Publish directory: `/` (root)
5. Click "Deploy site"

---

## 🎮 Using the Web Application

### Step 1: Adjust Parameters

Use the interactive sliders to customize:
- **Initial Investment** ($10K - $500K)
- **Time Horizon** (30 - 500 trading days)
- **Number of Simulations** (1K - 50K)
- **Portfolio Weights** for each stock (0% - 100%)

### Step 2: Run Simulation

Click the **"Run Monte Carlo Analysis"** button to execute the simulation. The app generates thousands of scenarios in seconds.

### Step 3: Review Results

Analyze the output:
- **Expected Value & Returns** - Central tendency metrics
- **Value at Risk** - Maximum potential loss
- **Probability of Profit** - Chance of positive return
- **Distribution Charts** - Histogram and cumulative probability
- **Risk Assessment** - Color-coded recommendation

### Step 4: Make Decisions

Use the recommendation panel for:
- Position sizing guidance by risk tolerance
- Stop-loss placement suggestions
- Rebalancing strategy recommendations

---

## 📊 Application Features

The web application provides:

1. **Interactive Controls** - Real-time parameter adjustment via sliders
2. **Histogram** - Distribution of possible portfolio values with percentile markers
3. **Cumulative Distribution Function** - Probability of achieving different values
4. **Metrics Dashboard** - Key statistics displayed prominently
5. **Risk Assessment** - Color-coded recommendations (Low/Medium/High)
6. **Decision Support** - Actionable guidance for different risk tolerances

---

## 🧪 Testing the Application

### Validation Scenarios

Run these tests to validate the simulator:

**Test 1: Equal Allocation**
- Set all stocks to 20% each
- Expected: Balanced risk/return profile

**Test 2: High Tech Allocation**
- AAPL: 50%, MSFT: 50%, Others: 0%
- Expected: Higher volatility, higher returns

**Test 3: Defensive Allocation**
- JNJ: 50%, JPM: 50%, Others: 0%
- Expected: Lower volatility, moderate returns

**Test 4: Short Time Horizon**
- Set days to 30
- Expected: Tighter confidence intervals

**Test 5: Long Time Horizon**
- Set days to 500
- Expected: Wider distribution due to compounding

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Ideas for Contributions
- Add more portfolio optimization features
- Implement Black-Scholes options pricing
- Add risk parity allocation strategy
- Integrate real-time data feeds
- Add export to PDF functionality
- Implement portfolio backtesting

---

## 📝 Requirements

### Python Dependencies

```txt
numpy>=1.21.0
pandas>=1.3.0
matplotlib>=3.4.0
seaborn>=0.11.0
yfinance>=0.1.70
scipy>=1.7.0
jupyter>=1.0.0
```

Save this as `requirements.txt` in your project folder.

### Browser Requirements

- Modern browser with JavaScript enabled
- Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Canvas API support for Chart.js

---

## 🔐 Data Privacy & Security

- **No data collection:** The web app runs entirely in your browser
- **No server-side processing:** All calculations performed client-side
- **No external API calls:** Historical parameters hardcoded from analysis
- **Open source:** Full code transparency for security audit

---

## 📚 References & Resources

### Academic Papers
- Markowitz, H. (1952). "Portfolio Selection". Journal of Finance
- Black, F., & Scholes, M. (1973). "The Pricing of Options and Corporate Liabilities"

### Documentation
- [NumPy Random Sampling](https://numpy.org/doc/stable/reference/random/index.html)
- [Chart.js Documentation](https://www.chartjs.org/docs/latest/)
- [Yahoo Finance API](https://pypi.org/project/yfinance/)

### Related Projects
- [QuantLib](https://www.quantlib.org/) - Quantitative finance library
- [PyPortfolioOpt](https://pyportfolioopt.readthedocs.io/) - Portfolio optimization
- [Zipline](https://www.zipline.io/) - Backtesting library

---

## 📄 License

This project is licensed under the MIT License.

```
MIT License

Copyright (c) 2025 Florvil Occean

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 👤 Author

**Florvil Occean**
- GitHub: [@florvil1066](https://github.com/florvil1066)
- Email: florvil.occean001@mymdc.net

---

## 🙏 Acknowledgments

- **CAP4767 Course Staff** for assignment guidance
- **Yahoo Finance** for providing free historical data
- **Anthropic Claude** for AI-assisted development
- **Chart.js Team** for excellent visualization library

---

## 📞 Support

If you have questions or need help:

1. Check the Issues page on GitHub
2. Open a new issue with detailed description
3. Email: florvil.occean001@mymdc.net

---

## 🗺️ Roadmap

### Version 1.0 (Current)
- ✅ Monte Carlo simulation with 5-stock portfolio
- ✅ Interactive web application
- ✅ Risk assessment and recommendations
- ✅ Responsive design

### Version 2.0 (Planned)
- ⬜ Real-time data integration
- ⬜ Portfolio optimization algorithms
- ⬜ Options and derivatives pricing
- ⬜ Multi-asset class support (bonds, real estate)
- ⬜ User accounts for saving portfolios
- ⬜ Export reports to PDF

### Version 3.0 (Future)
- ⬜ Machine learning for return prediction
- ⬜ Social sentiment analysis integration
- ⬜ Automated rebalancing recommendations
- ⬜ Tax optimization strategies

---

## 📊 Performance Benchmarks

| Simulations | Execution Time | Memory Usage |
|-------------|----------------|--------------|
| 1,000 | ~0.5s | ~5MB |
| 10,000 | ~2.0s | ~15MB |
| 50,000 | ~8.0s | ~50MB |

*Tested on: Chrome 120, M1 MacBook Air, 8GB RAM*

---

## 🐛 Known Issues

- **Large simulations (>50K):** May cause browser lag on slower devices
- **Portfolio weight validation:** Sum may not exactly equal 100% due to floating point
- **Mobile experience:** Charts may be difficult to read on very small screens (<375px)

See the Issues page on GitHub for full list and solutions.

---

## ⭐ If You Find This Helpful

If you find this project helpful, please consider:
- Giving it a star on GitHub
- Sharing it with classmates
- Contributing improvements via pull requests

---

**Built with ❤️ for CAP4767 - AI-Driven Business Innovation**

*Last updated: November 5, 2025*

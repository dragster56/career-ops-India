# Career-Ops India 🇮🇳

**AI-powered job search pipeline — customized for Indian data roles (fresher)**

<p align="center">
  <em>Companies use AI to filter candidates. I gave myself AI to <strong>choose</strong> companies.</em><br>
  <em>Forked from <a href="https://github.com/santifer/career-ops">career-ops</a> by Santiago and customized for the Indian data job market.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Gemini_CLI-4285F4?style=flat&logo=google&logoColor=white" alt="Gemini CLI">
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/Brave-FB542B?style=flat&logo=brave&logoColor=white" alt="Brave">
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white" alt="Playwright">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT">
</p>

---

## What Is This

A personal fork of [career-ops](https://github.com/santifer/career-ops) — an AI-powered job search automation system. I've customized it for **entry-level data roles in India** as a fresher graduating in 2027.

### What I Changed

| Area | Original (EU/Senior AI) | My Fork (India/Fresher Data) |
|------|------------------------|------------------------------|
| **Target Roles** | Senior AI Engineer, LLMOps, AI PM | Data Analyst, Data Engineer, Data Scientist, ML Engineer, BI Analyst, Analytics Engineer |
| **Salary** | EUR 95K-130K | ₹3-8 LPA (INR, CTC-based) |
| **companies** | 45+ EU/US AI companies | 26 Indian companies (Mu Sigma, Fractal, Flipkart, Razorpay, CRED, Swiggy, Zomato...) |
| **Job Portals** | Greenhouse, Ashby, Lever | + Naukri, LinkedIn India, Instahyre, iimjobs, Wellfound, Hirist, Internshala |
| **Title Filter** | AI/ML/Platform/PM keywords | Data/Analytics/SQL/Python/Tableau/Power BI + fresher-friendly filters |
| **Seniority** | Senior, Staff, Principal | Fresher, Junior, Entry, Associate, Graduate, Trainee |
| **Salary Scoring** | EUR, market rate | INR/LPA, CTC vs in-hand, notice period, WFH scoring, tier-1 city premiums |
| **Interview Prep** | System design, AI architecture | SQL coding, Python/pandas, case studies, guesstimates, A/B testing, data viz |
| **Browser** | Chromium | Brave |

## Features

| Feature | Description |
|---------|-------------|
| **Auto-Pipeline** | Paste a URL → get evaluation + PDF + tracker entry |
| **6-Block Evaluation** | Role summary, CV match, level strategy, comp research, personalization, interview prep |
| **6 Data Archetypes** | Auto-detects Data Analyst / Data Engineer / Data Scientist / ML Engineer / BI Analyst / Analytics Engineer |
| **India Salary Scoring** | CTC vs in-hand breakdown, notice period scoring, WFH/hybrid scoring, tier-1 city premiums, ESOP evaluation |
| **Data Interview Prep** | SQL rounds, Python/pandas, case studies, guesstimates, business framing, A/B testing, data viz, take-home assignments |
| **India Company Context** | Interview patterns for analytics firms (Mu Sigma, Fractal), startups (Razorpay, CRED), MNCs (Accenture, Deloitte), SaaS (Freshworks, Zoho) |
| **ATS PDF Generation** | Keyword-injected CVs via Brave browser |
| **Portal Scanner** | 26 Indian companies + 7 job portals pre-configured |
| **Negotiation Scripts** | India-specific, INR-based, fresher-friendly |

## Indian Companies Tracked

### Analytics Pure-Play
Mu Sigma · Fractal Analytics · Tiger Analytics · LatentView Analytics · Sigmoid

### Startups
Zepto · Razorpay · CRED · Groww · PhonePe · Swiggy · Zomato · Meesho

### SaaS
Freshworks · Zoho

### Consulting / IT
ThoughtWorks India · Accenture India · Deloitte India

### E-Commerce
Flipkart · Meesho

### Job Portals
Naukri · LinkedIn India · Instahyre · iimjobs · Wellfound · Hirist · Internshala

## Quick Start

```bash
# 1. Clone
git clone https://github.com/dragster56/career-ops-India.git
cd career-ops-India && npm install
npx playwright install chromium

# 2. Check setup
npm run doctor

# 3. Edit your profile
# config/profile.yml  → your details, target roles, salary range
# cv.md               → paste your full resume
# portals.yml         → already configured for Indian companies

# 4. Start using (with Gemini CLI)
gemini
# Then: /career-ops scan
# Or paste a job URL directly
```

## How It Works

```
You paste a job URL or description
        │
        ▼
┌──────────────────┐
│  Archetype       │  Classifies: Data Analyst / Data Engineer / DS / ML / BI / Analytics Eng
│  Detection       │
└────────┬─────────┘
         │
┌────────▼─────────┐
│  A-F Evaluation  │  Match, gaps, comp research (INR/LPA), STAR stories
│  (reads cv.md)   │
└────────┬─────────┘
         │
    ┌────┼────┐
    ▼    ▼    ▼
 Report  PDF  Tracker
  .md   .pdf   .tsv
```

## Salary Scoring (India-Specific)

| Factor | How It's Scored |
|--------|----------------|
| **CTC vs In-Hand** | CTC includes PF (12%), gratuity, insurance. In-hand = ~70-80% of CTC |
| **Notice Period** | Immediate = +0.3, 30d = neutral, 60d = -0.1, 90d = -0.2 |
| **WFH/Hybrid** | Full remote = 5.0, Hybrid = 4.0, Full onsite = 3.0 |
| **City Premium** | Bangalore +20%, Mumbai +15%, Delhi-NCR +15%, Hyderabad +10% |
| **ESOPs** | Pre-Series A = ₹0, Series B-C = 10-20%, Late-stage = 30-50% of paper value |

### Fresher Salary Benchmarks (2026)

| Role | Average CTC | Top-Tier CTC |
|------|-------------|-------------|
| Data Analyst | ₹3-6 LPA | ₹5-8 LPA |
| BI Analyst | ₹3-5 LPA | ₹5-7 LPA |
| Data Engineer | ₹4-8 LPA | ₹6-12 LPA |
| Analytics Engineer | ₹4-7 LPA | ₹6-10 LPA |
| Data Scientist | ₹5-10 LPA | ₹8-15 LPA |
| ML Engineer | ₹5-12 LPA | ₹8-18 LPA |

## Interview Prep Modes

The system generates prep guides based on company type:

| Company Type | Interview Pattern |
|--------------|-------------------|
| **Analytics Firms** (Mu Sigma, Fractal, Tiger) | Aptitude → Case study/Guesstimate → Technical (SQL+Python) → HR |
| **Indian Startups** (Razorpay, CRED, Zepto) | Recruiter → SQL/Python live → Case study → Hiring manager → HR |
| **MNCs** (Accenture, Deloitte) | HackerRank → Technical → Case study → HR |
| **SaaS** (Freshworks, Zoho) | Online test → Technical → Domain → HR |

### Technical Rounds Covered
- SQL Coding (window functions, CTEs, joins, optimization)
- Python/Pandas (data manipulation, cleaning, merging)
- Case Studies & Guesstimates (MECE framework, metric diagnosis)
- Business Problem Framing (KPI definition, data scoping)
- A/B Testing (hypothesis, sample size, significance)
- Data Visualization (dashboard design, chart selection)
- Take-Home Assignments (EDA, insights, presentation)

## Project Structure

```
career-ops-india/
├── cv.md                        # My resume
├── config/
│   └── profile.yml              # My profile (data roles, INR salary)
├── portals.yml                  # 26 Indian companies + 7 portals
├── modes/
│   ├── _shared.md               # Scoring + 12 archetypes (6 AI + 6 data)
│   ├── _profile.md              # India salary scoring, negotiation scripts
│   ├── interview-prep.md        # Data-specific interview rounds
│   ├── oferta.md                # Single evaluation
│   ├── pdf.md                   # PDF generation
│   ├── scan.md                  # Portal scanner
│   └── ...                      # 14 modes total
├── data/
│   ├── pipeline.md              # Pending offers
│   ├── applications.md          # Tracker
│   └── scan-history.tsv         # Scan log
├── reports/                     # Evaluation reports
├── output/                      # Generated PDFs
├── templates/
│   └── cv-template.html         # ATS CV template
├── generate-pdf.mjs             # HTML → PDF (Brave browser)
├── check-liveness.mjs           # Job link checker (Brave browser)
├── scan.mjs                     # Zero-token API scanner
└── docs/                        # Setup & architecture guides
```

## Tech Stack

![Gemini CLI](https://img.shields.io/badge/Gemini_CLI-4285F4?style=flat&logo=google&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)
![Brave](https://img.shields.io/badge/Brave-FB542B?style=flat&logo=brave&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white)

- **Agent**: Gemini CLI with custom modes
- **PDF**: Playwright + Brave browser + HTML template
- **Scanner**: Playwright + Greenhouse/Ashby/Lever APIs + WebSearch
- **Data**: Markdown tables + YAML config + TSV batch files

## Credits

This project is a personal fork of [career-ops](https://github.com/santifer/career-ops) by [Santiago Ferreira](https://santifer.io). The original system — evaluation engine, PDF generator, scanner architecture, batch processing — is his work. I customized it for the Indian data job market.

## About Me

I'm Shourya Vardhan Singh — final-year B.E. (IT) student at UIET Chandigarh, Panjab University. I'm targeting data roles (Data Analyst, Data Engineer, Data Scientist) as a fresher in the Indian market.

**Projects:** Churn Prediction Web App (Python + FastAPI + React), Top 50 Indian Companies Dashboard (Python + AWS + Power BI), Sign Language to Text Conversion (MediaPipe + Neural Network)

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/dragster56)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shourya-vardhan-singh-1bb59515a)

## License

MIT — Same as the original [career-ops](https://github.com/santifer/career-ops).

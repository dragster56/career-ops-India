# Mode: interview-prep — Company-Specific Interview Intelligence

When the user asks to prep for an interview at a specific company+role, or when an evaluation scores 4.0+ and the user updates status to `Interview`, run this mode.

## Inputs

1. **Company name** and **role title** (required)
2. **Evaluation report** in `reports/` (if exists) — read for archetype, gaps, matched proof points
3. **Story bank** at `interview-prep/story-bank.md` — read for existing prepared stories
4. **CV** at `cv.md` + `article-digest.md` — read for proof points
5. **Profile** at `config/profile.yml` + `modes/_profile.md` — read for candidate context

## Step 1 — Research

Run these WebSearch queries. Extract structured data, not summaries. Cite sources for every claim.

| Query | What to extract |
|-------|-----------------|
| `"{company} {role} interview questions site:glassdoor.com"` | Actual questions asked, difficulty rating, experience rating, process timeline, number of rounds, offer/reject ratio |
| `"{company} interview process site:teamblind.com"` | Candid process descriptions, recent data points, comp negotiation details, hiring bar |
| `"{company} {role} interview site:leetcode.com/discuss"` | Specific coding/technical problems, system design topics, round structure |
| `"{company} engineering blog"` | Tech stack, values, what they publish about, technical priorities |
| `"{company} interview process {role}"` (general) | Fills gaps from above — blog posts, YouTube, prep guides, candidate write-ups |

If the company is small or obscure and yields few results, broaden: search for the role archetype at similar-stage companies, and note that intel is sparse.

**Do NOT fabricate questions.** If a source says "they asked about distributed systems," report that. Do not invent a specific distributed systems question. When generating likely questions from JD analysis, label them clearly as `[inferred from JD]` not sourced from candidates.

## Step 2 — Process Overview

```markdown
## Process Overview
- **Rounds:** {N} rounds, ~{X} days end-to-end
- **Format:** {e.g., recruiter screen → technical phone → take-home → onsite (4 rounds) → hiring manager}
- **Difficulty:** {X}/5 (Glassdoor avg, N reviews)
- **Positive experience rate:** {X}%
- **Known quirks:** {e.g., "pair programming instead of whiteboard", "no LeetCode, all practical", "take-home is 4 hours"}
- **Sources:** {links}
```

If data is insufficient for any field, write "unknown — not enough data" rather than guessing.

## Step 3 — Round-by-Round Breakdown

For each round discovered in research:

```markdown
### Round {N}: {Type}
- **Duration:** {X} min
- **Conducted by:** {peer / manager / skip-level / recruiter — if known}
- **What they evaluate:** {specific skills or traits}
- **Reported questions:**
  - {question} — [source: Glassdoor 2026-Q1]
  - {question} — [source: Blind]
- **How to prepare:** {1-2 concrete actions}
```

If round structure is unknown, state that and provide the best available intel on what types of rounds to expect based on company size, stage, and role level.

## Step 4 — Likely Questions

Categorize all discovered and inferred questions:

### Technical
Questions about system design, coding, architecture, domain knowledge.
For each: the question, source, and what a strong answer looks like for this candidate specifically (reference CV proof points).

### Behavioral
Questions about leadership, conflict, collaboration, failure.
For each: the question, source, and which story from `story-bank.md` maps best.

### Role-Specific
Questions tied to the specific job description (archetype-aware).
For each: the question, why they're likely asking it (what JD requirement it maps to), and the candidate's best angle.

### Background Red Flags
Questions the interviewer will probably ask about gaps, transitions, or unusual elements in the candidate's background. Read `_profile.md` and `cv.md` to identify what might raise questions.
For each: the likely question, why it comes up, and a recommended framing (honest, specific, forward-looking — never defensive).

## Step 5 — Story Bank Mapping

| # | Likely question/topic | Best story from story-bank.md | Fit | Gap? |
|---|----------------------|-------------------------------|-----|------|
| 1 | ... | [Story Title] | strong/partial/none | |

- **strong**: story directly answers the question
- **partial**: story is adjacent, needs reframing
- **none**: no existing story — flag for the user

For each gap, suggest: "You need a story about {topic}. Consider: {specific experience from cv.md that could become a STAR+R story}."

If the user wants to draft missing stories, help them build STAR+R format and append to `interview-prep/story-bank.md`.

## Step 6 — Technical Prep Checklist

Based on what the company actually tests, not generic advice:

```markdown
- [ ] {topic} — why: "{evidence from research}"
- [ ] {topic} — why: "{their blog/product suggests this matters}"
- [ ] {topic} — why: "{asked in N/M recent Glassdoor reviews}"
```

Prioritize by frequency and relevance to the role. Max 10 items.

## Step 6b — Data Role Technical Rounds (India-Specific)

**If the detected archetype is a data role (Data Analyst, Data Engineer, Data Scientist, ML Engineer, BI Analyst, Analytics Engineer), include these round-specific prep guides:**

### SQL Coding Round

Most data roles in India include a SQL assessment (live or HackerRank/Codility).

**Topics to prep (by frequency):**
- `JOIN` types (INNER, LEFT, FULL OUTER, CROSS) — understanding when to use each
- Window functions: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LAG()`, `LEAD()`, `NTILE()`
- CTEs (Common Table Expressions) and recursive CTEs
- Aggregations: `GROUP BY`, `HAVING`, conditional aggregates (`CASE WHEN` inside `SUM`/`COUNT`)
- Subqueries vs CTEs vs temp tables — trade-offs
- Query optimization: indexes, `EXPLAIN` plans, avoiding `SELECT *`
- Date functions: `DATEADD`, `DATEDIFF`, `DATE_TRUNC`, `EXTRACT`
- String manipulation: `LIKE`, `REGEXP`, `CONCAT`, `SUBSTRING`
- NULL handling: `COALESCE`, `NULLIF`, `IS NULL` vs `= NULL`

**Common patterns in Indian company SQL rounds:**
- "Find the Nth highest salary" (window functions)
- "Calculate running totals / moving averages" (window + frame)
- "Find duplicate records" (GROUP BY + HAVING)
- "Employee-manager hierarchy" (self-join or recursive CTE)
- "Month-over-month growth" (LAG + arithmetic)

**Prep resources:** StrataScratch, LeetCode SQL, HackerRank SQL, Mode Analytics SQL Tutorial

### Python / Pandas Round

Jupyter notebook live coding or shared-screen coding.

**Topics to prep:**
- **pandas basics:** `read_csv`, `head`, `info`, `describe`, `dtypes`
- **Data manipulation:** `merge`, `groupby`, `pivot_table`, `melt`, `stack`/`unstack`
- **Filtering:** boolean indexing, `.query()`, `.loc[]` / `.iloc[]`
- **Cleaning:** `fillna`, `dropna`, `replace`, `astype`, handling duplicates
- **String operations:** `.str.contains()`, `.str.split()`, `.str.extract()`
- **Datetime:** `pd.to_datetime`, `dt.year`, `dt.month`, `resample`
- **Vectorized operations:** avoid loops, use `apply` only when needed
- **NumPy:** array operations, broadcasting, statistical functions

**Common tasks:**
- "Clean this messy dataset and produce a summary"
- "Merge these 3 tables and compute a metric"
- "Handle missing values and outliers — justify your approach"
- "Write a function that processes X and returns Y" (think: reusable code)

### Case Study / Guesstimates Round

**Very common at Indian analytics firms (Mu Sigma, Fractal, Tiger Analytics, LatentView).**

**Formats:**
- **Metric diagnosis:** "Revenue dropped 15% last quarter — walk me through your analysis"
- **Funnel analysis:** "Conversion rate dropped from 3.2% to 2.1% — why?"
- **Guesstimate:** "How many Uber rides happen in Bangalore per day?"
- **Root cause analysis:** "Customer churn increased by 20% — diagnose"

**Framework (MECE approach):**
1. **Clarify** — Ask what metric, what time period, what segment
2. **Structure** — Break into mutually exclusive, collectively exhaustive buckets
3. **Hypothesize** — For each bucket, state a testable hypothesis
4. **Data needed** — What data would you pull to test each hypothesis?
5. **Recommend** — Based on findings, what would you do?

**India-specific patterns:**
- Analytics firms love guesstimates as warm-up (5-10 min)
- Case studies are 30-45 min and often include a dataset to analyze live
- Startups (Razorpay, CRED) blend case study with SQL — "here's a table, write the query"

### Business Problem Framing Round

**Common at product companies (Flipkart, Swiggy, Zomato, PhonePe).**

**What they test:**
- Translate a vague business problem into a structured data problem
- Define the right metric (KPI) to optimize
- Identify what data you'd need and how you'd collect it
- Scope the analysis — what's in vs out
- Communicate findings to non-technical stakeholders

**Example prompts:**
- "Swiggy wants to reduce delivery time. How would you approach this as a data analyst?"
- "Flipkart wants to improve seller rating accuracy. Design the analysis."
- "Product manager says 'we need a churn model' — what questions do you ask?"

### A/B Testing Round

**Common at product companies and data science roles.**

**Topics to prep:**
- Hypothesis formulation (H₀ and H₁)
- Test design: control vs treatment, randomization unit
- Sample size calculation (power analysis)
- Duration: how long to run the test
- Statistical significance: p-value, confidence intervals
- Common pitfalls: peeking, multiple comparisons, selection bias
- Guardrail metrics: metrics that must NOT degrade
- Post-hoc analysis: interpreting results, segment deep-dives

**Example questions:**
- "How would you test whether a new checkout flow increases conversions?"
- "Your A/B test shows p=0.06. What do you do?"
- "Two metrics conflict — conversion went up but revenue went down. Now what?"

### Data Visualization Round

**Common at BI Analyst and Data Analyst roles.**

**Topics to prep:**
- Choosing the right chart type (bar vs line vs scatter vs heatmap)
- Dashboard design principles: hierarchy, flow, interactivity
- Storytelling with data: insight → recommendation → action
- Tool-specific: Power BI DAX, Tableau calculations, Looker LookML
- Color theory: when to use color, accessibility considerations
- Avoiding chart junk: 3D charts, pie charts with 10+ slices, dual axes

**Common tasks:**
- "Here's a dataset. Build a dashboard in 30 minutes"
- "Present these findings to a VP of Sales"
- "Critique this dashboard — what would you change?"

### Take-Home Assignment

**Common at startups (Zepto, CRED, Meesho) and some analytics firms.**

**Typical format:**
- Receive a dataset (CSV/SQL dump) + 3-5 questions
- 48-72 hours to complete
- Submit Jupyter notebook + presentation deck
- Present findings in a 20-30 min follow-up call

**What they evaluate:**
- Code quality (clean, commented, reproducible)
- EDA thoroughness (distributions, missing data, outliers)
- Insight quality (not just describing data, but finding actionable patterns)
- Visualization quality
- Communication clarity in the presentation
- Statistical rigor (appropriate tests, correct interpretation)

### India-Specific Interview Context by Company Type

**Analytics Pure-Play (Mu Sigma, Fractal, Tiger, LatentView, Sigmoid):**
- 3-4 rounds: Aptitude → Case study/Guesstimate → Technical (SQL+Python) → HR
- Mu Sigma has a unique "problem-solving" round with ambiguous scenarios
- Fractal and Tiger often give take-home assignments
- LatentView: SQL heavy, dashboard design round

**Indian Startups (Razorpay, CRED, Zepto, Swiggy, Flipkart):**
- 3-5 rounds: Recruiter → SQL/Python live → Case study → Hiring manager → HR
- Focus on product sense + data intuition
- SQL questions are harder (window functions, optimization)
- May include system design for data pipelines (Data Engineer roles)

**MNCs & Consulting (Accenture, Deloitte, ThoughtWorks):**
- 3-4 rounds: Aptitude test → Technical (SQL+Python basics) → Case study → HR
- Accenture/Deloitte use HackerRank for initial screening
- ThoughtWorks has a unique pairing exercise (collaborative coding)
- MNCs may ask about tools: Power BI, Tableau, Excel advanced (VLOOKUP, pivot tables)

**SaaS Companies (Freshworks, Zoho):**
- 3-4 rounds: Online test → Technical → Domain knowledge → HR
- Zoho has its own proprietary test format
- Freshworks is more startup-like in its process

**Notice Period Negotiation in Interviews:**
- As a fresher, your biggest advantage is **immediate availability**
- Always mention "I can join within X days of offer acceptance"
- If asked about other offers, be honest but use it to show market validation

## Step 7 — Company Signals

Things to say, do, and avoid based on research:

- **Values they screen for:** name them, cite source (careers page, blog, Glassdoor reviews)
- **Vocabulary to use:** terms the company uses internally — shows homework (e.g., Stripe says "increase the GDP of the internet", Anthropic says "safety" not "alignment")
- **Things to avoid:** specific anti-patterns flagged in interview reviews
- **Questions to ask them:** 2-3 sharp questions that demonstrate you've researched the company, tied to recent news or blog posts discovered in Step 1

## Output

Save the full report to `interview-prep/{company-slug}-{role-slug}.md` with this header:

```markdown
# Interview Intel: {Company} — {Role}

**Report:** {link to evaluation report if exists, or "N/A"}
**Researched:** {YYYY-MM-DD}
**Sources:** {N} Glassdoor reviews, {N} Blind posts, {N} other
```

## Post-Research

After delivering the report:

1. Ask the user if they want to draft stories for any gaps found in Step 5
2. If they have a scheduled interview date, note it: "Your interview is in {X} days. Want me to set a reminder to review this prep?"
3. Suggest running `deep` mode if the company research in Step 1 was thin — deep mode covers strategy, culture, and competitive landscape in more depth

## Rules

- **NEVER invent interview questions and attribute them to sources.** Inferred questions must be labeled `[inferred from JD]`.
- **NEVER fabricate Glassdoor ratings or statistics.** If the data isn't there, say so.
- **Cite everything.** Every question, every stat, every claim gets a source or an `[inferred]` tag.
- Generate in the language of the JD (EN default).
- Be direct. This is a working prep document, not a pep talk.

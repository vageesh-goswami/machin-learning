
Here's a comprehensive breakdown of each step with detailed explanations and examples:

---

# ML Problem Framing — Complete Guide

## Why Problem Framing Matters

Problem framing is the **most critical first step** in any ML project. Get it wrong, and you'll spend months building the wrong system. Get it right, and everything else — algorithm selection, metrics, tuning — flows naturally.

> *"A well-framed problem is half-solved."*

---

## Step 1: Define the Business Objective

### What It Means
Building a model is **never** the end goal. You need to understand:
- What does the business actually want to achieve?
- How will the model's output be used?
- What downstream systems will consume this output?

### Why It's Critical
If you misunderstand the objective, you'll optimize for the wrong thing. A model that's technically accurate but doesn't drive business value is useless.

### Key Questions to Ask
1. What problem are we solving for the end user?
2. How does success look in business terms (revenue, retention, cost savings)?
3. Where does the model output go next?
4. Who are the stakeholders?

### Examples

| Domain | Surface-Level Goal | **True Business Objective** |
|--------|-------------------|----------------------------|
| **Netflix** | Predict movie ratings | Maximize user retention & watch time |
| **Amazon** | Recommend products | Increase average order value & purchase frequency |
| **Spotify** | Suggest songs | Keep users listening longer → reduce churn |
| **Uber** | Predict ride demand | Minimize wait times → improve user satisfaction |
| **Bank** | Detect fraud | Minimize losses while not blocking legitimate transactions |
| **Hospital** | Predict disease | Early intervention → better patient outcomes, lower treatment costs |

### Detailed Example: Swiggy/Zomato

❌ **Wrong framing:** "Predict what food user will order"

✅ **Correct framing:**
- **Business objective:** Maximize order completion rate and average order value
- **Downstream usage:** Model output feeds into:
  - Homepage restaurant ranking
  - Push notification timing
  - Discount/coupon targeting
- **Success metric:** ₹ increase in revenue per user per month

---

## Step 2: Determine the System Type

### What It Means
Categorize your problem along three dimensions:

#### Dimension 1: Learning Type
| Type | Definition | When to Use |
|------|------------|-------------|
| **Supervised** | Learn from labeled data (input → known output) | You have historical labels |
| **Unsupervised** | Find patterns in unlabeled data | No labels, need to discover structure |
| **Reinforcement** | Learn by trial and error with rewards | Sequential decisions, delayed feedback |
| **Semi-supervised** | Mix of labeled + unlabeled data | Labels are expensive to obtain |

#### Dimension 2: Task Type
| Task | Output Type | Examples |
|------|-------------|----------|
| **Regression** | Continuous number | Price prediction, rating prediction, demand forecasting |
| **Classification** | Discrete category | Spam/not spam, disease/healthy, fraud/legitimate |
| **Clustering** | Group assignment | Customer segmentation, document grouping |
| **Ranking** | Ordered list | Search results, recommendations |
| **Anomaly Detection** | Normal/abnormal | Fraud detection, network intrusion |

#### Dimension 3: Learning Mode
| Mode | How It Works | When to Use |
|------|--------------|-------------|
| **Batch Learning** | Train on entire dataset at once, deploy static model | Data doesn't change frequently |
| **Online Learning** | Update model incrementally with each new data point | Streaming data, need to adapt quickly |

### Detailed Example: Flipkart Product Recommendations

**Analysis:**
- **Learning type:** Supervised (we have purchase history as labels)
- **Task type:** Ranking (output is ordered list of products)
- **Learning mode:** Online (millions of new interactions daily)

**Alternative framings possible:**
1. **Regression:** Predict exact purchase probability (0.0 to 1.0)
2. **Classification:** Will user buy this? (Yes/No)
3. **Clustering:** Group similar users, recommend what similar users bought

**Best choice:** Ranking with online learning — because the goal is to show the *best* products first, not just predict purchase probability.

### Detailed Example: Ola/Uber Surge Pricing

| Dimension | Decision | Reasoning |
|-----------|----------|-----------|
| Learning type | Supervised | Historical demand data with labels |
| Task type | Regression | Predict continuous value (surge multiplier 1.0x to 3.0x) |
| Learning mode | Online | Demand changes by minute, need real-time adaptation |

---

## Step 3: Assess Current Solutions

### What It Means
Before building anything, understand:
- What solution exists today? (Even if it's manual)
- How well does it perform?
- What are its limitations?

### Why It's Critical
1. **Baseline:** Your ML model must beat this to be valuable
2. **Insights:** Current solution reveals edge cases and domain knowledge
3. **Feasibility:** If current solution works "well enough," ML might be overkill

### Types of Current Solutions

| Type | Example | What You Learn |
|------|---------|----------------|
| **Manual/Human** | Experts manually curating content | Human performance = upper bound for some tasks |
| **Rule-based** | If-else business rules | Edge cases already discovered |
| **Simple heuristics** | "Show most popular items" | Hard-to-beat baseline for cold-start |
| **Existing ML model** | Legacy model in production | Feature engineering insights |
| **No solution** | Problem currently unsolved | High potential impact but also high risk |

### Detailed Example: Email Spam Detection (Gmail)

**Historical progression:**

| Era | Solution | Performance | Limitation |
|-----|----------|-------------|------------|
| 1990s | Manual filtering | ~60% accuracy | Doesn't scale |
| 2000s | Rule-based (keyword matching) | ~75% accuracy | Easy to bypass ("V1@gra" instead of "Viagra") |
| 2010s | Naive Bayes classifier | ~90% accuracy | Can't handle image-based spam |
| Today | Deep learning + user feedback | ~99.9% accuracy | Still misses sophisticated phishing |

**Lesson:** Each new solution must significantly outperform the previous one. "Slightly better" isn't worth the engineering cost.

### Detailed Example: IRCTC Tatkal Booking Prediction

**Current solution:** First-come-first-serve, no prediction

**Proposed ML solution:** Predict which trains will sell out fastest, alert users

**Baseline to beat:** Random chance (~50% accuracy for binary "will sell out" prediction)

**Minimum viable improvement:** Must achieve >80% accuracy to be useful

---

## Step 4: Select a Performance Measure

### What It Means
Choose a metric that:
1. Aligns with business objective
2. Is measurable and trackable
3. Guides model optimization

### Common Metrics by Task Type

#### Regression Metrics
| Metric | Formula Intuition | When to Use |
|--------|-------------------|-------------|
| **MAE** (Mean Absolute Error) | Average of absolute differences | All errors matter equally |
| **MSE** (Mean Squared Error) | Average of squared differences | Large errors are much worse |
| **RMSE** (Root MSE) | Square root of MSE | Same unit as target variable |
| **MAPE** (Mean Absolute % Error) | Percentage-based error | Comparing across different scales |
| **R² Score** | Proportion of variance explained | Quick goodness-of-fit check |

#### Classification Metrics
| Metric | What It Measures | When to Use |
|--------|------------------|-------------|
| **Accuracy** | % correct predictions | Balanced classes only |
| **Precision** | Of predicted positives, how many correct? | False positives are costly (spam) |
| **Recall** | Of actual positives, how many caught? | False negatives are costly (disease) |
| **F1 Score** | Harmonic mean of precision & recall | Need balance between both |
| **AUC-ROC** | Ranking quality across thresholds | Comparing models, threshold-agnostic |

### Choosing the Right Metric — Decision Framework

```
Is your problem regression or classification?
│
├── REGRESSION
│   ├── Are outliers important? → Use MAE
│   ├── Are large errors much worse? → Use RMSE
│   └── Comparing across scales? → Use MAPE
│
└── CLASSIFICATION
    ├── Balanced classes? → Accuracy is fine
    ├── False positives costly? → Optimize Precision
    │   (Example: Spam filter — don't block real emails)
    ├── False negatives costly? → Optimize Recall
    │   (Example: Cancer detection — don't miss cases)
    └── Need balance? → Use F1 Score
```

### Detailed Example: Loan Default Prediction (Bank)

**Business context:**
- If bank gives loan to defaulter → loses ₹10 lakhs
- If bank rejects good customer → loses ₹50,000 in interest

**Analysis:**
- False Negative (miss a defaulter) = ₹10,00,000 loss
- False Positive (reject good customer) = ₹50,000 loss
- Cost ratio = 20:1

**Metric choice:** Optimize for **Recall** (catch maximum defaulters), but set a minimum Precision threshold to avoid rejecting too many good customers.

**Better approach:** Use **cost-sensitive learning** where you weight false negatives 20x more than false positives.

### Detailed Example: YouTube Video Recommendations

**Multiple metrics needed:**

| Metric | What It Measures | Target |
|--------|------------------|--------|
| Click-Through Rate (CTR) | Do users click recommendations? | >5% |
| Watch Time | How long do they watch? | >60% of video |
| Session Duration | Total time on platform | Maximize |
| Diversity | Are recommendations varied? | >70% unique genres |

**Why multiple metrics?** Optimizing only CTR leads to clickbait. Optimizing only watch time leads to addictive but low-quality content. Balance is key.

---

## Step 5: Check and Verify Assumptions

### What It Means
List every assumption you're making and verify each one. Wrong assumptions = wasted months.

### Common Dangerous Assumptions

| Assumption | Why It's Dangerous | How to Verify |
|------------|-------------------|---------------|
| "Data quality is good" | Garbage in = garbage out | Run data quality checks before modeling |
| "Labels are accurate" | Wrong labels = wrong model | Sample 100 labels, manually verify |
| "Distribution won't change" | Model degrades over time | Monitor production data drift |
| "More data = better model" | Diminishing returns | Plot learning curves |
| "Downstream team needs X output" | Might need Y instead | Talk to them directly |
| "Users will use this feature" | They might ignore it | Run A/B test |

### Verification Checklist

```
□ Data assumptions
  □ Is data representative of production?
  □ Are there missing values? How handled?
  □ Is there class imbalance?
  □ Any data leakage?

□ Label assumptions
  □ Are labels accurate?
  □ Is labeling consistent?
  □ Any label noise?

□ Feature assumptions
  □ Will these features be available at inference time?
  □ Any look-ahead bias?

□ Deployment assumptions
  □ What output format does downstream need?
  □ What latency is acceptable?
  □ How often should model retrain?

□ Business assumptions
  □ Will improving this metric actually help the business?
  □ Are there any ethical concerns?
```

### Detailed Example: Food Delivery Time Prediction (Swiggy)

**Initial assumptions:**
1. Restaurant prep time is constant → **WRONG** (varies by order complexity, time of day)
2. Traffic data is real-time → **WRONG** (15-minute delay in API)
3. Delivery partner accepts immediately → **WRONG** (average 3-minute delay for acceptance)
4. Customer wants exact ETA → **PARTIALLY WRONG** (range like "25-30 mins" reduces complaints)

**Impact of wrong assumptions:**
- Model predicted 25 mins
- Actual delivery took 40 mins
- Customer complained, gave 1-star rating
- Swiggy lost a loyal customer

**Corrected approach:**
- Add buffer time based on historical variance
- Predict a range, not exact time
- Under-promise, over-deliver

### Detailed Example: Resume Screening for Jobs

**Assumption:** Past hiring decisions are good labels for "good candidate"

**Reality check:**
- Historical data might be biased (gender, college name, etc.)
- Past hires might not actually be good employees
- Job requirements change over time

**Verification steps:**
1. Audit historical data for bias
2. Cross-reference with employee performance data
3. Have diverse team review model decisions
4. Implement human-in-the-loop for final decisions

---

## Putting It All Together — Complete Example

### Problem: Predicting Crop Yield for Indian Farmers

#### Step 1: Business Objective
- **Surface goal:** Predict crop yield
- **True objective:** Help farmers make better decisions → increase income → reduce loan defaults
- **Downstream usage:** 
  - Mobile app shows predicted yield
  - Banks use it for loan decisions
  - Government uses it for subsidy planning

#### Step 2: System Type
- **Learning type:** Supervised (historical yield data available)
- **Task type:** Regression (predict yield in kg/hectare)
- **Learning mode:** Batch (seasonal data, yearly retraining sufficient)

#### Step 3: Current Solution
- **Current:** Farmers estimate based on experience
- **Accuracy:** ~50-60% within 20% error margin
- **Limitation:** Doesn't account for weather anomalies, new seed varieties

#### Step 4: Performance Measure
- **Primary:** MAPE (Mean Absolute Percentage Error) — target <15%
- **Secondary:** R² Score — target >0.8
- **Business metric:** % of farmers who trust and use the prediction

#### Step 5: Verify Assumptions
| Assumption | Verification | Finding |
|------------|--------------|---------|
| Weather data available | Check IMD API | ✅ Available with 1-day lag |
| Soil data available | Check soil health cards | ⚠️ Only 40% farmers have it |
| Farmers have smartphones | Survey 500 farmers | ✅ 75% have smartphones |
| Farmers trust ML predictions | Focus groups | ⚠️ Need to show reasoning, not just numbers |

**Adjusted plan:** Include explainability features showing why prediction is what it is.

---

## Quick Reference Card

| Step | Key Question | Output |
|------|--------------|--------|
| 1. Business Objective | Why are we building this? | Clear success definition |
| 2. System Type | What kind of ML problem is this? | Algorithm family selection |
| 3. Current Solution | What are we replacing? | Baseline to beat |
| 4. Performance Measure | How do we know it's working? | Optimization target |
| 5. Verify Assumptions | What could go wrong? | Risk mitigation plan |

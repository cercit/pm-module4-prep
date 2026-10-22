# Module 4 revision guide (short version)

Exam: Saturday 31 Oct 2026, any start between 12:00 and 6:30 PM, 90 minutes, 10% weightage. Objective questions are +4 / −1, plus subjective questions. The mock and consolidated notes go up on the LMS by 27 Oct.

Syllabus: Academic Sessions 23–28. This guide covers only what the syllabus asks, using your class notes. Read this first. Open the full class notes only for a topic you're unsure of.

| Session | Syllabus title | Your notes folder | Taught live? |
|---|---|---|---|
| 23 | AI Foundations for PMs | Class 23 - Covered for Prof - AI PM | Yes |
| 24 | Re-imagining Products with an AI Lens | Class 24 - Looking products from AI lens | Yes (prompting) |
| 25 | AI Strategy, Research Acceleration & Responsible AI | Class 25 | Model choice live; responsible AI from the deck only |
| 26 | AI-Powered Ideation & PRD Drafting | Class 26 - Metrics and Prioritization | No. Metrics were taught instead |
| 27 | AI Product Teardown: Slack AI vs Microsoft Copilot | Class 27 - GitHub | No. GitHub was taught; Slack/Copilot is in the deck only |
| 28 | AI-Driven UX & Ethical AI Interfaces | Class 28 - AI Driven UX | Yes |

Watch out: the paper is set from the syllabus, not from what happened in class. Sessions 26 and 27 were taught as different topics, so sections 5 and 6 below matter more than their class time suggests.

---

## 1. AI, ML, deep learning and LLMs (Session 23)

**Learning objective:** explain AI, ML and LLMs in plain language and how they differ.

They nest inside each other, like boxes:

| Term | Plain meaning | Example |
|---|---|---|
| AI | Any machine doing a task we'd call intelligent. Includes hand-written rules | Spam filter built from rules |
| Machine learning | Learns patterns from data instead of following written rules | Credit score model, fraud detection |
| Neural network / deep learning | ML using layered networks; deep = many layers | Image recognition, speech-to-text |
| Generative AI | Creates new content: text, images, audio, code | ChatGPT, Midjourney |
| LLM | A generative model trained on huge text to predict the next token | GPT, Claude, Gemini |

Points the class stressed:
- **AI is bigger than GenAI.** Classification, recommendation and prediction solve many problems with no generation at all.
- **Start with the user problem, then pick the simplest method that works.** The Uber ETA example: predicting arrival time is a prediction problem. You don't need an LLM for it.
- **A transformer is an architecture, not a chatbot.** Don't use the two words as if they mean the same thing.
- Not every image model is an LLM, and GenAI is not only a part of NLP.

Three kinds of AI PM work (crawl → walk → run):
- **Crawl:** use AI to do PM work faster (research, drafts, analysis).
- **Walk, the AI PM:** build AI features. Pick the model, set guardrails, run evaluations.
- **Run, the AI-native PM:** build whole AI-first products or platforms.

The PM decides **what to build and why**. Engineering decides **how**. Example: switching to a cheaper model. The PM owns the requirement and the trade-offs, and engineers do the change.

AI work also needs **evaluation**: a set of expected answers (a "golden set"), traces, and error analysis. A demo that looks good is not proof.

---

## 2. Writing structured prompts (Sessions 23–24)

**Learning objective:** write clear prompts with the **Role–Context–Format** method.

| Part | Answers | Example |
|---|---|---|
| **Role** (persona) | Who should the model act as? | "You are a senior PM trainer" |
| **Context** | Who needs this, why, and with what data? | "For a first-time PM preparing for interviews; use the article below" |
| **Task** | What exactly to do | "Summarise new items since last Monday" |
| **Format** | Shape of the output | "3 sections: what changed, why it matters, what to do. Max 150 words" |
| **Tone** | How it should sound | "Plain, no jargon" |

Rules from class:
- **Context and persona are different.** Context answers who needs the work. Persona answers which role the model plays to do it.
- **Say where the information comes from and what to do if it can't be accessed.** In the TechCrunch exercise, "if you can't open the site, stop and say so" stops the model from making things up.
- **Fixed prompting:** user, role and rules are set in advance. Suits sensitive or controlled work.
- **Dynamic (adaptive) prompting:** the prompt asks who the user is and adjusts within allowed limits. Suits exploration.
- Neither type gives the model access to history, data or tools it doesn't have.
- **Prompt injection:** hidden instructions inside a document or web page ("ignore your instructions and…"). Always review source material and outputs for these.
- Simplified pipeline from class: prompt + guardrails → raw output → output checks → filtered output → evals run on that.

Good prompts give you **reliability** (the same kind of output every time), **scalability** (works for different users), **business alignment** (fits the real job) and **adaptability** (revisited as models change).

---

## 3. Re-imagining a product with AI (Session 24)

**Learning objective:** find where AI makes an existing product smarter, and propose features honestly.

A simple 4-step way to answer any "add AI to product X" question:
1. **Pick one user and one painful task**, for example "Swiggy user deciding what to order at 9 PM".
2. **Ask what AI can do there:** find, summarise, predict, recommend, generate, or act.
3. **Propose the feature and say why it would work.** Name the data it needs, and check the product already has that data.
4. **Do a reality check:** cost per use, delay, accuracy needed, what happens when it's wrong, privacy, and whether a simpler non-AI fix would do.

Use the **T-shaped skill** idea: broad knowledge across AI uses, and depth in one area. Knowing tool names isn't the same as being able to test a workflow.

---

## 4. AI strategy, model choice and responsible AI (Session 25)

### Build vs buy vs fine-tune
This wasn't completed live. Learn this standard version:

| Option | Choose when | Watch out for |
|---|---|---|
| **Buy / use an API** (OpenAI, Gemini, ready SaaS) | Common task, need speed, not your differentiator | Cost per call, data leaving your system, vendor lock-in |
| **Prompting + RAG** (give the model your own documents at query time) | Need answers from your own data that changes often | Retrieval quality; still not training |
| **Fine-tune** an existing model | Need a consistent style or format, or a narrow task where prompting falls short, and you have good labelled examples | Needs data, money and re-tuning; not required for every model switch |
| **Build your own model** | AI is the core product, you have unique data, and you have a big team | Most expensive and slowest; rarely right for a PM's feature |

Exam trap: **fine-tuning is not automatically needed** when you change models, and RAG is not just "pasting a paragraph".

### Choosing a model: the class's four levels
1. **Task fit.** Start from the user's task, not the newest model. One product can use different models for different tasks.
2. **Quality, latency, cost.** Test on real past cases with expected answers.
3. **Benchmarks.** Use only benchmarks that match your task. A public "intelligence score" doesn't tell you what's good enough for you.
4. **Decide, then keep monitoring.**

Latency terms:
- **TTFT** (time to first token): from start until the first text appears.
- **TTLT** (time to last token): from start until the answer is complete.
- **Output speed:** tokens per second.

Deck example: first token at 2 s and finish at 10 s, so 8 s of streaming.

Cost formula:
**Daily cost = requests per day × tokens per request ÷ 1,000,000 × price per 1M tokens.** Do it separately for input and output tokens, then add them.

Practice: 2M requests/day × 4,000 input tokens = 8,000M tokens/day. Divide by 1M and you get 8,000 "millions". At ₹X per million, the cost is 8,000 × X.

### AI for research
AI speeds up competitor and market research, but **you check the facts**. Ask for sources, open them, and treat any number without a source as a guess. Use AI to draft the research, and do the judging yourself.

### Responsible AI and red teaming (deck only, likely examined)
**Six principles:** fairness, reliability and safety, transparency, privacy, accountability, grounding (no hallucination).

**Red teaming:** organised attempts to make the system fail *before* users see it. The five attack types to know:

| Attack | What it tries | Expected safe behaviour |
|---|---|---|
| Jailbreak | Get past the safety rules | Refuse, explain |
| Prompt injection | Instructions hidden in data ("ignore previous instructions") | Treat data as data, not as commands |
| False premise / contradiction | "How many sides does a five-sided square have?" | Challenge the premise |
| Role-play disguise | Unsafe request wrapped in a story | Still refuse |
| Leakage | Reveal hidden system prompt or confidential data | Refuse |

**Five risk areas to track:** harmful content, jailbreaks, grounding/hallucination, privacy, copyright/IP. Each needs an owner, a guardrail, a review and a retest.

**Bias example:** a photo-tagging model made more errors on darker-skinned users because the training data was imbalanced. The fix starts with the data, not the model.

---

## 5. AI ideation and PRD drafting (Session 26: syllabus topic, not taught live)

**Learning objectives:** use AI to brainstorm features and find edge cases, then draft PRD sections with AI and correct them.

How to use AI for ideation:
- Give it the user, the problem and the constraints. Ask for **10 ideas, then the 3 riskiest assumptions** behind each.
- Ask specifically for **edge cases**: not logged in, already done, network drops, wrong input, misuse, accessibility.
- You choose the ideas. AI widens the list, and you narrow it with evidence.

How to draft a PRD with AI (the two-prompt method from the PRD workshop):
1. **Prompt 1:** "Here is the brief. Don't write the PRD yet. List what's missing to write the problem, goals and metrics."
2. Answer those gaps yourself.
3. **Prompt 2:** "Draft these sections using my skeleton. Mark guesses as [ASSUMPTION]."
4. **Review every [ASSUMPTION].** Accept it, correct it, or send it back to the stakeholder.

What to check in an AI-written PRD:
- Is the problem backed by evidence, or made up?
- Does every metric have a number and a timeframe?
- Are the out-of-scope items there?
- Do the acceptance criteria cover the happy path, the blocked path and the already-done path?
- Are there invented statistics or sources?

**Line to remember:** AI writes the first draft faster, but every assumption is still your decision.

What was actually taught in this slot (worth a quick look, it may come up): **AARRR** (acquisition, activation, retention, referral, revenue) · **HEART** (happiness, engagement, adoption, retention, task success) · North Star → drivers → guardrails · prioritising with MoSCoW, then impact/effort, then RICE · Kano.

---

## 6. Slack AI vs Microsoft Copilot (Session 27: syllabus topic, deck only)

**Learning objectives:** break down how each brought AI in, and compare **AI-added vs AI-native**.

**Slack AI** builds on its **work graph**: people, conversations, channels, files and projects. Its four verbs are **find, understand, create, act**. Typical use: you come back after two days to hundreds of unread messages, and AI summarises the decisions, updates and blockers with links to the source messages. The value is **less effort to catch up on context**.

**Microsoft 365 Copilot** works across Word, Excel, PowerPoint, Outlook, Teams, OneDrive and SharePoint. Typical use: preparing for a meeting by pulling together emails, calendar, documents and Teams chats; drafting a proposal in Word; explaining a revenue drop in Excel; making slides in PowerPoint. The value is **AI working inside the files and apps you already use**.

Both are **AI-added**: AI placed on top of a product people already use.

| | AI-added (Slack AI, M365 Copilot, Notion AI) | AI-native (ChatGPT, Perplexity, Claude, Cursor) |
|---|---|---|
| Starts from | An existing workflow | The user's intent, with AI at the centre |
| Users and trust | Already has users, data and distribution | Has to earn them |
| Design freedom | Limited by the old UI and architecture | Can redesign the whole flow |
| User habit | Extends a current habit | May need a new habit |
| Main risk | Feature parity, "bolted-on" AI | Reliability and adoption |
| Monetisation | Add-on to the existing plan | May need a new model |

Deck examples of the same task done both ways:
- **Slides:** pick a template and edit by hand (added) vs "make a 10-slide Q3 strategy deck", then review (native).
- **Music:** better playlists (added) vs "a 2-hour drive playlist that starts energetic and gets calmer, with no repeats" (native).

---

## 7. AI-driven UX and ethical interfaces (Session 28)

**Learning objectives:** explain how AI changes interfaces (adaptive and generated screens), and design AI experiences that are transparent.

**How AI changes interfaces:**
- **Adaptive content:** the same screen shows different content to each user, based on their behaviour.
- **Generative UI:** the interface is created on the spot for the request, for example a table or chart the AI builds for you.
- **Conversational intent:** users say what they want instead of clicking through menus.

**The three AI shifts and what UX must do about them:**
- Output can vary, so show the evidence and make correction easy.
- Answers take time, so show honest progress status.
- Conversational intent, so offer clear choices, changes the user can review, and control.

**The 8 AI UX principles (learn the list):**

| Principle | Means | Example |
|---|---|---|
| 1. Transparency | Show what AI did and why | Perplexity's citations |
| 2. Human in the loop | User reviews and approves | Editable Notion AI drafts |
| 3. Progressive disclosure | Show more depth only when asked | ChatGPT follow-ups |
| 4. Graceful failure | Explain the failure, keep the user's work, offer a retry | Gemini explaining a refusal |
| 5. Latency management | Stream the answer or show progress | Claude streaming its reply |
| 6. Permission / consent | Ask before acting | Copilot permission prompts |
| 7. Contextual memory | Remember useful context and let the user control it | Slack thread context |
| 8. Trust through design | Consistent, honest, predictable | Duolingo Max guided chat |

**Two separate checks.** A product can pass one and fail the other:
- **Intuitive:** easy to work out.
- **Non-intrusive:** doesn't interrupt the main task.

**UI vs UX:** UI is the surface (colour, fonts, buttons). UX is the whole task: entry → understand → request → wait → review → act → recover. It covers navigation, trust, efficiency, onboarding and failure.

**Ethical interface rules:**
- Never hide AI limitations to make the product feel "magic".
- Keep consent steps even when you're cutting friction.
- Watch for **sycophancy**, where the AI just agrees with the user.
- A copy or download isn't proof the answer was right.

**Redesign method:** watch a real user do the task → name one concrete problem → propose one change → pick one metric to prove it worked.

---

## 8. Exam technique (lessons from Module 3)

- **Subjective answers:** copy each sub-task as a heading (Task 1a, 1b…) and answer under it. Marks follow the rubric, not the quality of your thinking.
- **Multi-select:** missing one correct option scores −1. Before you tick, test **every** option as its own true/false.
- **Unit check before you calculate:** 1 crore = 100 lakh = 10,000,000. ₹18 crore ÷ 12 lakh users = **₹150**, not ₹1.5 lakh.
- **Easy percentages without a calculator:** 1,800 ÷ 20,000 → drop the zeros → 18 ÷ 200 = 9%.

## 9. Quick self-test (answers below)

1. Is a rule-based spam filter AI? Is it ML?
2. Name the parts of a Role–Context–Format prompt, and say how context differs from persona.
3. Product needs answers from company policy docs that change weekly: fine-tune or RAG?
4. Name the five red-teaming attack types.
5. Slack AI is AI-added or AI-native? Give one advantage and one risk.
6. What's the difference between TTFT and TTLT?
7. List the 8 AI UX principles.
8. A feature is easy to understand but pops up during checkout. Which check does it fail?

**Answers:**
1. AI yes, ML no. It follows written rules and doesn't learn from data.
2. Role, context, task, format, tone. Context is who needs the work and why. Persona is the role the model plays.
3. RAG. The data changes often, and fine-tuning doesn't keep facts current.
4. Jailbreak, prompt injection, false premise or contradiction, role-play disguise, leakage.
5. AI-added. Advantage: existing users and data. Risk: feels bolted on, or competitors match it easily.
6. TTFT is the time until the first text appears. TTLT is the time until the answer is complete.
7. Transparency, human in the loop, progressive disclosure, graceful failure, latency management, permission/consent, contextual memory, trust through design.
8. It's intuitive but fails non-intrusive.

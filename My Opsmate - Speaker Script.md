# My Opsmate — Speaker Script

**Role:** Senior AI Product Manager
**Audience:** Apple Supply Chain BPR leadership
**Duration:** ~30 minutes
**Purpose:** Propose the first version of an AI teammate for supply chain operations.

> Note: this script is spoken, not read. Slide text is *not* repeated verbatim — each section adds the reasoning, the trade-offs, and the process logic that the slide can't carry on its own.

---

### Slide 1 — Title · ~0.5 min

Good morning. I'm Ma Jing, and I'm here to propose the first version of an AI platform for supply chain operations. We're calling it "My Opsmate."

One sentence on what it is: an AI teammate that doesn't wait to be asked, but actively helps your planners and managers resolve exceptions faster. Over the next thirty minutes I'll take you from the problem, to the decision, to a ten-week plan you can actually evaluate — and I'll be explicit about my assumptions along the way, because for this team, the reasoning is as important as the recommendation.

---

### Slide 2 — Method · ~2 min

Let me start with how I think, because the method *is* the proposal — the recommendation is just the evidence.

I followed five steps. First, understand where the time actually goes. Second, score every candidate opportunity on value versus difficulty. Third, prove the winner with one concrete case. Fourth, translate the need into AI capabilities. Fifth, validate with a scoped MVP and a measurable gate. Notice what's *not* step one: technology. We'll get to the AI last, deliberately.

What I was given to work with matters here: enterprise LLMs, structured business data, a data warehouse, existing dashboards and reporting, and secure auth and permissions. I want to be clear that I'm not proposing to replace any of that stack. I'm proposing to layer on top of it — the platform sits on your warehouse, reuses your dashboards, and respects your permission model. For a BPR team, that's the difference between a process change you can adopt and one you'd have to fight to integrate.

One honest caveat up front: this is a hypothetical study. Every number I haven't sourced from an external benchmark, I've marked as my own estimate. I'd rather flag uncertainty than hide it — and I'll do that throughout.

---

### Slide 3 — Pain × data · ~2.5 min

So, step one: where does the time go? I mapped the seven manual activities your planners live with every day — searching for information across systems, coordinating with stakeholders, reading emails and reports, investigating issues, tracking action items, consolidating updates, and preparing management reports.

Two of these have hard external numbers. Searching consumes roughly nineteen to twenty percent of a planner's week — that's McKinsey. Coordinating runs two to four hours a day, from a planner workload study. The other five I estimated, conservatively, and marked them as estimates.

Now here's the point I want to leave with you, because it reframes everything. These seven are not seven separate problems. They're seven symptoms of one underlying process defect: **your SDP planners are the human integration layer.** Every time a plan changes or an exception fires, a person has to manually stitch together context that already exists in your systems — orders in one place, inventory in another, supplier commitments in a third. That stitching is pure waste. It's not analysis, it's not planning, it's not judgment. It's a person doing the work that the integration should already be doing. That's the process problem we're actually solving.

---

### Slide 4 — Scoring · ~2.3 min

So how do we decide which of these to attack first? Not by instinct — by scoring. This is where I turn the problem into a decision you can audit.

I scored every candidate on two axes. Value on the vertical — and value here is a composite: frequency times time spent, how standardizable the task is, business impact, measurability, and reuse across scenarios. Difficulty on the horizontal — is the data already structured, are the rules deterministic, how much human judgment is required, what's the compliance risk, and how hard is the integration into existing systems.

The result is this four-quadrant chart. The quick-win quadrant — high value, low difficulty — is where you want to play. What lands there is **exception resolution**: investigating, coordinating, and tracking a shortage from alert to closure. What deliberately does *not* land there is reading emails — it's unstructured, so it sits in the avoid quadrant for now, not because it's unimportant, but because it's the hardest to ground.

The reason I'm showing you the matrix rather than just telling you the answer: this prioritization is transparent and reproducible. You can argue with my scores — please do — and if you'd weight "business impact" higher or "integration cost" higher, the answer shifts in a way we can discuss openly. That's the discipline. It turns a subjective "I think this is important" into a scoring model we can both inspect.

---

### Slide 5 — Case · ~2.8 min

"Exception resolution" is a phrase until you see it, so let me make it concrete with one case.

The scenario: a part goes short for next week's build. A supply planner gets the alert, and they own it to closure. I broke that single exception into eight steps and timed it. Receive the alert — two minutes. Search across systems to rebuild context — twelve. Interpret what it means — eight. Find the owner — eight. Coordinate with stakeholders — twelve. Execute — two. Follow up — three. Report — three. Fifty minutes, end to end.

The insight is in the middle. The wedge — searching, interpreting, coordinating — is thirty-two of those fifty minutes. Sixty-four percent. That's not a planner doing planning. That's a planner acting as a manual API between your systems: reading from one, writing to another, holding the state in their head.

Now scale it. Roughly ten exceptions a week, fifty minutes each, across twenty planners — that's about a hundred and sixty hours a week on this single workflow. That's the equivalent of four full-time planners just doing context-reassembly and chasing.

And there's a second cost that doesn't appear in any time log but shows up on the P&L: the exceptions that *don't* get resolved in time. A missed allocation, a line stoppage, an expedited freight bill. The tail risk. So the value story is two-layered — the measurable hours we can save, and the costly misses we can prevent. For this team, the second one is usually the more persuasive number.

---

### Slide 6 — Prioritize · ~1.8 min

So the value is there. What do we build first, and why?

Three tiers. P-zero is exception-to-resolution — it's the wedge, it's the highest value, and it's feasible because the underlying data is already structured. P-one is the fast follow: a proactive morning brief, a drafted daily report, and surfacing the BI you already have — that's reuse, not new build. "Later" is natural-language query and management reporting — powerful, but they need the foundation to earn trust first.

The ordering logic is value, feasibility, and dependency. We build the most valuable and most buildable thing first, prove it works, then widen. That's the same discipline you'd apply to any process change: pilot the highest-leverage step before you reengineer the entire flow. Don't boil the ocean in the first quarter.

---

### Slide 7 — AI mapping · ~2.3 min

Now I'll translate those needs into capabilities. This is where a lot of AI proposals go wrong, because they jump straight to "a chatbot." We are not building a chatbot.

Look at the mapping. Rebuilding context across systems becomes context assembly — a structured query, not a guess. Reading emails becomes entity extraction — pulling part numbers, quantities, and dates out of messages. Deciding what's urgent becomes prioritization with rationale — an LLM plus rules. Drafting coordination becomes a communication draft, with a human approving before anything goes out. Follow-ups that stall become task tracking with a timeline. And the two things we're deliberately deferring: text-to-SQL and RAG.

The key architectural choice is **grounding**. For the MVP, everything the AI says is backed by structured data it can cite back to. That's what keeps a BPR team's confidence: the system is reviewable and auditable, not a black box. If it recommends an allocation change, it points at the inventory and the order that justify it. If it can't point at a source, it doesn't speak. That constraint is the single most important thing keeping this deployable in a risk-managed environment like yours.

---

### Slide 8 — Product form · ~1.5 min

So what does the teammate look like to a user? Four surfaces, one shared model underneath.

Today — proactive: "what needs my attention right now." Explore — the BI view, reusing the dashboards you've already invested in. Messages — exception tickets and tracking. Ask — natural-language query, which we're deferring.

The design principle that ties it together: proactive by default. The system reaches out with a brief and a recommended action, rather than sitting there waiting for someone to type a question. That matters for adoption — a tool you have to remember to open is a tool that gets abandoned by week two. And beneath all four surfaces, one shared task-and-context model, so the same fact appears consistently everywhere. One version of the truth, regardless of which surface you're looking at.

---

### Slide 9 — Core loop · ~2.2 min

Now the heart of it — the **end-to-end workflow** this thing runs. This is the process-reengineering part, so let me walk it carefully.

Six steps. Detect and group — signals roll up into a single exception. Assemble context — orders, inventory, owners, pulled from the systems that already hold them. Explain impact — what's affected, who's affected, how urgent. Recommend — the next best action, with the reasoning attached. Coordinate — a draft message, and here's the critical part: a human approves it before it goes anywhere. Track closure — follow up and close the loop.

Notice where the human sits. Not in the data-gathering, not in the context-assembly — those are the wasteful steps we're automating away. The human sits in judgment and approval. That's the reengineering insight: we're not removing the planner, we're removing the busywork and elevating the planner to the decisions that actually need them. The loop is designed so that every automated step is safe and reversible, and every judgment step is human. That's the line we will not cross — and it's the line that makes this a process improvement, not a risk.

---

### Slide 10 — Live demo · ~0.8 min

Rather than keep describing it, let me show it running.

This is the same loop, live. Here's the exception; here's the assembled context; here's the recommendation with its reasoning; and here's the approval step where the human stays in control.

I'll keep this brief — happy to do a deeper walkthrough in the questions.

---

### Slide 11 — MVP scope · ~2 min

Now, discipline. What ships first — and just as important, what doesn't.

In scope: P-zero exception-to-resolution, plus P-one — the daily brief, the report draft, and BI reuse. Explicitly out: a general-purpose chatbot, autonomous external communication, unsupervised write-back into your systems, and any cross-supplier data sharing. Deferred: Ask and management reporting.

Why this tight scope? Because scope creep is how AI projects die — and you've likely seen enough of those to know it. A tight, reviewable teammate in ten weeks beats a broad demo that never ships. Every "out" on this list is a fence we're putting up deliberately. I'd rather defend those fences now, on this slide, than explain a failed launch later. The "won't do" list is part of the proposal, not an afterthought.

---

### Slide 12 — 10-week plan · ~2 min

Here's how we'd build it. Five sprints, ten weeks, Scrum cadence.

Sprint one — weeks one and two — discover and baseline: we time the wedge, and pick the first exception type to automate. Sprints two and three — weeks three through six — build: context assembly, drafts, the P-zero loop end to end. Sprint four — weeks seven and eight — evaluate and harden: grounding, human approval, permissions. Sprint five — weeks nine and ten — pilot with a real planner cohort, measure time saved, and make a go/no-go call.

This is the MVP team — six people, deliberately lean: one product manager, one UI/UX designer, three engineers across backend, AI, and frontend, and one embedded planner. The embedded planner is non-negotiable — we're not building this in a vacuum, we're building it with the people who'll use it, so the process we design matches the process they actually run. And every sprint ends with a demo the planners can react to. That means course-correction is constant — not a surprise waiting for you at week ten. For a BPR team, that cadence should feel familiar; it's how you'd want any workflow change rolled out.

---

### Slide 13 — Metrics · ~2 min

How do we know it's working? Four ways, measured every sprint, reviewed at week ten.

First, business: time-to-resolution — target fifty minutes down to under twenty — and hours saved against that hundred-and-sixty-hour baseline. Second, user behavior: daily active planners, briefs read, drafts accepted. Because if people aren't actually using it, nothing else matters — adoption is the first leading indicator of value. Third, AI quality: grounding accuracy and draft acceptance rate — we're not just counting outputs, we're counting outputs that are correct and that people actually acted on. Fourth, safety: permission errors, write-back attempts blocked, escalation-to-human rate.

Those four together give a complete picture — value, adoption, quality, and risk. And they're measurable from week one, so the ten-week decision isn't a vibe check. It's a data-gated go/no-go, with thresholds we can agree on before we start.

---

### Slide 14 — Risks · ~2.2 min

Let me be upfront about what could go wrong, and what we're doing about each.

Hallucination — the classic AI failure mode. Our counter: structured query first, evidence links on every claim, human approval on every draft. If the system can't cite a source, it doesn't answer. Data quality — we only pick domains where the data is already structured and clean; we don't build on a shaky foundation and then blame the model. User trust — we graduate autonomy in stages: suggest, then draft, then act, and we never skip a stage. Scope creep — that explicit "won't do" list we just agreed on.

And one expectation to set clearly, because this is where AI proposals overpromise and lose credibility: this is a **coordination reducer**, not an autopilot. It does not replace human judgment. It removes the friction around it. If we hold that line, the risks are manageable. If we oversell it as "AI replaces planners," we fail — and honestly, we'd deserve to.

---

### Slide 15 — Closing · ~1.5 min

To close, the whole argument in one breath.

We started with seven pain points — two of them hard-measured — and scored every opportunity to find the one wedge that's both high-value and feasible: exception resolution. We quantified it: roughly a hundred and sixty hours a week across twenty planners. We translated it into grounded capabilities, shaped it as a proactive teammate with a human in the loop, scoped a tight MVP, and planned ten weeks to a data-gated pilot.

The through-line from start to finish is the same: value first, process second, technology last. The AI is the *last* thing we decided, not the first — and that's the sequence I'd recommend any BPR program follow. The workflow redesign is the point; the model is just the tool that makes it economical.

---

### Slide 16 — Thank you · ~0.5 min

Thank you.

I'd welcome your questions — and I'd especially invite pushback on the scoring, the scope, or the timeline. Those are exactly the conversations I'd want to have before committing a single sprint. Let's make it better before we make it real.

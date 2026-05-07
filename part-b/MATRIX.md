# Impact vs Effort Matrix

## The Matrix

|                   | Low Effort                                              | High Effort                                  |
|-------------------|---------------------------------------------------------|----------------------------------------------|
| **High Impact**   | Persistent Smart Train Filters                          | Tatkal Smart Queue System                    |
|                   | Responsive Mobile Booking Experience                    | Smart PNR Travel Dashboard                   |
|                   | Seat Preference Persistence System                      |                                              |
| **Low Impact**    | Guided TDR Refund Assistant                             |                                              |

---

## How I Scored Each Dimension

### Impact Scoring (1–5)

I scored Impact based on:
- Number of users affected (from Part A frequency analysis)
- Whether the issue occurs during the core booking journey
- Severity of user frustration and booking failure
- Frequency of occurrence on the live IRCTC platform

### Effort Scoring (1–5)

I scored Effort based on:
- Number of backend and frontend systems affected
- Need for new infrastructure or integrations
- Risk of disrupting existing booking systems
- Railway API dependencies and real-time data requirements

---

## Placement Justifications

### Tatkal Smart Queue System — High Impact / High Effort

This problem affects one of the highest-traffic flows on IRCTC and impacts thousands of users daily during Tatkal booking hours. Implementing a real-time queue system requires major infrastructure changes, session handling improvements, and live update mechanisms. Because it directly improves booking success rates for critical users, this feature should be treated as a long-term high-priority investment.

---

### Persistent Smart Train Filters — High Impact / Low Effort

Train filtering issues affect a large portion of users during regular train searches and create repeated friction in the booking process. Compared to other solutions, this feature mainly requires frontend state management improvements and search optimization rather than large infrastructure changes. Since it delivers immediate usability improvements with relatively lower engineering effort, it qualifies as a strong quick-win feature.

---

### Seat Preference Persistence System — High Impact / Low Effort

Seat preference reset issues negatively affect families, elderly passengers, and users with berth-specific needs during booking. The solution mainly involves improving session persistence and frontend booking state management rather than redesigning the entire booking engine. This makes the feature highly valuable while remaining relatively easier to implement safely.

---

### Responsive Mobile Booking Experience — High Impact / Low Effort

Mobile browser usability problems affect a large percentage of users because many passengers access IRCTC through smartphones. The solution focuses primarily on responsive frontend redesign, touch optimization, and modal behavior improvements without requiring deep backend restructuring. Since it improves usability across multiple booking flows with manageable development effort, it belongs in the high-impact, low-effort category.

---

### Smart PNR Travel Dashboard — High Impact / High Effort

The lack of contextual travel information affects passengers throughout their journey after booking completion. Implementing this feature requires integration with live railway systems, real-time train APIs, platform information systems, and notification services. Although technically complex, the feature significantly improves travel preparedness and user trust, making it a valuable long-term enhancement.

---

### Guided TDR Refund Assistant — Low Impact / Low Effort

The TDR refund issue affects a smaller subset of users compared to core booking problems, but still creates confusion and frustration during refund situations. The guided assistant mainly involves workflow redesign, simplified UI, and AI-assisted explanations without major booking infrastructure changes. While the feature improves transparency and accessibility, it is slightly lower priority because it affects fewer users than search and booking flows.

---

## Recommended Sprint Order

1. Persistent Smart Train Filters — Fast usability improvement with low implementation risk.
2. Responsive Mobile Booking Experience — Improves accessibility and booking experience for mobile users immediately.
3. Seat Preference Persistence System — Prevents booking frustration with relatively simple session handling improvements.
4. Tatkal Smart Queue System — Critical booking flow improvement requiring deeper infrastructure investment.
5. Smart PNR Travel Dashboard — Valuable contextual travel enhancement with higher integration complexity.
6. Guided TDR Refund Assistant — Improves refund transparency after higher-priority booking flows are stabilized.

---

## Peer Review Notes

During peer review discussions, the Responsive Mobile Booking Experience feature was confirmed as a strong High Impact / Low Effort solution because it improves usability across multiple booking flows without major backend infrastructure changes.

The Tatkal Smart Queue System remained in the High Impact / High Effort quadrant due to the complexity of implementing real-time queue management and handling peak-scale booking traffic.

No quadrant changes were required after review, but prioritization confidence improved based on feedback regarding usability impact and technical feasibility.

---
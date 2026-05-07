# AI Feature Specification: AI-Powered TDR Refund Assistant

## Problem It Solves

This AI feature addresses **Problem 6: TDR Refund Process Feels Like a “Black Box”** from Part A.

The current TDR refund system is difficult for users to understand because refund rules are presented in lengthy legal-style documents with technical railway terminology. Users struggle to determine refund eligibility, filing timelines, and refund outcomes, which creates confusion and uncertainty during the refund process.

## Proposed Feature — User Perspective

The AI-Powered TDR Refund Assistant simplifies the refund experience by guiding users through the refund process using conversational and easy-to-understand interactions.

When users open the refund section, they are shown a simple assistant interface where they can:
- Select their refund issue
- Describe what happened in plain language
- Upload ticket details or PNR number

The AI assistant then:
- Explains whether the user is eligible for a refund
- Summarizes the applicable refund rules
- Estimates refund timelines
- Guides the user through TDR filing step-by-step

Instead of reading complex PDF documents, users receive simplified explanations and actionable guidance directly inside the booking platform.

## Model or API Choice

### Selected Model:
OpenAI GPT-4 API

### Why GPT-4?

GPT-4 is well-suited for:
- Simplifying complex railway refund policies
- Understanding user-written refund descriptions
- Converting legal terminology into plain language
- Generating contextual guidance dynamically

Compared to rule-based chatbots, GPT-4 handles natural language much more effectively and provides flexible explanations for multiple refund scenarios.

## Training or Input Data

### Data Required:
- IRCTC refund rules and TDR policies
- Historical TDR request categories
- Refund processing timelines
- Railway cancellation policies
- User-entered refund descriptions
- PNR and booking information

### Data Sources:
- IRCTC refund policy database
- Railway Board refund rules
- Historical IRCTC refund records
- User booking and cancellation metadata

### Data Availability:
Most policy and booking data already exists inside IRCTC systems. Historical refund categorization data may require additional cleanup and structuring before model integration.

## How Output Is Shown to the User

The AI output appears as a guided refund assistant panel inside the refund section.

Example UI:

--------------------------------------------------

AI Refund Assistant

Issue Detected:
"Train delayed more than 3 hours"

Refund Eligibility:
Eligible for partial refund

Estimated Refund Timeline:
5–7 business days

Recommended Action:
File TDR before journey completion.

[File TDR Now]

--------------------------------------------------

The assistant also displays:
- Simplified refund summaries
- Required next steps
- Important deadlines
- Refund tracking progress

This assistant would connect directly to the proposed TDR wireframe from Part B.

## Confidence Threshold and Fallback

### Confidence Threshold:
The AI response is displayed only if confidence exceeds 85%.

### Fallback Behavior:
If confidence is low or the AI service becomes unavailable:
- The platform falls back to standard refund workflows
- Users are shown official IRCTC refund rules
- A manual refund category selection form appears instead

Fallback message example:

“AI guidance is temporarily unavailable. Please continue with the standard TDR filing process.”

## Success Metrics

- Reduce refund-related support requests
- Reduce TDR filing confusion
- Improve successful TDR completion rate
- Increase refund process satisfaction scores
- Reduce time spent reading refund policy documents

## Limitations and Risks

- AI may occasionally misinterpret complex refund cases
- Refund eligibility depends on official railway policies, which may change frequently
- Incorrect AI guidance could create user frustration if refunds are denied later
- Regional language variations may affect understanding
- Real-time railway policy synchronization is required to maintain accuracy

To reduce risk, all final refund approvals will continue to follow official IRCTC policy systems rather than AI-generated decisions.

---
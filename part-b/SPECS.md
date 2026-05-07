# IRCTC Feature Specifications — Part B

---

# Feature Spec 1: Tatkal Smart Queue System

## Problem Statement

In Part A, the Tatkal booking flow was identified as one of the most critical IRCTC pain points. During the 10:00 AM Tatkal rush, users experience crashes, freezing, failed payments, and sudden ticket unavailability due to extremely high traffic and lack of queue management.

## Current State (from Part A)

Currently, users repeatedly refresh the website during Tatkal opening hours. At the booking stage, the platform becomes unresponsive and users receive little or no feedback regarding booking progress, queue position, or retry expectations.

## Proposed Solution

Introduce a virtual Tatkal smart queue system. Instead of users constantly refreshing the website, they are automatically placed into a managed waiting queue with live progress tracking, estimated waiting time, and booking turn notifications.

## Proposed User Flow — Step by Step

1. User logs into IRCTC before 10:00 AM
2. User selects train and Tatkal quota
3. User clicks “Join Tatkal Queue”
4. System assigns queue number automatically
5. User sees live queue position and estimated wait time
6. Queue updates in real-time without page refresh
7. Booking form unlocks when user’s turn arrives
8. User completes passenger details and payment
9. Booking confirmation appears successfully

## Technical Implementation Plan

### System components affected:
- Booking engine
- Session management
- Queue management service
- Notification service

### New data requirements:
- Queue ID
- Queue timestamp
- Queue position
- Estimated wait time

### API changes:
- Queue enrollment endpoint
- Queue status endpoint
- Live queue polling API

### Frontend changes:
- Queue waiting screen
- Real-time progress tracker
- Retry handling UI
- Booking unlock indicator

### Third-party services (if any):
- WebSocket service for live updates

## Success Metrics

- Reduce Tatkal booking crashes by 70%
- Reduce excessive page refreshes
- Improve booking completion success rate
- Improve user satisfaction during Tatkal hours

## Edge Cases and Constraints

- Queue overload during peak demand
- Internet disconnect during waiting
- Railway infrastructure limitations
- Graceful fallback to normal booking flow if queue fails

---

# Feature Spec 2: Persistent Smart Train Filters

## Problem Statement

Part A identified that IRCTC train search filters behave inconsistently. Users applying filters such as Sleeper Class, Available Seats, or Morning Departure frequently see incorrect results or lose their filter selections after navigation.

## Current State (from Part A)

Currently, filters partially update results and reset unexpectedly when users navigate between pages. This forces users to repeatedly apply the same preferences during train search.

## Proposed Solution

Implement persistent smart filters that update results instantly while preserving user selections throughout the search session.

## Proposed User Flow — Step by Step

1. User searches trains between two stations
2. Train results load normally
3. User selects filters such as Sleeper Class or Available Seats
4. Results refresh dynamically
5. Selected filters remain visible as filter chips
6. User navigates between train details pages
7. Filters remain preserved automatically
8. User can clear all filters with one click

## Technical Implementation Plan

### System components affected:
- Search engine
- Filter management system
- Frontend search UI

### New data requirements:
- User filter preferences
- Session-based filter state

### API changes:
- Filter persistence endpoint
- Dynamic filtering API improvements

### Frontend changes:
- Sticky filter sidebar
- Filter chips
- Session-based state preservation
- Real-time result refresh

### Third-party services (if any):
- None

## Success Metrics

- Reduce filter reset complaints
- Improve train search completion rate
- Reduce repeated filter interactions
- Improve search usability ratings

## Edge Cases and Constraints

- Large result datasets
- Slow internet conditions
- Browser session expiration
- Backend caching limitations

---

# Feature Spec 3: Seat Preference Persistence System

## Problem Statement

Part A identified that berth selections frequently reset during booking flow, especially on mobile devices. Users selecting lower berths or preferred seating lose their choices unexpectedly.

## Current State (from Part A)

Currently, selected berth preferences disappear when the passenger details page reloads or navigation occurs between booking steps.

## Proposed Solution

Introduce persistent seat preference tracking that automatically saves and restores user-selected berth preferences throughout booking.

## Proposed User Flow — Step by Step

1. User selects train and class
2. Passenger details form opens
3. User selects berth preference
4. System saves preference instantly
5. User proceeds to next booking step
6. Selected berth remains visible
7. User receives confirmation indicator
8. Booking continues without resetting preferences

## Technical Implementation Plan

### System components affected:
- Booking flow
- Passenger session management
- Seat preference engine

### New data requirements:
- Saved berth preference
- Temporary booking session state

### API changes:
- Seat preference save endpoint
- Session restore endpoint

### Frontend changes:
- Saved preference indicator
- Auto-save interaction
- Mobile session persistence handling

### Third-party services (if any):
- None

## Success Metrics

- Reduce seat preference reset reports
- Improve booking completion rate
- Improve mobile booking usability
- Reduce repeated seat selection actions

## Edge Cases and Constraints

- Session timeout
- Train class changes
- Shared device booking conflicts
- Mobile browser refresh interruptions

---

# Feature Spec 4: Responsive Mobile Booking Experience

## Problem Statement

Part A identified major usability issues on mobile browsers where the calendar popup overlaps booking controls and advertisements interfere with interaction.

## Current State (from Part A)

Currently, the mobile website layout becomes cluttered during booking. Calendar modals overlap important controls and users struggle with accidental taps and blocked interactions.

## Proposed Solution

Redesign the mobile booking experience using responsive mobile-first layouts, simplified navigation, and optimized modal handling.

## Proposed User Flow — Step by Step

1. User opens IRCTC on mobile browser
2. Mobile-optimized homepage loads
3. User taps travel date field
4. Full-screen mobile calendar opens cleanly
5. Background interactions are disabled temporarily
6. User selects date easily
7. Booking controls remain accessible
8. User completes search smoothly

## Technical Implementation Plan

### System components affected:
- Mobile frontend UI
- Responsive layout engine
- Modal handling system

### New data requirements:
- Mobile viewport preferences

### API changes:
- None

### Frontend changes:
- Mobile-first responsive layout
- Full-screen calendar modal
- Improved spacing and touch targets
- Floating widget management

### Third-party services (if any):
- None

## Success Metrics

- Reduce accidental mobile taps
- Improve mobile booking completion rate
- Improve usability scores
- Reduce mobile bounce rate

## Edge Cases and Constraints

- Small screen devices
- Older mobile browsers
- Slow network environments
- Advertisement placement constraints

---

# Feature Spec 5: Smart PNR Travel Dashboard

## Problem Statement

Part A identified that the PNR Status page lacks contextual travel information such as platform number, coach position, delay alerts, and live running status integration.

## Current State (from Part A)

Currently, users only see basic booking status information and must visit separate railway services to check train delays or platform updates.

## Proposed Solution

Create a unified smart PNR dashboard that combines booking status with real-time train context and travel updates.

## Proposed User Flow — Step by Step

1. User opens PNR enquiry page
2. User enters PNR number
3. Smart dashboard loads automatically
4. Booking status appears
5. Platform number is displayed
6. Coach position appears visually
7. Delay alerts update live
8. User can tap “Track Train”
9. Journey information remains centralized

## Technical Implementation Plan

### System components affected:
- PNR enquiry system
- Live train tracking integration
- Notification system

### New data requirements:
- Platform allocation data
- Coach position data
- Live delay information

### API changes:
- Live train status API integration
- Platform information endpoint

### Frontend changes:
- Dashboard-style UI
- Live travel cards
- Delay notification banner
- Coach visualization

### Third-party services (if any):
- NTES live train API integration

## Success Metrics

- Reduce external train status searches
- Improve passenger preparedness
- Increase engagement on PNR page
- Improve travel information satisfaction

## Edge Cases and Constraints

- Platform last-minute changes
- Missing live train data
- API downtime
- Regional railway system inconsistencies

---

# Feature Spec 6: Guided TDR Refund Assistant

## Problem Statement

Part A identified that the TDR refund process feels confusing and inaccessible because refund rules are presented in dense legal-style documents without simplified guidance.

## Current State (from Part A)

Currently, users open lengthy PDF documents containing difficult refund terminology and receive no progress tracking after filing a TDR request.

## Proposed Solution

Introduce a guided refund assistant that explains refund eligibility step-by-step and provides transparent TDR tracking.

## Proposed User Flow — Step by Step

1. User opens refund section
2. User selects refund issue category
3. Guided refund assistant asks simple questions
4. Eligibility status appears clearly
5. User submits TDR request
6. Refund progress tracker becomes available
7. User receives status updates automatically
8. Refund completion notification is displayed

## Technical Implementation Plan

### System components affected:
- Refund management system
- TDR processing system
- Notification service

### New data requirements:
- Refund tracking status
- TDR stage progress
- Refund eligibility categories

### API changes:
- Refund tracker API
- TDR status endpoint

### Frontend changes:
- Step-by-step refund wizard
- Progress tracker timeline
- Simplified refund explanation cards

### Third-party services (if any):
- SMS or email notification service

## Success Metrics

- Reduce refund-related confusion
- Reduce support requests
- Improve TDR completion rate
- Improve refund transparency satisfaction

## Edge Cases and Constraints

- Delayed railway approval
- Refund disputes
- Partial refund situations
- Backend processing delays

---

# Peer Review Updates

## Overview

The top two feature specifications presented during peer review were:

1. Tatkal Smart Queue System
2. Responsive Mobile Booking Experience

Feedback focused on scalability, accessibility, fallback behavior, and handling edge-case failures during peak booking traffic.

---

## Update 1 — Tatkal Smart Queue System

### Feedback Received

Reviewers raised concerns about what happens if the queue system itself crashes or if users lose internet connectivity while waiting in the queue.

### Changes Added

- Added temporary queue recovery support using session-based restoration
- Added auto-reconnect handling for interrupted mobile internet sessions
- Added fallback booking mode if live queue services fail completely

### Updated Edge Cases

Additional edge cases added:
- Queue session expiration
- Duplicate queue entries from multiple tabs
- Mobile browser refresh during waiting period

### Updated Success Metrics

New metric added:
- Reduce duplicate queue refresh attempts by 80%

---

## Update 2 — Responsive Mobile Booking Experience

### Feedback Received

Reviewers pointed out accessibility concerns for elderly users and users with smaller screen devices.

### Changes Added

- Increased minimum touch target sizes for buttons and date selection
- Added accessibility-friendly spacing and simplified interaction zones
- Reduced floating widget interference during booking flow

### Updated Technical Plan

New frontend improvements added:
- Adaptive mobile spacing system
- Dynamic keyboard-aware form adjustments
- Mobile accessibility testing for low-resolution devices

### Updated Success Metrics

New metrics added:
- Reduce accidental mobile taps by 60%
- Improve mobile task completion speed

---

## Matrix Reconsideration

Based on peer review feedback, the Responsive Mobile Booking Experience feature was confirmed as a stronger “High Impact / Low Effort” solution because it improves usability across multiple booking flows without requiring major backend infrastructure changes.

The Tatkal Smart Queue System remained in the “High Impact / High Effort” quadrant due to infrastructure complexity and scalability requirements during peak booking traffic.

---
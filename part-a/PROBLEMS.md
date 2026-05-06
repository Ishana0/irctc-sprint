# IRCTC Problem Discovery — Part A

## Summary

- Total problems documented: 6
- Platform explored: irctc.co.in
- Devices used:
  - Desktop Chrome
  - Mobile Chrome

---

# Problem 1: Tatkal Booking Crashes at 10:00 AM [Given]

## What is broken

The IRCTC platform becomes extremely slow or crashes during Tatkal booking at 10:00 AM. Users experience loading issues, failed sessions, and sudden quota disappearance without feedback.

## Affected users

Daily Tatkal users, office workers, emergency travelers, students, and agents trying to book tickets quickly.

## Frequency

Occurs daily around 10:00 AM during Tatkal opening.

## Current flow — step by step

1. User opens IRCTC around 9:50 AM
2. User logs into account
3. User searches train route
4. User selects Tatkal quota
5. User enters passenger details
6. User waits for booking window to open
7. User clicks Book at 10:00 AM
8. Website becomes slow or freezes
9. Payment page fails to load
10. Ticket quota disappears

## Where exactly it breaks

Step 8:
The server fails to handle heavy traffic at Tatkal opening time, causing timeout and page freezing.

---

# Problem 2: Search Filters Do Not Work Reliably [Given]

## What is broken

Train search filters like sleeper class, available seats, and departure timing do not consistently update results.

## Affected users

Users searching for specific train preferences and availability.

## Frequency

Occurs frequently during normal train searches.

## Current flow — step by step

1. User searches trains between two cities
2. Train list appears
3. User applies Sleeper filter
4. Results partially update
5. User applies Available Seats filter
6. Some unrelated trains still appear
7. User clicks back
8. Filters reset automatically
9. User must reapply filters again

## Where exactly it breaks

Step 6:
The filtering logic does not refresh results correctly and resets state unexpectedly.

---

# Problem 3: Seat Selection Resets [Given]

## What is broken

Selected seat or berth preferences disappear during booking flow.

## Affected users

Passengers preferring lower berths, families, elderly travelers.

## Frequency

Common during booking flow, especially on mobile browsers.

## Current flow — step by step

1. User searches train
2. User selects class
3. User proceeds to booking
4. User opens berth preference
5. User selects lower berth
6. User clicks Continue
7. Passenger page reloads
8. Selected berth disappears
9. Default option gets selected

## Where exactly it breaks

Step 7:
The selected seat preference is not preserved between pages.

---

# Problem 4: Mobile Web Friction and Poor Responsive Experience [Self-Discovered]

## How I found it

While testing the IRCTC website on a mobile Chrome browser during train search flow.

## What is broken

The mobile browser experience is poorly optimized even though the website is technically responsive. Important UI elements overlap with each other, the date picker blocks surrounding content, and interaction becomes difficult on smaller screens. The calendar popup partially hides buttons and creates accidental taps.

## Affected users

Mobile browser users, elderly passengers, first-time users, and users with smaller screen devices.

## Frequency

Occurs very frequently on mobile browsers during ticket booking and train search flows.

## Current flow — step by step

1. User opens IRCTC website on a mobile browser
2. Homepage loads with the "Book Ticket" section
3. User taps the date input field
4. Calendar popup opens on the screen
5. The calendar overlaps surrounding UI elements
6. Parts of the interface become difficult to access
7. User struggles to scroll or tap correctly
8. Nearby advertisements and floating widgets interfere with interaction
9. User accidentally taps wrong areas or closes the calendar unintentionally
10. Train search flow becomes frustrating and slow

## Screenshot or description

Screenshot attached: `assets/screenshots/irctc-mobile.png`

The calendar popup overlaps nearby UI elements and partially blocks the lower section of the booking form. Floating advertisement widgets further reduce usable screen space, making date selection difficult on mobile devices.

## Where exactly it breaks

Step 5:

The responsive layout fails when the calendar modal opens. The popup is not properly optimized for smaller screens, causing overlap with important booking controls and creating interaction friction.

---

# Problem 5: PNR Status Page Lacks Real-Time Travel Context [Self-Discovered]

## How I found it

While exploring the PNR Status section on the Indian Railways Passenger Reservation Enquiry website after checking booking-related services.

## What is broken

The PNR Status page only displays basic booking information such as CNF, WL, or RAC status, but does not provide contextual travel information like platform number, coach position, train delay updates, or direct live running status integration. Users are forced to navigate to separate railway websites or services to gather important travel updates.

## Affected users

Passengers checking train status before travel, elderly users, first-time train travelers, and users traveling during delays or platform changes.

## Frequency

Occurs every time users check PNR details because the missing information is not integrated into the page.

## Current flow — step by step

1. User opens the Indian Railways enquiry website
2. User clicks on the "PNR Enquiry" tab
3. Passenger Current Status Enquiry page opens
4. User enters PNR number
5. User clicks the Submit button
6. Current booking status is displayed (CNF/WL/RAC)
7. User looks for train delay information
8. User searches for platform number or coach position
9. No live running status or contextual travel updates are shown
10. User must open another website or NTES separately to check real-time updates

## Screenshot or description

Screenshot attached: `assets/screenshots/pnr-information-gap.png`

The PNR enquiry page only contains a basic PNR input field and booking status functionality. There is no visible integration for platform number, live running status, delay alerts, or coach positioning information.

## Where exactly it breaks

Step 7:

The experience breaks when users need real-time travel context after viewing their booking status. The system provides isolated ticket information without integrating essential journey-related updates, forcing users to leave the platform and search elsewhere.

---

# Problem 6: TDR Refund Process Feels Like a “Black Box” [Self-Discovered]

## How I found it

While exploring refund and cancellation-related sections on the IRCTC platform and opening the Refund Rules document from the footer section.

## What is broken

The TDR (Ticket Deposit Receipt) refund process is highly confusing and difficult for regular users to understand. The refund rules are presented as a dense legal-style PDF document filled with technical railway terminology, making it hard for users to quickly understand eligibility, timelines, or refund outcomes. There is also no refund tracking or progress visibility after filing a TDR request.

## Affected users

Passengers applying for refunds due to missed trains, delays, failed journeys, ticket issues, or cancellation disputes — especially first-time users and elderly passengers.

## Frequency

Occurs whenever users attempt to understand refund eligibility or file a TDR request.

## Current flow — step by step

1. User visits the IRCTC website
2. User looks for cancellation or refund information
3. User scrolls to the footer section
4. User clicks on “Refund Rules”
5. A lengthy PDF document opens
6. User sees multiple pages of dense legal and policy text
7. Important refund conditions are difficult to locate
8. User struggles to understand TDR eligibility and timelines
9. User files a TDR request with uncertainty
10. No progress tracker or real-time status updates are provided afterward

## Screenshot or description

Screenshot attached: `assets/screenshots/tdr-refund-rules.png`

The Refund Rules page opens as a long PDF document containing complex legal-style text and policy tables without simplified explanations, visual guidance, or user-friendly navigation.

## Where exactly it breaks

Step 6:

The experience breaks when users encounter dense policy documentation instead of simplified refund guidance. The system prioritizes legal documentation over user comprehension, making the refund and TDR process feel unpredictable and inaccessible.

---
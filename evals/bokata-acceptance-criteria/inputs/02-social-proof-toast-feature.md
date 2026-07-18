<!-- Initiative: Social Proof Toast — Clip2Coach | Source: bokata-feature-mapper output (eval-2) -->

**Actors confirmed:**
- **Visitor**: Unauthenticated user on landing page or signup page. Primary target for the toast.
- **Authenticated User**: Coach already logged in. Must never see the toast.

**Discovery context confirmed:**
- Toast only shown when threshold conditions are met (fallback logic).
- One toast per session (sessionStorage-backed dedup).
- Never shown to authenticated users.
- Auto-dismiss after 8 seconds unless the visitor hovers (pauses timer).

## Feature: Visitor Views Social Proof Toast
<!-- ID: C2C-FEAT-a1b2 -->
**Purpose:** The visitor sees contextually timed social proof of platform activity on landing and signup pages, reinforcing their decision to register.

### User Task: View Toast on Landing Page
<!-- Task ID: C2C-TASK-c3d4 -->
The visitor arrives at the landing page and, after 4 seconds or reaching 40% scroll depth (whichever comes first), sees the social proof toast appear at the bottom-left with a slide-up animation.

### User Task: View Toast on Signup Page
<!-- Task ID: C2C-TASK-e5f6 -->
The visitor arrives at the signup page and immediately sees the social proof toast appear at the bottom-left, reinforcing their in-progress decision to register.

### User Task: Read Activity Message
<!-- Task ID: C2C-TASK-g7h8 -->
The visitor reads the copy displaying recent registrations and clips created, presented in their browser language (ES or EN) with a pulsing green dot indicating live activity.

### User Task: Dismiss Toast Manually
<!-- Task ID: C2C-TASK-i9j0 -->
The visitor clicks the × button to close the toast before the 8-second auto-dismiss timer completes.

### User Task: Pause Toast on Hover
<!-- Task ID: C2C-TASK-k1l2 -->
The visitor hovers over the toast, causing the auto-dismiss timer to pause so they can read the content without it disappearing.

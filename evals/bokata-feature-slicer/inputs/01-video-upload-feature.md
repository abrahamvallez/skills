<!-- Initiative: Video Upload with Mux Integration (Clip2Coach) | Source: bokata-feature-mapper output (eval-3) -->

**Actor:** Coach — primary actor (Coach Carlos persona); uploads, manages, and analyzes private training videos. No secondary actors in MVP scope.

**Relevant business rules (from Criteria Research):**
- Upload flow requires sufficient credits before proceeding; no credits = blocked with CTA to purchase.
- Plan cannot be changed after upload.
- Video download is not permitted.
- Videos up to 5GB, any Mux-supported format.
- Three pricing plans: Basic (20cr/1mo), Standard (30cr/1yr), Premium (60cr/1yr).

## Feature: Coach Uploads Video Content
<!-- ID: C2C-FEAT-b2c3 -->
**Purpose:** Upload a private training video directly to the platform with secure Mux storage, selecting a plan that defines storage duration and clip pricing.

### User Task: Verifies Credit Availability
<!-- Task ID: C2C-TASK-b2c4 -->
The coach confirms they have sufficient credits before starting an upload; if not, they are directed to purchase more credits.

### User Task: Selects Storage Plan
<!-- Task ID: C2C-TASK-b2c5 -->
The coach chooses one of the three pricing plans (Basic 20cr/1mo, Standard 30cr/1yr, Premium 60cr/1yr) based on their intended use of the video.

### User Task: Enters Video Metadata
<!-- Task ID: C2C-TASK-b2c6 -->
The coach provides the required video title and optional description and tags before submitting the upload.

### User Task: Uploads Video File
<!-- Task ID: C2C-TASK-b2c7 -->
The coach selects a video file (up to 5GB, any Mux-supported format) and initiates the direct upload to Mux, with the option to cancel in progress.

### User Task: Monitors Upload Progress
<!-- Task ID: C2C-TASK-b2c8 -->
The coach tracks the upload via a visual progress bar and estimated time remaining, and continues using the app while the upload runs in the background.

##### System Task: Processes Uploaded Video
**Trigger:** Upload to Mux completes successfully
The system deducts the plan credits from the coach's balance, initiates Mux transcoding (SD/HD/adaptive), generates thumbnails, and transitions the video status from "Procesando..." to "Listo" upon receiving the Mux processing webhook.

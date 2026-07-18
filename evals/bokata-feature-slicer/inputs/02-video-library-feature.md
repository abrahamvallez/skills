<!-- Initiative: Video Upload with Mux Integration (Clip2Coach) | Source: bokata-feature-mapper output (eval-3) -->

**Actor:** Coach — primary actor (Coach Carlos persona); manages their personal video library ("Mis Videos"). No secondary actors in MVP scope.

**Relevant business rules (from Criteria Research):**
- Video deletion is manual and does not refund credits.
- Plan change after upload is not permitted (so metadata edits never touch plan).
- Deleting a video with active clips must warn the coach before confirming.

## Feature: Coach Manages Video Library
<!-- ID: C2C-FEAT-c3d4 -->
**Purpose:** Browse, find, edit, and remove uploaded videos from the personal video library ("Mis Videos").

### User Task: Browses Video Collection
<!-- Task ID: C2C-TASK-c3d5 -->
The coach views all uploaded videos in a grid or list layout with thumbnails, status, plan, expiration date, and clip count per video.

### User Task: Filters Videos by Criteria
<!-- Task ID: C2C-TASK-c3d6 -->
The coach narrows the video list by status (Active/Processing/Expired), plan type, or upcoming expiration to find relevant videos.

### User Task: Sorts Video List
<!-- Task ID: C2C-TASK-c3d7 -->
The coach reorders the video list by date, duration, expiration, or name to suit their preferred browsing order.

### User Task: Searches Videos by Title or Tag
<!-- Task ID: C2C-TASK-c3d8 -->
The coach searches the library by title or tags to quickly locate a specific video.

### User Task: Updates Video Metadata
<!-- Task ID: C2C-TASK-c3d9 -->
The coach edits the video's title, description, or tags after upload (plan change is not permitted).

### User Task: Deletes Video
<!-- Task ID: C2C-TASK-c3da -->
The coach permanently removes a video before its expiration date, confirming via a modal, with a warning if active clips exist (credits are not refunded).

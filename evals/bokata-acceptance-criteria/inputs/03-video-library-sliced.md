<!-- Initiative: Video Upload with Mux Integration (Clip2Coach) | Source: bokata-feature-slicer output (eval-2, with_skill) chained from bokata-feature-mapper eval-3 -->

**Actor:** Coach — primary actor; manages their personal video library ("Mis Videos").

**Relevant business rules (from Criteria Research):**
- Video deletion is manual and does not refund credits.
- Plan change after upload is not permitted.
- Deleting a video with active clips must warn the coach before confirming.

## Feature: Coach Manages Video Library
<!-- ID: C2C-FEAT-c3d4 -->
**Purpose:** Browse, find, edit, and remove uploaded videos from the personal video library ("Mis Videos").

User Tasks: Browses Video Collection, Filters Videos by Criteria, Sorts Video List, Searches Videos by Title or Tag, Updates Video Metadata, Deletes Video.

---

# Vertical Slices: Coach Manages Video Library

## 💀 Walking Skeleton
*Goal: End-to-end connectivity and basic value. No bells and whistles.*

### User Task 1: Browses Video Collection
- [ ] **[Browses Video Collection]** Open Library on Tab Navigation: Coach taps "Mis Videos" to open the library -- (Task: Browses Video Collection)
- [ ] **[Browses Video Collection]** Fetch All Videos (No Pagination): The coach's full set of uploaded videos loads in one request -- (Task: Browses Video Collection)
- [ ] **[Browses Video Collection]** Compute Enrichment via Live Query: Each video's clip count and status/expiration are worked out fresh whenever the library is opened -- (Task: Browses Video Collection)
- [ ] **[Browses Video Collection]** Display as Simple List: Videos appear in a list showing thumbnail, status, plan, expiration, and clip count -- (Task: Browses Video Collection)

### User Task 2: Filters Videos by Criteria
- [ ] **[Filters Videos by Criteria]** Single Filter Dropdown (Status Only): Coach picks one status (Active/Processing/Expired) to narrow the list -- (Task: Filters Videos by Criteria)
- [ ] **[Filters Videos by Criteria]** Filter by Exact Status Match: Only videos matching the selected status remain visible -- (Task: Filters Videos by Criteria)
- [ ] **[Filters Videos by Criteria]** Filter Client-side on Loaded List: Filtering applies instantly to the already-loaded videos, no extra load time -- (Task: Filters Videos by Criteria)
- [ ] **[Filters Videos by Criteria]** Update List In-place: The visible list updates immediately to show only matching videos -- (Task: Filters Videos by Criteria)

### User Task 5: Updates Video Metadata
- [ ] **[Updates Video Metadata]** Edit Form with Title, Description, Tags (Plan Excluded): Coach opens a form to change title, description, and tags; plan is not shown or editable -- (Task: Updates Video Metadata)
- [ ] **[Updates Video Metadata]** Validate Editable Fields Only (Title Required, Plan Excluded): Coach must keep a non-empty, length-limited title; the form has no way to submit a plan change -- (Task: Updates Video Metadata)
- [ ] **[Updates Video Metadata]** Update Video Record Fields Directly: Saving updates the video's title, description, and tags -- (Task: Updates Video Metadata)
- [ ] **[Updates Video Metadata]** Update Card/List View Immediately: The library view reflects the new metadata right after saving -- (Task: Updates Video Metadata)

### User Task 6: Deletes Video
- [ ] **[Deletes Video]** Delete Button on Video Card: Coach taps a delete action on a video -- (Task: Deletes Video)
- [ ] **[Deletes Video]** Check Clip Count and Flag Warning: The system checks whether the video has active clips and prepares a warning if so -- (Task: Deletes Video)
- [ ] **[Deletes Video]** Basic Confirm Modal: Coach sees a Yes/No confirmation, including a warning if active clips exist and a note that credits are not refunded -- (Task: Deletes Video)
- [ ] **[Deletes Video]** Hard Delete Video Record: Confirming permanently removes the video from the coach's library -- (Task: Deletes Video)
- [ ] **[Deletes Video]** Synchronous Mux Asset Deletion Call: The underlying video asset is removed from the video processing/storage provider as part of the same deletion -- (Task: Deletes Video)

---

## 🏗️ Increments Backlog
*Select and prioritize these increments manually to build upon the Walking Skeleton.*

### User Task 2: Filters Videos by Criteria
- [ ] **[Filters Videos by Criteria]** Multiple Filter Dropdowns (Status, Plan, Expiration): Independent filter controls for each criterion -- (Enhances: Step 1)
- [ ] **[Filters Videos by Criteria]** Filter by Multiple Criteria (AND Logic): Combine status, plan, and expiration filters together -- (Enhances: Step 2)

### User Task 6: Deletes Video
- [ ] **[Deletes Video]** Block Deletion if Clips Are In Active Use: Prevent deletion entirely (not just warn) if clips are actively referenced elsewhere, e.g. a published playlist -- (Enhances: Step 2)
- [ ] **[Deletes Video]** Soft Delete with Recovery Window: Mark as deleted with a grace period before permanent removal -- (Enhances: Step 4)

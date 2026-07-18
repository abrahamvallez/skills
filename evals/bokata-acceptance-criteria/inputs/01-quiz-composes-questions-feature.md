<!-- Initiative: Clip2Coach — Desacoplar el Quiz del Clip (FASE 1) | Source: bokata-feature-mapper output (eval-1) -->

**Actor:** Coach — the registered user who creates quizzes.

**Discovery context confirmed:**
- Answer options are multiple-choice (standard quiz format).
- A quiz question requires at least two answer options.
- Exactly one answer option must be marked correct.

## Feature: Coach Composes Quiz Questions
<!-- ID: C2C-FEAT-003 -->
**Purpose:** The Coach writes the quiz question and defines the set of answer options that responders will see.

### User Task: Writes Quiz Question Text
<!-- Task ID: C2C-TASK-008 -->
The Coach types the question text that will be shown to responders at the selected video moment.

### User Task: Adds Answer Options
<!-- Task ID: C2C-TASK-009 -->
The Coach adds multiple answer options (at least two) for the question, one of which will be the correct answer.

### User Task: Marks Correct Answer
<!-- Task ID: C2C-TASK-010 -->
The Coach designates which of the answer options is the correct one, enabling automatic result feedback for responders.

### User Task: Edits or Removes Answer Option
<!-- Task ID: C2C-TASK-011 -->
The Coach modifies the text of an existing answer option or removes it entirely if it is incorrect or no longer needed.

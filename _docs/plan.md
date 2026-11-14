# Weekly Project Feedback Tool: v1 Plan

## 1. Purpose
A lightweight tool where team members give weekly feedback on their own project. Results are shared with the team as an anonymous aggregate.

## 2. Users and Roles
- **Primary user:** team members giving feedback on their own project.
- **Project creator:** any logged-in user can create a project. The creator alone manages the roster, questions, and week start day.
- **Team member:** anyone on a project's roster. Submits feedback and views results.

## 3. Core Features

### 3.1 Accounts and Access
- Login with **email + password** (includes registration, password reset, basic account security).
- Access to a project is limited to users on the **roster set by the project creator**.
- One web link per project.

### 3.2 Project Setup (creator only)
- Create a project (name, description).
- Manage the roster (add/remove members).
- Define feedback questions:
  - Rating questions, with the **scale chosen per question** (e.g. 1-5 numeric, emoji, agree/disagree).
  - One open text box.
- Choose the **week start day** for the project.

### 3.3 Submitting Feedback
- Web app only, via the project link.
- A submission = answers to the rating questions + one open text comment.
- A member may **submit multiple times per week; the latest submission replaces earlier ones**.

### 3.4 Results View
- Shows the **latest week only**: scores per question + anonymized comments.
- Visible to the whole team **instantly** as responses come in.
- Mixed scale types must be rendered appropriately per question.

## 4. Anonymity Model
- The team never sees who submitted what.
- Internally, submissions must be linked to a user (e.g. via a hashed ID) so a resubmission can replace the earlier one.
- **Known risk:** instant reveal on small teams makes early responders identifiable (e.g. the first submitter's scores are the whole aggregate). To be revisited.

## 5. Out of Scope for v1
- Reminders or notifications of any kind
- Trend charts / historical views
- Slack/Teams/email integrations
- SSO (Google, Microsoft, SAML)
- Auto-generated summaries

## 6. Chosen Tech Stack
- **Frontend:** React web app.
- **Backend:** Node.js API.
- **Database:** PostgreSQL.

## 7. Open Questions
- Which React and Node.js frameworks/libraries to use.
- How to implement authentication and instant results updates.
- Anonymity safeguards: minimum response threshold, comment attribution risks.
- Edge cases: members leaving mid-project, roster changes, weeks with no responses, week-start changes mid-project.
- Success metrics: how we will know the tool works (e.g. weekly participation rate).

## 8. Suggested Next Steps
1. Define the data model (users, projects, roster, questions, submissions, weeks).
2. Decide anonymity safeguards for small teams.
3. Choose frameworks and libraries for the React app and Node.js API.
4. Build the MVP: auth, project setup, submission form, results view.
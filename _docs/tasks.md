# MVP Backlog

## 1. Set up the empty application and a passing test
Goal: Create a runnable React frontend and Node.js API backed by PostgreSQL, with at least one passing automated test.
Description: Choose the minimal frameworks, package structure, and test tools for this stack, then initialize the frontend and API without product features. Document how to run the application and test, and verify the test passes from a clean setup.

## 2. Create the core PostgreSQL data model
Goal: Add a versioned database schema for accounts, projects, rosters, questions, weekly submissions, and answers.
Description: Define tables, relationships, and constraints for project ownership, roster membership, configurable rating questions, and feedback answers. Include each project's week-start setting and internal submission ownership needed to replace a member's prior submission without exposing that identity in results.

## 3. Implement account registration and sign-in
Goal: Let users register and securely sign in and out with an email address and password.
Description: Implement password hashing, session management, and protected API access, with the necessary React screens. Test successful registration and sign-in, invalid credentials, sign-out, and rejection of unauthenticated access.

## 4. Implement password reset
Goal: Let users securely recover access to an account when they forget their password.
Description: Add a time-limited password-reset flow that does not reveal whether an email address has an account. Provide the required user interface and tests for valid, expired, and invalid reset links.

## 5. Create and manage projects
Goal: Let an authenticated user create a project and manage its name, description, and week-start day.
Description: Implement the project API and creator-facing React screens for creating a project and editing these settings. Enforce creator-only changes and test unauthorized access as well as valid updates.

## 6. Manage project rosters
Goal: Let project creators add and remove members and limit project access to the roster.
Description: Implement roster management for existing accounts and enforce membership checks on project feedback and results. Test that only the creator can change the roster and that users outside the roster cannot access project data.

## 7. Configure feedback questions
Goal: Let project creators manage rating questions with per-question scales and one open-text prompt.
Description: Implement the API and React interface to create, edit, order, and remove rating questions, including each question's scale definition. Support one open-text prompt per project and enforce creator-only configuration.

## 8. Submit and replace weekly feedback
Goal: Let roster members submit ratings and a text comment, with their latest submission replacing earlier submissions for that project week.
Description: Build the submission API and React form using the project's configured questions and scales, and validate answers against them. Define and test week boundaries using the project's chosen start day, including boundary times, and ensure a resubmission replaces only that member's submission for that week.

## 9. Decide the MVP anonymity policy
Goal: Agree on when aggregate scores and comments may be shown without making early responders identifiable.
Description: Choose and document the minimum response threshold and comment disclosure rules, including how the app handles weeks below the threshold and potentially identifying comment content. Keep the policy focused on the plan's risk of instant results revealing individual responses on small teams.

## 10. Show anonymous latest-week results
Goal: Let roster members view policy-compliant aggregate scores and comments for the latest week.
Description: Implement the results API and React view to aggregate each question's answers and render them using that question's scale. Return no submitter identities or individual submissions, apply the agreed anonymity policy, and handle weeks with no responses or too few responses.

## 11. Update results as feedback arrives
Goal: Make policy-compliant aggregate results update for roster members as new feedback is submitted.
Description: Add authorized live updates to the results view using a mechanism appropriate for the chosen stack. Send only permitted aggregate results, apply the same roster and anonymity rules as the results view, and test that unauthorized users receive no updates or individual response data.

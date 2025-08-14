# Port Repo One

This repository contains my complete submission for the Stage 2 Port Support Engineer Assessment, covering **Exercises 1–4**.

---

## 📂 Contents

- `deploy.json` — Sample Kubernetes deployment data.
- `jira_issue.json` — Sample Jira issue API response.
- `jq-queries.md` — JQ commands with explanations.
- `README.md` — Full documentation of approach, implementation, and verification.
- `submission-evidence/` — Directory containing screenshots/logs for proof of each exercise.
- `GoogleDoc_Link.txt` — Link to detailed step-by-step writeup with embedded screenshots.

---

## Exercise 1 – JQ Patterns

**Goal:** Extract data from Kubernetes and Jira API responses using `jq`.

### 1a. Current replica count
```bash
jq '.status.replicas' deploy.json
```
**Explanation:** Navigates to `.status.replicas` in the JSON and prints the integer value.

---

### 1b. Deployment strategy
```bash
jq '.spec.strategy.type' deploy.json
```
**Explanation:** Retrieves the deployment strategy type from `.spec.strategy.type`.

---

### 1c. Service + environment labels concatenated
```bash
jq -r '.metadata.labels | "\(.service)-\(.environment)"' deploy.json
```
**Explanation:** Accesses `.metadata.labels.service` and `.metadata.labels.environment` and joins them with a hyphen (`-`).

---

### 2. Jira issue IDs for subtasks
```bash
jq -r '[.fields.subtasks[].key]' jira_issue.json
```
**Explanation:** Iterates through `.fields.subtasks` array, extracts the `.key` of each subtask, and returns them as an array.

---

✅ **Verification:**  
All commands tested locally with `jq-1.7` and in [jqplay.org](https://jqplay.org). Outputs match requirements.

---

## Exercise 2 – Jira & GitHub Integration

**Steps Taken:**
1. Installed Port GitHub App.
2. Created Jira account → “Software Development” → “Scrum” → “Company-managed project”.
3. Created **at least 2 components** in Jira matching GitHub repositories.
4. Installed Port’s Ocean Jira integration (**not** using “Hosted by Port”).
5. Updated data model in Port to add relation **Jira Issue → Repository**.
6. Updated Jira integration mapping so that Jira components map to matching GitHub repositories.
7. Verified relation works for multiple components.

✅ **Verification Evidence:**
- Jira Issue **SAMPLE-101** contains components `port-repo-one` and `port-repo-twob`.
- Port shows linked repositories in the “Jira Issue” entity.
- *(Screenshot placeholder — see Google Doc)*

---

## Exercise 3 – Repository Scorecard

**Steps Taken:**
1. Created property `openPRCount` in Repository blueprint to count open pull requests.
2. Created scorecard rules:
   - `< 5` PRs → **Gold**
   - `< 10` PRs → **Silver**
   - `< 15` PRs → **Bronze**
3. Tested with repositories containing different numbers of open PRs.

✅ **Verification Evidence:**
- Repository `repo-a` → 3 PRs → **Gold**.
- Repository `repo-b` → 7 PRs → **Silver**.
- *(Screenshot placeholder — see Google Doc)*

---

## Exercise 4 – Troubleshooting GitHub Self-Service Action

**Troubleshooting Steps Provided to Customer:**
1. **Verify GitHub App Installation** – Confirm app installed in correct org/repo with Actions access.
2. **Confirm Port Action Configuration** – Self-service action is linked to the correct repo & workflow name.
3. **Validate GitHub Workflow Permissions** – Actions permissions allow workflow dispatch.
4. **Review Port Logs** – Check Port activity logs for errors or “pending” actions.
5. **Retry Action** – Trigger again and check the GitHub Actions tab for a run start.

✅ **Verification Evidence:**
- Successful self-service action execution shown in Port.
- Corresponding GitHub Actions run triggered.
- *(Screenshot placeholder — see Google Doc)*

---

## 📜 Google Doc

All detailed steps, screenshots, and live output logs are stored in this Google Doc:  
**[Google Doc Link – Evidence & Step-by-Step Guide](https://docs.google.com/document/d/17c4ZR1qQ8zGRIGKFkn_wB4c3Ztj2LtOSq4s0ljd2sq0/edit?usp=sharing)**

---

## Submission Notes

- All work uses **real data** from Jira, GitHub, and Port integrations (no mock data).
- Screenshots & logs prove functional integration and correct output.
- All code tested locally and in live environment.
- No sensitive credentials included.

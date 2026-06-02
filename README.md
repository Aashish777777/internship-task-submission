# Internship Task Submission

**Name:** Admin  
**Date:** June 2, 2026

---

## Task 1 - QA & Debug Report

### What I did
- Tested the RealWorld demo application (https://demo.realworld.io)
- Executed main user flows: Sign up, Login, Create article, Edit article, Delete article, Logout
- Found 5 issues including functional bugs, UX problems, and missing validation

### Issues Found
| Severity | Issue |
|----------|-------|
| High | No confirmation when deleting article |
| Medium | Can sign up with invalid email |
| Medium | Password visible as plain text |
| Medium | Session expires without warning |
| Low | No loading indicator on form submit |

### Root Cause Analysis
I analyzed the delete confirmation issue. The root cause is missing a confirmation dialog before calling the delete API. The fix would add a JavaScript confirm() dialog that only proceeds with deletion after user confirmation.

**Deliverable:** Task1_QA_Report_Admin.pdf

---

## Task 2 - n8n API Integration Workflow

### APIs Used
- **Primary API:** JSONPlaceholder (https://jsonplaceholder.typicode.com/posts)
- **Why:** Free, no authentication required, returns clean JSON data

### Transformation Logic
- Code node takes the first 5 items from 100 total posts
- Extracts only: id, title, body (truncated to 100 characters)

### Conditional Branch
- IF node checks: `id > 3`
- **True branch:** Items with id 4 and 5
- **False branch:** Items with id 1, 2, and 3

### Error Handling
- HTTP Request node has **"Continue"** selected under On Error
- If the API fails, the workflow continues instead of crashing

### Output
- Currently uses No Operation nodes for demonstration
- In production, these would connect to Email/Slack/Discord/Google Sheets

### How to Test
1. Import Task2_Workflow_Admin.json into n8n
2. Click "Execute Workflow"
3. All nodes show green checkmarks
4. Click IF node to see true/false branches

**Deliverables:**
- Task2_Workflow_Admin.json
- Task2_Canvas.png
- Task2_Output.png

---

## Files Submitted

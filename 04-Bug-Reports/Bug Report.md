# Bug Reports

## Project Information

| Field            | Value                         |
| ---------------- | ----------------------------- |
| **Project**      | MeetMind AI                   |
| **Tester**       | Bashir Ahmed                  |
| **Testing Type** | API + Exploratory Testing     |
| **Tool**         | Postman                       |
| **Environment**  | Local Development Environment |

---

# BUG-MEET-001

## AI Assistant Request Fails Due to Missing Backend Route

| Field            | Details                                                 |
| ---------------- | ------------------------------------------------------- |
| **Bug ID**       | BUG-MEET-001                                            |
| **Title**        | AI Assistant request fails due to missing backend route |
| **Module**       | AI Assistant                                            |
| **Severity**     | High                                                    |
| **Priority**     | High                                                    |
| **Status**       | Confirmed                                               |
| **Testing Type** | Exploratory Testing                                     |

### Description

While using the MeetMind AI application normally, a request was submitted through the AI Assistant.

Instead of receiving an AI-generated response, the application displayed a routing-related error.

Further backend investigation showed that the required API route for the AI Assistant request was missing/not registered.

### Steps to Reproduce

1. Log in to MeetMind AI.
2. Open the AI Assistant.
3. Enter a normal user question.
4. Submit the question.
5. Observe the response.

### Expected Result

The AI Assistant should process the request and return an appropriate AI-generated response.

### Actual Result

The request failed with a routing error because the required backend route was missing.

### Root Cause

The backend did not contain/register the API route required by the AI Assistant request.

### Impact

The AI Assistant functionality could not complete the expected request-response workflow.

### Evidence

Recommended evidence:

```text
05-Evidence/
└── BUG-MEET-001-AI-Assistant-Missing-Route/
    ├── ai-assistant-error.png
    ├── route-investigation.png
    └── corrected-response.png
```

### Classification

**Confirmed application defect.**

---

# Previously Investigated Issue — Meeting Summary 404

## Status: Not a Defect

During an earlier testing session, the following endpoint returned `404 Not Found`:

```http
GET /api/v1/meetings/{meeting_id}/summary
```

The initial response suggested that the meeting summary endpoint might have been defective.

However, further investigation showed that the backend queue worker required for AI processing and summary generation was not running during that test.

The required command was subsequently started:

```bash
php artisan queue:work --queue=transcription,ai -v
```

The meeting was tested again after the queue worker was running.

### Retest Result

The AI processing completed successfully and the meeting summary was generated and retrieved correctly.

### Final Classification

**Not a confirmed defect.**

### Cause

Local backend/queue processing was not running during the original test.

### Testing Lesson

When testing asynchronous functionality, the required background workers must be running before classifying an API failure as an application defect.

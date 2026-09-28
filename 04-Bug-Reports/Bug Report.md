# API Bug Report

## Bug ID

`BUG-MEET-001`

## Related Test Case

`TC-MEET-005 — Meeting Summary`

## Summary

Meeting Summary endpoint returns `404 Not Found` even after the meeting's AI processing has completed.

## Endpoint

```text
GET /api/v1/meetings/{meeting_id}/summary
```

## Preconditions

* API server is running.
* User is authenticated with a valid Bearer token.
* Meeting exists.
* Meeting transcript has been processed.
* AI processing status is completed.
* Valid meeting ID is available.

## Steps to Reproduce

1. Create a meeting.
2. Process the meeting transcript.
3. Wait until the AI processing status becomes completed.
4. Send a `GET` request to:

   ```text
   /api/v1/meetings/{meeting_id}/summary
   ```
5. Observe the response.

## Expected Result

The API should return `200 OK` and provide the generated meeting summary.

Example:

```json
{
  "message": "Meeting summary retrieved successfully.",
  "data": {
    "summary": "..."
  }
}
```

## Actual Result

The API returns:

```text
404 Not Found
```

The generated meeting summary cannot be retrieved even though AI processing has completed.

## HTTP Status

Expected: `200 OK`

Actual: `404 Not Found`

## Severity

`High`

**Reason:** Meeting summarization is a core AI feature of MeetMind AI. If the summary has been successfully generated but cannot be retrieved through the API, users cannot access an important application feature.

## Priority

`P1`

## Evidence

```text
../05-Evidence/BUG-MEET-001-meeting-summary-404.png
```

## Status

`Open`

## Notes

The issue should be investigated to determine whether the problem is related to:

* Summary record creation.
* Meeting-to-summary relationship.
* Summary retrieval query.
* Meeting ID/model binding.
* AI processing completion state.
* Route/controller logic.
* Database record availability.
* Authorization or resource lookup.

> Never include passwords, access tokens, refresh tokens, API keys, or other secrets in the bug report or evidence.

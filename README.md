# ApplySent MCP server

ApplySent lets an AI assistant search jobs that fit your résumé, show you exactly what an application would send, and apply on the employer's own form, one job at a time, only after you say yes.

**Endpoint:** `https://applysent.com/api/mcp` (remote, Streamable HTTP, OAuth 2.1 sign-in)
**Registry name:** `com.applysent/applysent` on the [Official MCP Registry](https://registry.modelcontextprotocol.io)
**Website:** [applysent.com](https://applysent.com) · operated by Osmium Labs

> **Every application needs your approval.** There is no bulk or autopilot applying over MCP. `apply_to_job` only works with the single-use `confirmation_token` from `preview_application` for that one job, after you have reviewed the preview and said yes in the conversation. The token expires after 10 minutes.

## Connect

Add it as a remote MCP server in any client that supports Streamable HTTP and OAuth:

```json
{
  "mcpServers": {
    "applysent": {
      "type": "streamable-http",
      "url": "https://applysent.com/api/mcp"
    }
  }
}
```

- **Claude:** Settings → Connectors → Add custom connector → paste the URL.
- **ChatGPT, Cursor and others:** add a remote/custom MCP server with the same URL.

On first use your client opens an ApplySent sign-in page. You need an ApplySent account; a 7-day trial is available (card required). Plans and limits are on [applysent.com/pricing](https://applysent.com/pricing). You can see and revoke connected assistants in ApplySent under Settings → Assistants.

## What it can do (35 tools)

**Find jobs**
- `search_jobs`: search jobs that match your résumé and filters, best match first
- `search`, `fetch`: search and read jobs in the format assistants use for citations
- `get_job`, `get_jobs`, `get_job_from_link`: read one job, several jobs, or a job from its posting link
- `list_saved_jobs`, `set_job_saved`: list, save or unsave jobs
- `set_job_feedback`: skip a job or bring it back
- `list_blocked_companies`, `set_company_blocked`: hide or restore a company

**Apply (one job at a time, with your OK)**
- `preview_tailored_resume`, `approve_tailored_resume`, `regenerate_tailored_resume`: see, approve or redo the résumé tailored for a job
- `preview_application`: show what applying would send; sends nothing
- `apply_to_job`: send one application after you said yes to that preview
- `queue_application_for_review`: prepare an application for review in ApplySent; sends nothing
- `cancel_application`: stop an application before sending starts
- `answer_question`, `list_pending_questions`: answer questions an employer form asked that only you can answer

**Track**
- `list_applications`, `get_application`, `get_application_board`, `get_application_review`, `get_application_receipt`: status of each application and the receipt of exactly what was sent
- `get_metrics`: application metrics
- `list_inbox`, `get_message`, `get_thread`: employer emails linked to your applications
- `list_notifications`, `mark_notification_opened`, `get_notification_settings`, `update_notification_settings`

**Account**
- `get_account`: plan and usage
- `get_profile_status`: whether your profile is ready to apply

Every tool carries a title and read-only/destructive annotations. ApplySent applies on the employer's own form on [12 hiring systems](https://applysent.com/supported-ats) (Workday, Greenhouse, Lever, Ashby and more), not through LinkedIn Easy Apply or Indeed.

## Privacy and support

- Privacy policy: [applysent.com/privacy](https://applysent.com/privacy)
- Terms: [applysent.com/terms](https://applysent.com/terms)
- Help centre: [applysent.com/help](https://applysent.com/help)
- Support: support@applysent.com

This repository holds the public listing and documentation for the hosted server. The server itself is operated by ApplySent and is not self-hostable.

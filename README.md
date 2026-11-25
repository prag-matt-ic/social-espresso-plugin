# Social Espresso Operations

Ask which events are coming up, which confirmed bookings still need a barista or grinder, and who is available to cover them. The plugin bundles two skills and connects your agent to the Operations calendar over MCP. Calendar access uses your own Social Espresso account.

## Set up in cloud ChatGPT

Cloud setup has two parts. Connect the calendar first, then upload the workflow skills. If you already have a working **Social Espresso Operations** connection, go straight to part 2.

### 1. Connect the Operations calendar

Open [ChatGPT Plugins](https://chatgpt.com/plugins) and choose **Add → Add custom MCP server**. Select **Server URL** and keep **Authentication** set to **OAuth**.

| Field | Value |
| --- | --- |
| Icon | [Download the 256 × 256 Operations icon (PNG)](https://raw.githubusercontent.com/prag-matt-ic/social-espresso-plugin/main/assets/operations-icon.png) |
| Name | Social Espresso Operations |
| Description | Review the Social Espresso calendar and preview changes to staff and equipment assignments. Editors and admins can save changes after written approval in chat. |
| Server URL | `https://operations.socialespresso.co.uk/api/mcp` |

Open **Advanced OAuth settings**. Once discovery finishes, keep the discovered endpoints and choose **User-Defined OAuth Client**. Leave the client secret blank and set the token endpoint auth method to **none**.

| Field | Value |
| --- | --- |
| Client ID | `931a9bd8-9cab-40bf-88a1-4cedcb37f6ac` |
| Default scopes | Select only `email` |
| Base scopes | Enter `email` |

Review the notice, tick **I understand and want to continue**, then choose **Create as a plugin**. If ChatGPT asks you to confirm, choose **Connect Social Espresso Operations**. Sign-in should start automatically. Sign in with your Operations email if prompted, then choose **Allow access** to approve the connection.

### 2. Upload the two workflow skills

1. Open [ChatGPT Plugins](https://chatgpt.com/plugins) and choose **Add → Upload plugin archive**. Choose **click to upload**, select the [Social Espresso Workflows ZIP](https://raw.githubusercontent.com/prag-matt-ic/social-espresso-plugin/main/assets/social-espresso-workflows.zip) and choose **Add plugin**.

## Codex in the ChatGPT desktop app

1. Open **Plugins** in ChatGPT desktop and add the GitHub marketplace `https://github.com/prag-matt-ic/social-espresso-plugin`. Install **Social Espresso Operations**. If you already have v0.2.0, refresh the marketplace and check the installed version before testing.
2. Select the plugin in a new Codex chat and ask **“What events are on this week?”**
3. When ChatGPT offers **Connect** or a sign-in link for **operations**, open it on the same computer. Use your Operations email, complete sign-in and approve access. Return to the chat and repeat the question if needed.

The calendar is live. A reply listing the two installed skills only confirms the package is present. If there is no connection action, open the installed plugin details and check for a sign-in prompt. If it is missing there too, report your plugin version and what ChatGPT displayed. If sign-in was cancelled, start a fresh connection attempt. Each attempt has its own link.

## Install in Codex CLI

```sh
codex plugin marketplace add prag-matt-ic/social-espresso-plugin
codex plugin add social-espresso@social-espresso
```

**Every calendar change requires your explicit written approval in chat after you see the proposed changes.** You can approve all listed jobs or name a subset.

The calendar skill can also list weekly branding quantities, venue addresses, missing machine allocations, machines booked abroad today, and the full week’s setup, service and breakdown schedule.

## Try a weekly staffing review

1. **“Summarise next week’s events.”** You’ll see service dates, booking statuses and staffing or equipment gaps. [Calendar summary skill](skills/summarise-events/SKILL.md)
2. **“Assign staff and equipment to confirmed jobs only.”** Review the proposed barista and equipment for each job. You can change a selection or narrow the list. [Assignment skill](skills/plan-job-assignments/SKILL.md)
3. **“Approve all four”** or **“Approve the Tuesday booking only.”** Use the count or names from your preview. The agent saves each approved proposal and reads the job again. Newly booked baristas start unconfirmed. A proposal expires after 15 minutes, and a changed booking or competing reservation can require a new review.

## Connection and permissions

The desktop plugin connects to the hosted Operations calendar at `https://operations.socialespresso.co.uk/api/mcp`. Each teammate signs in with their own Operations account. Full-calendar viewers, editors and admins can query jobs, staff and equipment. Staff-scoped accounts have no plugin access.

Assignment previews and saves require an editor or admin account and a server that exposes both change tools. If your connection offers only reads, you can still review staffing and equipment gaps.

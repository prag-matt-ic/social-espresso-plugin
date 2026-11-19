# Social Espresso Operations

Ask which events are coming up, which confirmed bookings still need a barista or grinder, and who is available to cover them. The plugin bundles two skills and connects your agent to the Operations calendar over MCP. Calendar access uses your own Social Espresso account.

## Install in Codex

```sh
codex plugin marketplace add prag-matt-ic/social-espresso-plugin
codex plugin add social-espresso@social-espresso
```

Start a new chat, enable **Social Espresso Operations**, then connect with your Operations email when prompted. The hosted connection needs to be enabled by your workspace administrator. Until the hosted pilot opens, you can install the skills, but live queries and updates require a configured development connection.

## Install in ChatGPT

Once your administrator publishes the plugin to your workspace, open **Plugins**, choose your workspace as the source, install **Social Espresso Operations** and complete the Connect prompt. In a new chat select the plugin and ask “Summarise next week’s events.” If the listing is missing, ask your administrator whether your workspace has joined the pilot.

**Every calendar change requires your explicit written approval in chat after you see the proposed changes.** You can approve all listed jobs or name a subset.

The calendar skill can also list weekly branding quantities, venue addresses, missing machine allocations, machines booked abroad today, and the full week’s setup, service and breakdown schedule.

## Try a weekly staffing review

1. **“Summarise next week’s events.”** You’ll see service dates, booking statuses and staffing or equipment gaps. [Calendar summary skill](skills/summarise-events/SKILL.md)
2. **“Assign staff and equipment to confirmed jobs only.”** Review the proposed barista and equipment for each job. You can change a selection or narrow the list. [Assignment skill](skills/plan-job-assignments/SKILL.md)
3. **“Approve all four”** or **“Approve the Tuesday booking only.”** Use the count or names from your preview. The agent saves each approved proposal and reads the job again. Newly booked baristas start unconfirmed. A proposal expires after 15 minutes, and a changed booking or competing reservation can require a new review.

## Connection and permissions

The package declares one Streamable HTTP server at `https://operations.socialespresso.co.uk/api/mcp`. The client handles OAuth sign-in and consent. Full-calendar viewers can query jobs, staff and equipment. Editors and admins can approve assignment changes when writes are enabled. Staff-scoped accounts cannot access this integration.

Other Agent Plugins clients can load this repository root if they support version 1.0, Streamable HTTP and the registered OAuth flow. Your administrator supplies the client registration for that environment. The skills contain workflow instructions. Current availability, permissions and saved assignments come from Operations. [Agent Plugins runtime](https://agent-plugins.org/client-implementers/mcp-runtime)

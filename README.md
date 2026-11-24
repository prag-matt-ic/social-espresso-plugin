# Social Espresso Operations

Ask which events are coming up, which confirmed bookings still need a barista or grinder, and who is available to cover them. The plugin bundles two skills and connects your agent to the Operations calendar over MCP. Calendar access uses your own Social Espresso account.

## Set up in cloud ChatGPT

If **Social Espresso Operations** already appears under **Installed** at [ChatGPT Plugins](https://chatgpt.com/plugins), open it and choose **Try in chat**. For a fresh personal account with custom MCP servers enabled, follow these steps in a browser.

1. Go to **Plugins → Add → Add custom MCP server**. Enter **Social Espresso Operations** as the name. Select **Server URL** and enter `https://operations.socialespresso.co.uk/api/mcp`. Leave **Authentication** set to **OAuth**.
2. Open **Advanced OAuth settings** and wait for discovery to finish. Choose **User-Defined OAuth Client**. Enter public client ID `931a9bd8-9cab-40bf-88a1-4cedcb37f6ac`, leave the secret blank and use token endpoint auth method **none**. Select only **email** under default scopes and enter `email` under **Base scopes**. Keep the discovered endpoints.
3. Copy the **Callback URL** shown in that form and keep the form open. Give the URL to the Social Espresso maintainer to confirm it is allowed for this OAuth client. Each new connection can have its own callback. Wait for confirmation before continuing.
4. Review the custom-server notice, check **I understand and want to continue**, then choose **Create as a plugin → Connect Social Espresso Operations**. Sign in with your Operations email if prompted, check the account on the consent page, and choose **Allow access**.
5. Back in ChatGPT, choose **Try in chat** and ask **“How many confirmed events are in service today? Use the Operations calendar.”** A live result, including zero, verifies the connection.

This setup connects ChatGPT directly to the hosted calendar tools. The GitHub marketplace installation below also supplies two workflow skills for Codex.

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

# Privacy Policy

**Bot Name:** Z.ai
**Server:** Z.ai Community (Private)
**Last Updated:** June 14, 2026

---

## What Data We Collect

Z.ai collects the following data from server members:

| Data Type | Source | Purpose |
|-----------|--------|---------|
| Message content | Messages in channels where the bot has read access | Spam detection, slur filtering, sentiment analysis, AI chat (when mentioned) |
| Username & Discord ID | Message authors, command users | Strike tracking, moderation logging, analytics |
| Strike records | Moderation actions | Enforcement of server rules, audit trail |
| AI conversation history | Users who mention the bot | Context continuity for AI chat responses |

## How We Use Your Data

* **Auto-moderation.** Messages are scanned in real-time for spam patterns, slurs (including leet-speak variants), and self-promotional links. This determines whether a strike is issued.
* **Sentiment analysis.** Every message receives a sentiment score using VADER (a local library). Approximately 15% of messages with uncertain scores are sent to an LLM API for one-shot reclassification.
* **AI chat.** When you mention the bot, your message is sent to an LLM endpoint to generate a response. Conversation history is stored so the bot remembers context within a session.
* **Analytics.** Aggregated sentiment trends, keyword frequency, and activity metrics are available to server moderators via a dashboard. No individual message content appears in aggregate views.

## Where Your Data Goes

**Primary storage.** All data is stored in a SQLite database on our own hosting machine. We do not use cloud database services.

**Third-party API transmission:**

| Service | Data Sent | Purpose | Stored by Them? |
|---------|-----------|---------|-----------------|
| ZhipuAI/GLM Cloud API | ~15% of messages (sentiment-uncertain ones), AI chat messages when local model is unavailable | One-shot sentiment classification, AI response generation | No |
| Local llama.cpp instance | AI chat messages (primary path) | AI response generation | N/A (on our machine) |

**We do NOT:**
* Sell or share your data with anyone
* Use your messages to train AI models or improve any model
* Upload your data to public databases or analytics services
* Retain message content beyond the retention periods below

## Data Retention

| Data Type | Retention Period |
|-----------|-----------------|
| Message content (analytics store) | 90 days, then auto-pruned |
| AI conversation history | 30 days after last interaction, or until you run `/ai-clear` |
| Temporary spam detection data | Immediately after processing |
| Strike records & mod logs | Indefinite (audit trail) |
| Username & Discord ID | As long as strike record exists |

## Your Rights & Opt-Out

**Full opt-out: leave the server.** Membership in this server is voluntary. If you leave, you stop being tracked immediately. Your existing message content ages out of the analytics store per the 90-day retention schedule.

**Channel-level opt-out via Discord permissions.** Server administrators can remove the bot's "View Channel" or "Read Message History" permission on any channel. Messages in channels where the bot cannot read are not scanned and not stored.

**Individual opt-out.** If you want your historical data removed without leaving the server:
1. DM any server moderator and request deletion by your username
2. We will prune your message content from the analytics store within 7 days
3. Use `/ai-clear` to wipe your AI conversation history on demand, no moderator needed
4. Strike records cannot be deleted. They are part of the server's moderation audit log.

**Data deletion on leave.** If you leave the server, your data remains in the database per the retention schedule above. DM a moderator if you want it removed sooner.

## Security

* The database is hosted on a private machine, not publicly accessible
* Bot token and API keys are stored in environment variables, not in code
* The web dashboard requires an API key for access
* No PII beyond what Discord provides (username + ID) is collected

## Children's Privacy

This bot is used in a private Discord server. We do not knowingly collect additional personal information from children under 13 beyond what Discord itself provides through its API.

## Changes to This Policy

If we change how we handle your data, we will update this document and announce it in the server's announcements channel.

## Contact

Questions about this privacy policy? Contact a Z.ai server moderator or server administrator via DM.

---

*This privacy policy applies to the Z.ai Discord bot operating in the Z.ai Community server only.*

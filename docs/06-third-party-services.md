# Third-Party Services Inventory

Every outside service logbook-api touches. Each row is a trust boundary for the threat model, and the "What it sees" column is the data governance promise in writing.

Update this file whenever a service is added, removed, or starts seeing more data.

| Service | What it sees | Why we use it | Status |
|---------|--------------|---------------|--------|
| GitHub | Source code, CI secrets, issues | Repo, CI/CD (Actions), project board | In use |
| Railway | Everything (it runs the app and database) | v1 hosting | Planned |
| Email provider | Email addresses, log-in links, account notices. Never check-in content. | Magic-link log-in (FR-05) | To pick |
| May First | Everything, if chosen to host | Hosting option: member-owned co-op | Evaluating |
| Cloudflare Tunnel | All traffic passes through it (TLS ends at Cloudflare) | Hosting option: expose a home server without open ports | Evaluating |
| Pocket | Voice recordings and transcripts | Recording ingestion | v2 |
| LLM provider | Transcripts and notes sent for analysis | Summaries, mood insights | v2 |

## Questions to answer for each new service
- What data does it see, and is that the minimum it needs?
- Where is the data stored, and for how long?
- Does it use our data to train models or for anything else?
- What happens to us if it's breached or goes down?
- How do we get our data out and leave?

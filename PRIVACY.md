# YourXChamber privacy

## Local data

The background-check preference (default off), popup language preference, and account list are stored in local extension storage in your browser. The current Chrome build uses `chrome.storage.local`. Entries contain handles, identity/alias information when available, and local timestamps. The extension does not upload or automatically sync the list between browser profiles.

Content scripts inspect the current X page URL, displayed cards, and bounded author/post/parent metadata to apply the local policy. Short-lived relationship and count caches stay in memory. Removing an entry reverses applicable filtering. Uninstalling can remove the stored list.

## Network activity

YourXChamber has no backend, analytics, telemetry, advertising service, remote AI, or remotely loaded executable code.

It observes limited metadata from X responses your browser already receives. Only after explicit popup confirmation, for nearby posts with 1–10 replies it may also make bounded, read-only, same-origin X requests using your existing session. **X receives these ordinary authenticated post-detail requests.** They are not anonymous; X's own logging and privacy policy still apply. The extension does not click posts or send a separate click event. Whether X treats these detail requests as recommendation signals is unverified; an effect is possible, not proven. Disabling the option cancels queued and in-flight checks; it cannot undo a request X has already received.

Only necessary authorization/CSRF and X session header fields from existing same-origin GraphQL traffic are reused. They stay in the page's in-memory request closure, not extension storage, logs, or the public metadata bridge. The extension does not read cookies directly or send your hide list to X.

Limits: one in-flight request, 250 ms minimum start interval, 20 starts per five minutes per page, 12-second timeout, 2 MB response cap. Visibility, supported data-saving signals, error backoff, and duplicate suppression further restrict work.

## What it does not do

YourXChamber does not call X's block, follow, report, messaging, or notification actions. It changes your local presentation; selected accounts can still see or interact with your public account according to your X settings. It does not control X's tracking or traffic.

The extension uses this information only to provide the local filtering and optional reply-count feature described above. The developer does not receive the account list, inspected X content, or session headers. We do not sell user data, use it for advertising or credit decisions, or allow developer personnel to read it. YourXChamber's use of information complies with the Chrome Web Store User Data Policy, including its Limited Use requirements.

## Permissions and published files

The manifest requests `storage` and declares content scripts for `x.com` and `twitter.com`. No cookies, browsing-history, or webRequest permission is requested. Extension pages use a restrictive Content Security Policy.

Browser profiles, session files, screenshots, tool transcripts, local prompts, and raw test outputs are excluded from the repository and installation ZIP. Regression fixtures retain public structural evidence; captured post-body prose is replaced with synthetic text. Never share profiles or authentication material in an issue.

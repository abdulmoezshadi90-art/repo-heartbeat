# repo-heartbeat

A minimal repo paired with a recurring scheduled task (`repo-heartbeat-ping`) that runs every 5 hours and posts "Repo is working" back in chat.

## What it actually does

Claude's usage is metered in rolling 5-hour windows. Each time a prompt is sent, if there's no active window, a new one starts and the usage quota for that window begins ticking.

This routine's real purpose is to **trigger that 5-hour window on a predictable schedule** by sending a lightweight prompt on a timer, rather than waiting for a window to start naturally whenever the next real question happens to be asked. The "Repo is working" message is just a visible confirmation that the scheduled ping fired — the repo itself has no other function.

## Notes

- The task only fires while the Claude Desktop app is open; if it's closed when due, it runs on next launch instead.
- Runs on whatever model is active in the app at fire time — a scheduled task cannot pin a specific model.

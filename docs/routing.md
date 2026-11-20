# Automatic routing (forwarding) of studies

Send received studies on to other nodes by modality, sending AE title, IP address, station or institution.

### 1. Define the destinations first

1.  Routing sends through the normal send queue, so every destination must exist on the Remote nodes page under Settings and answer C-ECHO (green dot).
2.  A destination's queue rules (send window, hold, studies at the same time) apply to routed studies too.

In the console: `/settings/nodes`

### 2. Add a rule

1.  Under Settings, go to Routing, and look for Add rule.
2.  Give it a name and fill in only the conditions you need: modality (CT, MR), sending AE title (AGFANX, CT\*), sending IP (192.168.1.\*, 10.0.0.0/8), station name, institution, words in the study description, or SOP class.
3.  Empty fields match anything.
4.  Comma-separated values are alternatives; \* and ? are wildcards.

In the console: `/settings/routing`

### 3. Choose where it goes

1.  Tick one or more destination nodes.
2.  Each gets its own send job per study.
3.  'Stop' prevents the rules further down from also firing for a study this rule matched.
4.  Useful for an exception rule placed above a catch-all.

In the console: `/settings/routing`

### 4. Enable and set the settle time

1.  Tick Enabled at the top and Save.
2.  The settle time (default 2 minutes) is how long a study must be quiet before it is forwarded, so a study that arrives over several associations is sent complete and once.
3.  Rules are evaluated top to bottom. Use the arrows to reorder.

In the console: `/settings/routing`

### 5. Watch it work

1.  'Waiting to settle' lists studies still arriving (Route now skips the wait).
2.  'Recent decisions' shows which rule matched and what was queued, or that nothing matched.
3.  Routed jobs appear under Jobs as 'routing: \<rule\>' and in the Audit Log under Routing.
4.  A study is never sent back to the node it came from, and images that arrive later are forwarded without repeating the ones already sent.

In the console: `/jobs`

[Receiving images from a modality or PACS](receiving.md) · [All guides](index.md) · [Signing in and permissions](signin.md)

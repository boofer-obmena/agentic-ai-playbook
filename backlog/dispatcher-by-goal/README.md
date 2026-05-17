---
id: BACKLOG-001
title: "Dispatcher-by-Goal (Analog Dispatcher)"
title_ru: "Диспетчер аналогов (Dispatcher-by-Goal)"
type: backlog
status: Hypothesis
source: ""
date_added:
version:
related: ["PATTERN-006"]
---

# Dispatcher-by-Goal (Analog Dispatcher)

> **Диспетчер аналогов (Dispatcher-by-Goal)**

**Extension of PATTERN-006 (Filter-Router).** If the requested resource is unavailable, the dispatcher does not refuse the request. Instead, it determines the essence of the task and offers an approved analog. Algorithm: request → verify → determine goal → find analog → propose → confirm.

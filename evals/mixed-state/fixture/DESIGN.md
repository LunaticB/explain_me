# Target architecture

A background worker should read jobs from a durable queue and retry failed work.
This is design intent; no worker or queue is declared in deployable configuration.

---
published: true
title: Thread Efficiency
tags: thread fastware cpu
---
> Parallelism in 2021 should not be tightly coupled across threads if performance matters, the limitations of that model are well-understood. There is no way to make that comparatively efficient; the CPU cache waste alone ensures that. Nothing you can do with thread support in a programming language will be competitive with e.g. a purpose-built scheduler + native coroutines. That’s right up against the theoretical limit of what is possible in terms of throughput and it doesn’t have any thread overhead. It does introduce the problem of load shedding across cores but that’s solve for all practical purposes.... The state-of-the-art architectures are all, effectively, single-threaded with latency-hiding. This model has a lot of mechanical sympathy with real silicon which is why it is used. It is also pleasantly simple in practice.  - [HN](https://news.ycombinator.com/item?id=26444316)

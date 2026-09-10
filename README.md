<h1 align="center">Quanye Yang</h1>
<p align="center"><em>My Heart Is in the Work.</em></p>

I'm a Computer Science undergraduate at **Xi'an Jiaotong University**, a member of **[valkey-io](https://github.com/valkey-io)**, and a **Linux kernel contributor**.

I work on **RDMA networking, database internals, and distributed protocols**, with a particular interest in concurrency, resource lifetimes, and the behavior of systems under failure.

[Website](https://quanyeyang.github.io/) · [LinkedIn](https://www.linkedin.com/in/quanyeyang/) · [Email](mailto:quanyeyang@proton.me)

## Valkey & libvalkey

My contributions cover transport correctness, Raft cluster protocols, runtime integration, and regression testing.

| Area | Selected contributions | Merged work |
| --- | --- | --- |
| RDMA transport | Fixed re-entrant callbacks and busy loops with IO threads, and use-after-free during concurrent client disconnects. | [IO-thread integration](https://github.com/valkey-io/valkey/pull/3611) · [Disconnect handling](https://github.com/valkey-io/valkey/pull/4534) |
| Raft cluster | Implemented pre-vote to prevent disruptive term inflation, and non-voting members with explicit promotion and demotion. | [Pre-vote](https://github.com/valkey-io/valkey/pull/3931) · [Non-voting members](https://github.com/valkey-io/valkey/pull/4094) |
| RDMA integration | Added runtime loading of RDMA libraries so CLI and benchmark tools can run without RDMA dependencies when using other transports. | [libvalkey](https://github.com/valkey-io/libvalkey/pull/284) · [CLI / benchmark](https://github.com/valkey-io/valkey/pull/3072) |
| Core correctness | Fixed blocked-client use-after-free and invalid TSC calibration that could freeze the monotonic clock. | [Client lifetime](https://github.com/valkey-io/valkey/pull/4212) · [Clock calibration](https://github.com/valkey-io/valkey/pull/4346) |
| Testing & diagnostics | Added RDMA benchmark stress coverage and improved diagnostics for intermittent RDMA CI failures. | [Stress tests](https://github.com/valkey-io/valkey/pull/4025) · [CI diagnostics](https://github.com/valkey-io/valkey/pull/4586) |

## Linux kernel

Recent work on concurrency, resource lifetime management, and network protocol implementation.

<!-- Kernel status snapshot: 2026-09-05. Update from maintainer replies and commits. -->

| Area | Contribution | Status / reference |
| --- | --- | --- |
| **RDMA / RTRS** | Fixed a connection setup/teardown race that leaked shared completion-queue credits when a connection attempt was interrupted. | [Applied to the RDMA tree](https://git.kernel.org/rdma/rdma/c/2ae16aaa78b5ed) |
| **BPF** | Annotated intentional concurrent copies in `bpf_obj_memcpy()`, documenting existing lockless map-update semantics and addressing a syzbot KCSAN report. | [Applied to bpf-next](https://git.kernel.org/bpf/bpf-next/c/5e289c5a4a52) |
| **rhashtable / lockdep** | Investigated a tracepoint-BPF locking report, proposed an initial fix, and tested NeilBrown's revised lockdep-class implementation. | [Tested-by](https://lore.kernel.org/all/178677504716.2852630.10509837046652973246@noble.neil.brown.name/) · [Maintainer applied](https://lore.kernel.org/all/apqW9KXs0JywvG2L@gondor.apana.org.au/) |
| **RDMA / UCMA** | Proposed serializing multicast join and error-path leave to prevent a use-after-free; validated with KASAN and RXE. | [Applied to the RDMA tree](https://git.kernel.org/pub/scm/linux/kernel/git/rdma/rdma.git/commit/?id=662ade4de9ff5eceb0820a9f8e9fac70ba6a815b) |

Also contributed a proposal and follow-up discussion on userspace MPTCP path-manager subflow limits.

[Mailing-list patches and discussions](https://lore.kernel.org/all/?q=f%3Aquanyeyang+OR+f%3A%22Quanye+Yang%22)

## Other upstream contributions

- **[systemd](https://github.com/systemd/systemd/pull/43470):** fixed partition ordering in `systemd-repart` to preserve stable matching across repeated runs.
- **[LLVM](https://github.com/llvm/llvm-project/pull/203463):** added nearest-opcode suggestions to `llvm-exegesis` diagnostics.
- **[Apache ShardingSphere](https://github.com/apache/shardingsphere/pull/37391):** corrected MySQL proxy routing for multi-expression queries without a `FROM` clause.

## Projects & notes

- **[PacketGhost](https://github.com/quanyeyang/PacketGhost):** a userspace packet-mutation engine in C, using Netfilter and raw sockets to study TCP behavior and DPI evasion.
- **[6.5840 Labs](https://github.com/quanyeyang/6.5840-Labs):** Go implementations of MapReduce, Raft, and key-value services, with study notes.
- **[Systems notes](https://github.com/quanyeyang/pwd-writeup):** experiments and write-ups on DPDK, performance analysis, eBPF/XDP, and binary exploitation.

<details>
<summary><strong>Recent merged pull requests</strong> · updated daily</summary>

<!-- BEGIN_RECENT_PRS -->
- 2026-09-10 · [sd-ndisc: do not stop solicitations on zero-lifetime RA](https://github.com/systemd/systemd/pull/43698) in **systemd/systemd**
- 2026-09-01 · [tests/rdma: improve diagnostics for sporadic connection failures](https://github.com/valkey-io/valkey/pull/4586) in **valkey-io/valkey**
- 2026-08-31 · [Fix RDMA UAF: connection freed inside callHandler](https://github.com/valkey-io/valkey/pull/4534) in **valkey-io/valkey**
- 2026-08-26 · [repart: Keep new partitions after existing same-type partitions](https://github.com/systemd/systemd/pull/43470) in **systemd/systemd**
- 2026-08-20 · [Fix flaky multi-part AOF manifest tests](https://github.com/valkey-io/valkey/pull/4491) in **valkey-io/valkey**
- 2026-08-18 · [Skip IO-thread write-done client re-lookup unless update\_state sync-invokes handlers \(9.0\)](https://github.com/valkey-io/valkey/pull/4452) in **valkey-io/valkey**
- 2026-08-17 · [Skip IO-thread read-done followup unless update\_state sync-invokes handlers \(9.0\)](https://github.com/valkey-io/valkey/pull/4414) in **valkey-io/valkey**
- 2026-08-13 · [Skip IO-thread read-done followup unless update\_state sync-invokes handlers](https://github.com/valkey-io/valkey/pull/4401) in **valkey-io/valkey**
- 2026-08-12 · [Fix RDMA + IO threads re-entrancy via connection postpone masks \(9.0\)](https://github.com/valkey-io/valkey/pull/3335) in **valkey-io/valkey**
- 2026-08-12 · [Raft Cluster: Implement Non-voting Members](https://github.com/valkey-io/valkey/pull/4094) in **valkey-io/valkey**
- 2026-08-11 · [Fix slow-clocksource check for HW monotonic clock and non-x86 advisories](https://github.com/valkey-io/valkey/pull/4272) in **valkey-io/valkey**
- 2026-08-10 · [Fix re-entry into processPendingCommandAndInputBuffer on blocked clients](https://github.com/valkey-io/valkey/pull/4376) in **valkey-io/valkey**
- 2026-08-10 · [Fix frozen monotonic clock on unsynchronised TSC hosts](https://github.com/valkey-io/valkey/pull/4346) in **valkey-io/valkey**
- 2026-08-07 · [Fix/ready key blocked client uaf](https://github.com/valkey-io/valkey/pull/4212) in **valkey-io/valkey**
- 2026-08-06 · [tests/rdma: add valkey-benchmark --rdma stress for RDMA + IO threads](https://github.com/valkey-io/valkey/pull/4025) in **valkey-io/valkey**
- 2026-08-05 · [Fix RDMA + IO threads re-entrancy and busy-loop via connection postpone masks](https://github.com/valkey-io/valkey/pull/3611) in **valkey-io/valkey**
- 2026-08-03 · [Fix RESP3 push frame torn apart on self-publish with copy avoidance](https://github.com/valkey-io/valkey/pull/4253) in **valkey-io/valkey**
- 2026-08-03 · [Prevent double-free of the module timer when the callback stops it](https://github.com/valkey-io/valkey/pull/4211) in **valkey-io/valkey**
- 2026-07-21 · [Check and reject invalid slot import job names](https://github.com/valkey-io/valkey/pull/4210) in **valkey-io/valkey**
- 2026-06-17 · [\[llvm-exegesis\] Add did-you-mean hint for unknown opcodes](https://github.com/llvm/llvm-project/pull/203463) in **llvm/llvm-project**
- 2026-06-15 · [Raft Cluster: Implement Pre-Vote protocol to prevent term inflation](https://github.com/valkey-io/valkey/pull/3931) in **valkey-io/valkey**
- 2026-05-27 · [add/CVE-2026-25243 Invalid Memory Access in Redis RESTORE Command May Lead to Remote Code Execution](https://github.com/Unclecheng-li/poc-lab/pull/6) in **Unclecheng-li/poc-lab**
- 2026-05-22 · [add/CVE-2026-27623-valkey-dos](https://github.com/Unclecheng-li/poc-lab/pull/4) in **Unclecheng-li/poc-lab**
- 2026-05-06 · [Fixes server crash when RDMA benchmark clients disconnect](https://github.com/valkey-io/valkey/pull/3448) in **valkey-io/valkey**
- 2026-05-06 · [valkey-benchmark: centralize RDMA WRITABLE kick via createFileEvent](https://github.com/valkey-io/valkey/pull/3492) in **valkey-io/valkey**
- 2026-02-26 · [Lazy loading of RDMA libs in CLI/Benchmark when building as module](https://github.com/valkey-io/valkey/pull/3072) in **valkey-io/valkey**
- 2026-02-23 · [Implement runtime dynamic loading for RDMA libraries](https://github.com/valkey-io/libvalkey/pull/284) in **valkey-io/libvalkey**
- 2025-12-21 · [enforce 64‑bit off\_t regardless of include order; prevent LTO type mismatch \(Fixes #2938\)](https://github.com/valkey-io/valkey/pull/2943) in **valkey-io/valkey**
- 2025-12-16 · [mysql-proxy: skip admin for no-FROM multi-expression selects; add tests](https://github.com/apache/shardingsphere/pull/37391) in **apache/shardingsphere**
<!-- END_RECENT_PRS -->

[Browse all merged pull requests](https://github.com/search?q=author%3Aquanyeyang+is%3Apr+is%3Amerged+-user%3Aquanyeyang&type=pullrequests)

</details>

---

**I speak Chinese, English, Japanese and a little German, and enjoy learning languages.**

*Play the long game. Do the hard, right things.*


![Valkey](https://img.shields.io/badge/Valkey-Contributor-003545?style=for-the-badge&logo=redis&logoColor=white)

![Linux Kernel Contributor](https://img.shields.io/badge/Linux_Kernel-Contributor-E5A50A?style=for-the-badge&logo=linux&logoColor=white)

![systemd](https://img.shields.io/badge/systemd-Contributor-0086D1?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MyAxMyI+PHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgMHYxM2g1di0ySDJWMmgzVjB6bTM4IDB2MmgzdjloLTN2Mmg1VjB6Ii8+PGNpcmNsZSBmaWxsPSIjZmZmIiBjeD0iMTUuNSIgY3k9IjYuNSIgcj0iNC41Ii8+PHBhdGggZmlsbD0iI2ZmZiIgZD0ibTI0IDYuNSA4LTQuNXY5eiIvPjwvc3ZnPg==)

![LLVM](https://img.shields.io/badge/LLVM-Contributor-000000?style=for-the-badge&logo=llvm&logoColor=white)

![ShardingSphere](https://img.shields.io/badge/Apache_ShardingSphere-Contributor-E16223?style=for-the-badge&logo=apache&logoColor=white)

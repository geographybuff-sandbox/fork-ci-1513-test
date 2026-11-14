# Results, 2026-11-14

Both bridges sweep the same PR, [#1](https://github.com/geographybuff-sandbox/fork-ci-1513-test/pull/1), from [geographybuff/fork-ci-1513-test](https://github.com/geographybuff/fork-ci-1513-test), a fork created for this test. Every sweep was dispatched manually. Full log with every check: [log.md](log.md).

| Sweep | Fork state before the sweep | fork-ci v1.0.1 | With the #1513 fix (`52143ed`) |
|---|---|---|---|
| 1 | Actions never enabled; `GET …/actions/workflows/ci.yml` returns 404 and the push started no run | [`neutral`](https://github.com/geographybuff-sandbox/fork-ci-1513-test/runs/132459035911) "No fork run for this commit" | [`action_required`](https://github.com/geographybuff-sandbox/fork-ci-1513-test/runs/132459065633) "Workflow not available on the fork" |
| 2 | nothing changed | [0 written](https://github.com/geographybuff-sandbox/fork-ci-1513-test/actions/runs/43598880034) | [0 written](https://github.com/geographybuff-sandbox/fork-ci-1513-test/actions/runs/43598883393) |
| 3 | Actions enabled, new push, [fork run](https://github.com/geographybuff/fork-ci-1513-test/actions/runs/43598918458) in progress | [`in_progress`](https://github.com/geographybuff-sandbox/fork-ci-1513-test/runs/132459347926) | [`in_progress`](https://github.com/geographybuff-sandbox/fork-ci-1513-test/runs/132459373634) |
| 4 | that run finished | `success` | `success` |
| 5 | docs-only push, skipped by the fork's path filter; workflow `active` | [`neutral`](https://github.com/geographybuff-sandbox/fork-ci-1513-test/runs/132459602211) | [`neutral`](https://github.com/geographybuff-sandbox/fork-ci-1513-test/runs/132459609562) |
| 6 | nothing changed | [0 written](https://github.com/geographybuff-sandbox/fork-ci-1513-test/actions/runs/43599048551) | [0 written](https://github.com/geographybuff-sandbox/fork-ci-1513-test/actions/runs/43599052255) |

The fix changes only the 404 case. Runs are mirrored the same way, an active workflow with no run stays `neutral`, and unchanged sweeps still write nothing.

Note: `GET /repos/{fork}/actions/permissions` reported `enabled: true` on the fresh fork while the workflow endpoint returned 404. After a `PUT` to that endpoint and a new push, the workflow became `active` and the push ran.

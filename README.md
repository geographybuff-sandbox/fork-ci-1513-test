# fork-ci #1513 test

End-to-end test for [apache/infrastructure-actions#1513](https://github.com/apache/infrastructure-actions/issues/1513): what fork-ci reports for a fork that never enabled Actions.

- `bridge_v101.yml`: fork-ci v1.0.1 (`adff9de`), check "CI (fork) v1.0.1".
- `bridge_fix.yml`: the proposed fix (`geographybuff/infrastructure-actions@52143ed`), check "CI (fork) with fix".
- `ci.yml`: stand-in fork CI (from [arrow-rs-fork-ci-test](https://github.com/geographybuff-sandbox/arrow-rs-fork-ci-test)); `docs/**` pushes skip it.

Results: [RESULTS.md](RESULTS.md).

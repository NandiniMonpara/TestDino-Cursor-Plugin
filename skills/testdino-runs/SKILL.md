# TestDino Test Runs

Use TestDino tools when the user wants to inspect automated test results.

Preferred flow:

1. Call `health` if `projectId` is not known.
2. Use `list_testruns` to find the relevant run.
3. Use `get_run_details` for one specific run.
4. Use `list_testcase` or `get_testcase_details` for deeper failure analysis.
5. Use `debug_testcase` when the user wants historical debugging context for a failing test.

Good requests for this skill:

- show failed runs on a branch
- inspect flaky tests
- summarize one test run
- debug a failing testcase with history

Common filters from the docs:

- branch
- time interval
- author
- commit
- environment
- status
- browser
- error category
- tags

Use `list_testruns` first when the user does not already know the exact run ID or counter.
Use `debug_testcase` when the user wants root-cause analysis and recommendations across historical runs, not just a single-run snapshot.

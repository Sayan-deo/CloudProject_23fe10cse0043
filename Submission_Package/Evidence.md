# FestPass Jenkins evidence

**Source repository:** [Sayan-deo/CloudProject_23fe10cse0043](https://github.com/Sayan-deo/CloudProject_23fe10cse0043), branch `main`  
**Jenkins job:** `festpass-ci`  
**Submission codes:** class `001`, challenge `00443`  
**Alias:** `sayan-deo` (from the checked-out Git commit author)

## Red build

- Build **#5** was started by an SCM change and checked out `8a8b4998b9aa40bbc62a8e8e27d0e781bb56a561` (`Personalize my help introduction`).
- Result: **FAILURE**, 28 tests, 3 failures.
- `cancellationFreesSeat` failed because booking another student after cancelling the only seat still produced `SOLD OUT`. The cancellation method validated that a booking existed but left it in the event roster.
- `Build JAR`, `Smoke test JAR`, and `Save artifact` were skipped. No JAR was published; the diagnostic evidence CSV was archived.
- Files: [red evidence CSV](red-build-5/submission-evidence.csv), [Jenkins test report](red-build-5/jenkins-test-results.xml).

## Repair and green build

`BookingService.cancel()` now removes the validated student ID from the event’s booking set. Tests, build helpers, and pipeline stages were left intact.

- Build **#6** was started by an SCM change and checked out `2168a255288db41536544c69fec9dfbf20c90782` (`Remove cancelled event bookings`).
- Result: **SUCCESS**, 28 tests, 0 failures. All seven real-JAR smoke checks passed.
- JAR SHA-256: `fd0886d68cadc653f68cd76507f317eb14a6d3829f92bce85566088b3e87ab76`.
- Running the archived JAR’s `help` command prints: `FestPass - campus event registration (sayan-deo)`.
- Files: [green evidence CSV](green-build-6/submission-evidence.csv), [final JAR](green-build-6/festpass.jar), [build info](green-build-6/build-info.txt), [smoke-test results](green-build-6/smoke-test.txt), [JAR help output](green-build-6/help-output.txt).

The source history also includes polling-trigger commit `bb5fd6b` and help personalization commit `8a8b499`. Build #4 was the manual bootstrap run; #5 and #6 provide the automatic red and green evidence.

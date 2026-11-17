# Automation Strategy: saucedemo.com

## 1. Goal

Catch regressions in the critical shop flows within minutes of every code change, so manual testers can spend their time on exploratory testing.

## 2. Scope

- **In scope:** login (valid, invalid, locked-out user), add and remove items in the cart, checkout, product sorting.
- **Out of scope:** visual design, performance and load testing, exploratory testing.

## 3. Approach

- Mostly UI tests for the critical user journeys, plus one small API test.
- Page Object Model to keep locators and test logic separate.
- Each test is independent and sets up its own state.

## 4. Tools

- **Playwright:** auto-waiting, fast, built-in tracing and screenshots.
- **Python + pytest:** simple syntax, fixtures, markers, parametrize.
- **GitHub Actions:** runs the tests in CI.

## 5. Environments

- The public demo site `https://www.saucedemo.com`.
- The base URL is kept in config, so it can point to another environment later.

## 6. Test data

- Known saucedemo users (standard, locked-out) are stored in one data file, never hard-coded inside tests.

## 7. CI/CD

- Smoke tests run on every pull request.
- The full regression suite runs nightly.

## 8. Reporting

- HTML report after each run.
- Screenshots, video and traces saved when a test fails.

## 9. Metrics

- Pass rate, flaky-test rate, total run time, and bugs caught by automation.

## 10. Roadmap

1. Smoke suite (login, add to cart).
2. Full regression (checkout, sorting, negative cases).
3. CI pipeline and cross-browser runs.

## 11. Risks

- Flaky tests, which we reduce with auto-waiting and stable locators.
- The public site or its test data may change without notice.

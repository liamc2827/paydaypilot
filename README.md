# PaydayPilot — professional local-first PWA beta

A responsive, installable budgeting web app built with vanilla JavaScript modules, CSS, and an offline service worker. No build step, paid hosting, database, or account required.

## Features
- Two-step onboarding with editable pay schedule
- Safe-to-spend dashboard that reserves bills due before next payday
- Weekly, biweekly, twice-monthly, and monthly paycheck scheduling
- Recurring bills with weekly, biweekly, monthly, quarterly and yearly schedules
- Activity ledger for completed and planned income/expenses
- Add, edit, pause, and delete recurring bills
- Savings goals with per-paycheck contributions
- Eight-paycheck cash projection
- Local-only data storage, JSON backup/restore and data deletion
- Offline-ready after first successful online load on HTTPS/localhost

## Run locally
Use a local web server, not `file://`, because the app uses JavaScript modules.

```bash
cd paydaypilot_pro
python3 -m http.server 8080
```
Visit http://localhost:8080. For iPhone testing, deploy to a free HTTPS static hosting service such as GitHub Pages or Cloudflare Pages. For GitHub Pages, create a public repository, upload the contents of this folder to its root, then enable Pages from the main branch/root under Settings > Pages. The hosted URL will be provided by GitHub.

## Tests
Requires Node.js 18+:

```bash
node --test tests/*.test.mjs
node --check app.mjs
```

## Important beta limitations
- This is a usable **local-first beta**, not a production-ready fintech service.
- The app does not sync across devices or connect to banks. Balances must be manually updated.
- Data is stored unencrypted in this browser's localStorage. Avoid shared devices. Browser resets or private mode can lose data; export backups.
- No paid subscriptions, authentication, analytics, or server-side infrastructure are present.
- Forecasts assume bills and paychecks arrive as scheduled, and don't account for unentered purchases or transfers. Goal contributions are tracked separately and are not automatically deducted from forecasts.
- Recurring schedules are calendar-based and do not adjust for weekends, bank holidays, or employer-specific pay rules.
- Service workers require HTTPS or localhost; SVG icon support varies by platform. For production, generate 192px/512px PNG icons and Apple touch icons.
- Needs manual end-to-end device, accessibility, and financial edge-case QA before inviting real users.

## Free deployment checklist
1. Run the six automated tests.
2. Upload project files to GitHub Pages or Cloudflare Pages; no paid plan needed for a small static beta.
3. Open the HTTPS URL on your phone and complete onboarding.
4. Add a recurring bill, create a savings goal, and confirm forecasts.
5. Test export, import, reset, offline reload, and Add to Home Screen.
6. Prepare a public privacy policy and support contact before public promotion.

No guarantees of earnings or zero-cost operation at scale.

## Product behavior and caveats
- Enter *net* paycheck deposits; do not subtract withholding again.
- Record completed spending to update the manually tracked balance; planned transactions affect forecasts only.
- Savings goals are trackers, not separate bank accounts. Recording a goal contribution does not automatically deduct it from checking.
- Recurring bills must use the next **unpaid** due date. If you pay early, update the next due date to avoid double counting.
- Forecasts assume all entered income and recurring bills occur as scheduled. They do not predict unrecorded spending.
- No user accounts, paid subscriptions, bank integration, or server database are implemented.
- Browser end-to-end testing was attempted but the testing environment blocked local navigation. Unit tests and JS syntax checks passed; real-device acceptance testing is required.

=============================================================
  SHIFT COVERAGE TRACKER
  v1.0 — Single-file HTML App
=============================================================

OVERVIEW
--------
A browser-based shift coverage tracking tool for distributed
teams. All data is stored locally in your browser
(localStorage) and optionally synced to Google Sheets for
multi-user access.

No installation required. Open the HTML file in any modern
browser and start tracking.


GETTING STARTED
---------------
1. Open shift_coverage_tracker.html in your browser.
2. Select the current month from the top header.
3. Click "Manage Resources" to set up your team.
4. Add Shifts, Locations, and Team Members.
5. Start entering status codes in the grid.


MANAGE RESOURCES (Modal)
------------------------
Three tabs: Resources | Shifts | Locations

  Resources Tab
  - Add team members with name, shift, timezone, days off,
    and assigned location.
  - Check boxes next to members, then use the ⋯ button →
    "Apply holidays to checked" to bulk-apply holidays for
    the current month.
  - Edit or remove members at any time.

  Shifts Tab
  - Create reusable shift configurations (label, start/end
    time, timezone).
  - Assign a shift preset to any resource.

  Locations Tab
  - Add location names (e.g. Manila, Bangalore, Austin).
  - Auto-fill public holidays by searching for a country
    and clicking ⬇ Auto-fill.
    and clicking ⬇ Auto-fill.
  - Manually add or remove individual holiday dates.
  - India is supported via built-in holiday data (2024–2027).


STATUS CODES
------------
Enter these codes in the grid cells (case-insensitive):

  (blank)   Present — full day, 100% coverage
  PN1       Night shift — off 1st half, present 2nd half (50%)
  PN2       Night shift — present 1st half, off 2nd half (50%)
  PTO1      Paid Time Off — PTO 1st half, present 2nd half (50%)
  PTO2      Paid Time Off — present 1st half, PTO 2nd half (50%)
  HOL       Holiday — full day off, 0% coverage (teal)
  (other)   Absent / Leave — 0% coverage (e.g. SL, AL, LWOP)

Press Enter or click away to save a cell edit.


HOLIDAY FLAGS
-------------
- Dates with configured holidays show a 🚩 flag in the
  grid's date column. Hover to see which location(s).
- Click 🏖 in a resource's column header to apply that
  resource's location holidays to the current month.
- Use ⋯ → "Apply holidays to checked" to apply holidays
  to multiple resources at once.


DAY VIEW
--------
Click any #, Day, Date, or Coverage cell to open the
detailed day view. It shows:
  - Overall daily coverage percentage
  - Hour-by-hour timeline for all resources
  - Coverage % per hour
  - Total Available count per hour
  - Selectable time range with average coverage summary
  - Total Available count per hour
  - Selectable time range with average coverage summary


LIVE STATUS BAR
---------------
Shows real-time coverage for the current hour and next
4 hours, based on the selected view timezone. Updates
every 60 seconds.


TODAY HIGHLIGHT
---------------
Today's row (#, Day, Date) is highlighted in yellow based
on the selected view timezone.


CLOUD SYNC (Google Sheets)
--------------------------
Enables multi-user access via a Google Apps Script web app.

Setup:
  1. Open Google Sheets → Extensions → Apps Script.
  2. Copy the GAS script from the Cloud Sync panel
     (click ⟳ icon in toolbar → Copy GAS Script).
  3. Deploy as Web App (Execute as: Me, Access: Anyone).
  4. Paste the Web App URL into the Cloud Sync panel.
  5. Click 💾 Save URL.

Sync behavior:
  - Push: Happens automatically 2 seconds after any data
    change, if a sync URL is configured.
  - Pull-before-push: Before pushing, the app fetches the
    current server state and merges your local changes on
    top — preserving edits made by other users on different
    cells simultaneously.
  - Auto-pull: Optional. Enable in the sync panel to pull
    on a schedule (30s / 1min / 5min / 10min).
  - Manual pull: Click ⟳ in the toolbar at any time.

Multi-user notes:
  - Different people editing different cells = safe ✓
  - Two people editing the exact same cell simultaneously =
    last push wins (unavoidable without server locking)
  - Config changes (resources, shifts, locations) are
    last-write-wins — coordinate these changes manually


TOOLBAR BUTTONS
---------------
  ⚙ Advanced Filter   Filter grid by shift, timezone, days off
  🔍 Quick filter      Filter by resource name
  Manage Resources    Open the Resources/Shifts/Locations modal
  Export CSV          Download current month as CSV
  ⬇ Export Data       Download full app data as JSON
  ⬆ Import Data       Restore from a previously exported JSON
  ⟳                   Manual pull from cloud
  ☁ Cloud Sync        Open sync configuration panel
  Clear This Month    Wipe all status data for current month


EXPORT / IMPORT
---------------
- Export Data: saves a full JSON snapshot of all resources,
  shifts, locations, holidays, and status data.
- Import Data: restores from a snapshot. Replaces all
  current data — use with caution.
- Export CSV: exports the current month's grid for use in
  Excel or other tools.


KEYBOARD SHORTCUTS
------------------
  Enter   Commit cell edit (same as clicking away)
  Escape  (click away) Cancel focus without changes


BROWSER STORAGE
---------------
All data is saved in browser localStorage under these keys:
  sct_resources, sct_data, sct_shift_cfgs,
  sct_locations, sct_holidays, sct_sync_url,
  sct_auto_pull, sct_auto_interval

Clearing browser data will erase all local data.
Use Export Data regularly as a backup.


SUPPORTED BROWSERS
------------------
Chrome, Edge, Firefox, Safari (modern versions).
Not designed for mobile — best used on desktop.


=============================================================
  Built for CloudOps team use. Single HTML file, no server,
  no dependencies, no installation.
=============================================================

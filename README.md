# LabPlan — Process Lab build planning

Website: https://yousefmahajna.github.io/lab-build-plan/

Main website: https://yousefmahajna.github.io/interconnect-process-lab/

This standalone website has its own repository, `YousefMahajna/lab-build-plan`, separate from the Process Lab hub. It uses plain HTML, CSS and JavaScript and needs no dependencies or build step.

## Features

- Editable full-year timeline, with a configurable planning year and working week.
- Products, machines, module quantities, priorities, practical engineers, vacations and training.
- Product, person and machine views with consistent product colors and a side legend.
- One bar per product; click to edit its steps or use Edit all steps to update product, dates, quantity and priority together.
- Drag a build to reschedule it; dragging a product moves all its steps together.
- Large P1–P4 badges. Products sort P1, P2, P3, P4, then time away/training, then unscheduled products without priority labels.
- Working-day capacity and warnings for overlapping person or machine assignments.
- Browser-local saving and JSON export/import.

## Bring your current plan to this website

1. Open the original LabPlan website in the browser where you edited your plan.
2. Click **Export plan** to download its JSON file.
3. Open this GitHub Pages website and click **Import** to select that file.

The old and new GitHub Pages addresses share the same origin and keep the same `labplan-v1` storage key, so an existing GitHub Pages plan stays available in the same browser. Browser data belongs to a website origin. The migration does not automatically copy a plan saved on the original ChatGPT Site. Source files contain generic sample data; no private browser plan is committed. Export a backup before changing browsers or clearing storage. This app does not currently synchronize plans between users or devices.

## Files

- index.html — application layout and editing dialogs.
- app.js — planner, validation, scheduling, persistence and import/export.
- style.css — responsive layout, product colors and priority badges.
- tests/planning.test.cjs — scheduling, bulk editing, sorting and color consistency checks.
- package.json — check and test commands, with no dependencies.

## Local preview and checks

Serve this folder with any static HTTP server, or open index.html directly. Run checks with Node 24:

```sh
npm run check
npm test
```

This repository has its own Pages deployment and checks workflows. Enable Pages in this repository under Settings → Pages → Source: GitHub Actions. Return to the hub by clicking the LabPlan logo.

## Planning rules

Each activity reserves assigned resources for full working days. Training and vacations count as occupied person-days. The product quantity shown is its largest stage quantity, so the same modules are not counted repeatedly across stages. Separate batches can be represented as separate products. A product uses the highest priority among its stages; P1 = Critical, P2 = High, P3 = Normal, P4 = Low. Blank mixed fields in the bulk editor preserve each step's existing value.

The hub's Users list controls its application links. The planner itself is a static browser-local tool and does not enforce authenticated roles. Do not treat a hub permission label as access control for this URL.



## Process development marks

Use **+ Mark development** to choose a product (or **All scheduled products**) and dates. The timeline draws a bracket under that part of the product build bar, with **Process development** centered beneath it. A mark describes the product's steps during the selected period; it is not an additional task and reserves no lab team or machine capacity. Existing development periods display automatically as brackets. Click a bracket to change its dates or delete it. Product dragging moves its marks together with its steps.


### Development marks in By machine

The machine timeline repeats each product’s Process development bracket beneath its matching build steps. A machine shows only the dates where that product’s marked period overlaps its build on that machine. Overlapping builds and development marks have enough vertical space for their labels. Editing a bracket changes the same saved product mark in both views; annotations do not add machine bookings or capacity. The Process Development type filter also finds related machine builds.



## Full-year timeline navigation

Activities and development marks can be scheduled anywhere from January 1 to December 31 of the planning year. Use From/To month selectors for any consecutive range, 1 month/3 months/Full year presets, and Earlier/Later to move the selected window. Drag the annual navigator’s selected window to pan, or its edges to change the visible range and fit it to the available width. The zoom slider and zoom buttons adjust day scale; Fit period restores a fitted overview. Use the horizontal scrollbar for detailed views or Ctrl+mouse wheel to zoom. Arrow keys move the focused navigator window or edge by a day; Shift+arrow moves a week. View preferences save separately from the plan and do not change activity dates. Existing plans and exports remain compatible.

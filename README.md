# Bamboo Breakfast &amp; Coffee website

This site was created to practice the bases of web development. The idea for the content on the page comes from my daughter who wants to create a restaurant.

## Running the project locally

The pages are static HTML/CSS/JS, but the menu items, news and users are loaded with `fetch` from a REST API at `http://localhost:3000`. That API is provided by [json-server](https://github.com/typicode/json-server), which serves the data in `db/db.json` (tables: `menu`, `news`, `users`).

### Prerequisites

- [Node.js](https://nodejs.org/) (with npm)

### Installation

```bash
git clone <repository-url>
cd bbandc
npm install        # installs Bootstrap and Font Awesome into node_modules/
```

The HTML files load Bootstrap and Font Awesome from `node_modules/`, so `npm install` is required for the styling to work.

### Start the JSON API (terminal 1)

```bash
npx json-server@0.17.4 --watch db/db.json --port 3000
```

The version is pinned because newer json-server releases changed the CLI and behaviour. Check that it works by opening <http://localhost:3000/menu> in the browser; you should see the menu items as JSON.

### Serve the web pages (terminal 2)

Serve the project root with any static server (opening the files directly with `file://` may be blocked by the browser for `fetch`/CORS reasons):

```bash
npx serve .
# or
python3 -m http.server 8080
```

Then open, for example:

- <http://localhost:8080/html/index.html> – home page and news
- <http://localhost:8080/html/menu.html> – menu items loaded from `db.json`
- <http://localhost:8080/html/admin.html> – admin page (create/edit/delete records through the API)

(With `npx serve` use the port it prints instead of 8080.)

### Notes

- Both servers must be running at the same time. If the menu or news is empty, check that json-server is running on port 3000.
- Changes made on the admin page are written to `db/db.json`.
- `db/db2.json` and `db/db copy.json` are older copies of the data and are not used by the pages.

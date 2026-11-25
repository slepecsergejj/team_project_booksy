<<<<<<< HEAD
# 📚 Booksy

Booksy is a responsive, single-page online bookstore website. It allows users to browse books by category, view detailed book information, explore customer reviews, discover upcoming events, and find the bookstore's contact information and location.

## 📖 About the Project

Booksy is a team project developed based on a Figma design and a technical specification.

The main goal of the project is to provide users with a convenient way to explore a bookstore's catalog, find books by category, view detailed information, and interact with demo shopping features.

Book and category data are retrieved from an external REST API rather than being hardcoded into the application.

## ✨ Features

- **Responsive Design:** Mobile First approach with support for screens from 320px, including mobile devices, tablets, and desktop screens.
- **Header:** Navigation with anchor links and a full-screen mobile menu. The menu supports keyboard interaction, closes with the Escape key, and prevents background scrolling while open.
- **Hero:** Image slider powered by Swiper, with navigation arrows and keyboard controls.
- **Books Catalog:**
  - Dynamic book and category loading from the API.
  - Filtering books by category.
  - Display counter showing the number of visible books.
  - Responsive pagination: 10 books on mobile devices and 24 on tablets and desktops.
  - Show More button that loads 4 additional books per click.
  - Loading, empty-state, and error messages.
- **Book Details Modal:**
  - Book cover, title, author, and price.
  - Quantity selector with automatic total price calculation.
  - Accordion sections: Details, Shipping, and Returns.
  - Demo Add To Cart and Buy Now actions.
- **Feedbacks:** Customer review slider with navigation arrows, pagination, and keyboard support.
- **Events:** Event slider with a registration modal for selected events.
- **Article:** A short story about the bookstore.
- **Location:** Clickable email and phone links, along with an embedded Google Maps location.
- **Footer:** Navigation links and an email subscription form with validation.

All modal windows can be closed using the close button, clicking outside the modal, or pressing Escape. Background scrolling is disabled while a modal is open.

## 🛠 Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 | Semantic markup, forms, lists, and the dialog element |
| CSS3 | Responsive styling, Mobile First approach, CSS Reset |
| JavaScript (ES Modules) | Application logic, API requests, DOM manipulation, modals, and sliders |
| Vite 8 | Development server and production build |
| Swiper 14 | Sliders in the Hero and Feedbacks sections |
| accordion-js 4 | Accordion functionality in the book details modal |
| Google Fonts (Rubik) | Typography |
| SVG Sprite | Centralized icon management |
| GitHub Actions | Automated build and deployment |
| GitHub Pages | Website hosting |
| Books API | External source of book and category data |

## 🚀 Getting Started

### Requirements

- Node.js (version 22 is used in CI).
- npm (included with Node.js).

### Installation

Clone the repository:

```bash
git clone https://github.com/vladyslavdanko391-lab/booksy.git
cd booksy
git checkout main
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Vite will display the local development URL in the terminal, usually:

```text
http://localhost:5173/booksy/
```

Open the URL in your browser.

### Available Scripts

| Command | Description |
|---|---|
| `npm run dev` | Starts the development server with hot module replacement |
| `npm run build` | Creates an optimized production build in the `dist/` directory |
| `npm run preview` | Starts a local server to preview the production build |

**Note:** The `vite.config.js` file defines `base: '/booksy/'`, so the application is configured to run under the `/booksy/` path on both the local development server and GitHub Pages.

## 🌍 Deployment

The website is automatically built and deployed using GitHub Actions.

The workflow is configured in:

```text
.github/workflows/deploy.yml
```

Deployment is triggered automatically whenever changes are pushed to the `main` branch. It can also be started manually using `workflow_dispatch`.

The workflow performs the following steps:

1. Sets up Node.js 22.
2. Installs dependencies using `npm ci`.
3. Builds the project using `npm run build`.
4. Deploys the contents of the `dist/` directory to GitHub Pages.

## 🗂 Project Structure

```text
booksy/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── index.html
├── vite.config.js
├── package.json
└── src/
    ├── assets/
    │   └── icons/
    │       └── icons.svg
    ├── img/
    ├── partials/
    │   ├── header.html
    │   ├── hero.html
    │   ├── books.html
    │   ├── feedbacks.html
    │   ├── events.html
    │   ├── article.html
    │   ├── location.html
    │   ├── footer.html
    │   ├── book-modal.html
    │   └── contact-modal.html
    ├── css/
    │   ├── reset.css
    │   ├── base.css
    │   ├── index.css
    │   └── partials/
    └── js/
        ├── main.js
        ├── api.js
        ├── header.js
        ├── hero.js
        ├── feedbacks.js
        ├── events.js
        ├── footer.js
        └── books/
            ├── init-books.js
            ├── config.js
            ├── state.js
            ├── elements.js
            ├── helpers.js
            ├── books.js
            ├── filter.js
            ├── modal.js
            ├── quantity.js
            ├── order.js
            └── toast.js
```

## 🧩 Project Architecture

The `index.html` file contains the main application container:

```html
<div id="app"></div>
```

The `src/js/main.js` file acts as the application entry point. It imports HTML partials from `src/partials/` as raw strings, processes asset paths, inserts the markup into the `#app` container, and initializes the application's JavaScript modules.

### JavaScript Modules

| File | Responsibility |
|---|---|
| `main.js` | Assembles the page and initializes application modules |
| `api.js` | Centralizes requests to the Books API |
| `header.js` | Handles mobile navigation, menu interactions, and scroll locking |
| `hero.js` | Initializes the Hero slider with navigation and keyboard controls |
| `feedbacks.js` | Manages the customer reviews slider and responsive slide behavior |
| `events.js` | Handles the events slider and registration modal |
| `footer.js` | Validates the newsletter subscription form |

### Books Module (`js/books/`)

The books module contains the catalog functionality, divided into smaller modules:

| File | Responsibility |
|---|---|
| `init-books.js` | Initializes the catalog, event listeners, categories, and books |
| `config.js` | Stores application constants and configuration |
| `state.js` | Manages the catalog state |
| `elements.js` | Collects and organizes DOM elements |
| `helpers.js` | Provides formatting and utility functions |
| `books.js` | Renders book cards, updates counters, and handles loading states |
| `filter.js` | Loads categories and manages category filtering |
| `modal.js` | Handles the book details modal and accordion |
| `quantity.js` | Manages book quantity and total price calculation |
| `order.js` | Handles demo shopping actions |
| `toast.js` | Displays notification messages |

## 🔌 Backend API

The application uses an external REST API to retrieve book data.

**Base URL:**

```text
https://books-backend.p.goit.global/books
```

| Endpoint | Description |
|---|---|
| `/category-list` | Retrieves the list of book categories |
| `/top-books` | Retrieves popular books from all categories |
| `/category?category=<name>` | Retrieves books from a specific category |
| `/<bookId>` | Retrieves detailed information about a book |

## ℹ️ Notes

Some features are implemented for demonstration purposes:

- Event registration data is displayed in the browser console and is not sent to a backend.
- Newsletter subscription data is not stored or submitted to a server.
- Add To Cart and Buy Now buttons demonstrate user interactions but do not process real purchases or maintain a shopping cart.

Full functionality for these features would require additional backend integration.

Website navigation uses anchor links to the following sections:

`#books`, `#feedback`, `#events`, `#article`, `#location`.

## 👥 Team -- WebForge -- 9 people

- Team Leader -- Vladyslav -- vladyslavdanko391-lab
- Scrum Master -- Olga -- OlgaYakovleva2011
- Develop -- Pavlo -- Pavlo-Work
- Develop -- Viktoria -- vikauvarova
- Develop -- Sofia -- SofiiiaSk
- Develop -- Eva -- 2006112014a-ai
- Develop -- Ivan -- Ivan-Kyznetsov
- Develop -- Serhii -- slepecsergejj
- Develop -- Nazarii -- nazariisaul

Booksy was developed as a collaborative team project.
=======
# team_project_booksy
>>>>>>> a52b9915808fabe886a2c0cb2031986e34e83bcc

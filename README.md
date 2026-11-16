# INFR3120 – Assignment 2: Express Portfolio Site

**Student:** Jovitha Dogga  
**Course:** INFR3120 – Web and Script Programming  
**Institution:** Ontario Tech University  
**Date:** November 15, 2026

---

## Submission Links

- **Live Portfolio:** [Still need to be added here, the render one]
- **GitHub Repository:** [https://github.com/Jovitha-Dogga/assignment2-portfolio](https://github.com/Jovitha-Dogga/assignment2-portfolio)
- **Video Presentation:** [Gotta add the video link here]

## Project Overview

Welcome to my portfolio!

This project is a personal portfolio website I built as part of INFR3120 – Web and Script Programming at Ontario Tech University for Assignment 2.

The website is built using Node.js, Express.js, and EJS. It consists of four main pages: Home, About Me, Projects, and Contact Me. Each page has its own Express route, while a shared header and footer keep the layout consistent throughout the site.

I also incorporated Bootstrap 5 for responsive styling and Font Awesome for icons. Both libraries are installed through npm rather than relying on external CDNs.

This assignment gave me the opportunity to work with Express routing, EJS templates, reusable partials, and the process of preparing a web application for cloud deployment.

## The whole Tech Stack

| Technology        | Purpose                                |
| ----------------- | -------------------------------------- |
| Node.js           | JavaScript runtime                     |
| Express.js        | Server-side framework and routing      |
| EJS               | Dynamic HTML templating                |
| Bootstrap 5       | Responsive layout and styling          |
| Font Awesome Free | Icons                                  |
| Express Generator | Initial project scaffolding            |
| Git & GitHub      | Version control and repository hosting |
| Render            | Cloud hosting and deployment           |

## The Entire Project Structure

```text
assignment2-portfolio/
│
├── public/
│   ├── images/
│   │   └── profile.jpg
│   ├── stylesheets/
│   │   └── style.css
│   └── videos/
│       └── introduction.mp4
│
├── routes/
│   ├── index.js
│   └── users.js
│
├── views/
│   ├── partials/
│   │   ├── header.ejs
│   │   └── footer.ejs
│   ├── index.ejs
│   ├── about.ejs
│   ├── projects.ejs
│   ├── contact.ejs
│   └── error.ejs
│
├── app.js
├── server.js
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

## How the Application Works

### 1. Routing – `routes/index.js`

Each portfolio page has its own GET route. Express uses `res.render()` to display the corresponding EJS template and passes page-specific information through a locals object.

| Route       | EJS Template   | Page Title |
| ----------- | -------------- | ---------- |
| `/`         | `index.ejs`    | Home       |
| `/about`    | `about.ejs`    | About Me   |
| `/projects` | `projects.ejs` | Projects   |
| `/contact`  | `contact.ejs`  | Contact Me |

For example:

```javascript
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Home' });
});
```

### 2. Layout and Reusable Partials

The `views/partials/` directory contains two shared templates:

- **header.ejs:** Contains the document structure, page head, stylesheet references, and navigation bar.
- **footer.ejs:** Contains the footer, including links to my GitHub and LinkedIn profiles.

The navigation bar also uses EJS conditional statements to highlight the currently active page.

Rather than repeating the same header and footer code in every page, each EJS template includes them using:

```ejs
<%- include('partials/header') %>

<!-- Individual page content -->

<%- include('partials/footer') %>
```

This keeps the layout consistent and makes future changes easier to manage.

### 3. Serving Bootstrap and Font Awesome

Both Bootstrap and Font Awesome are installed through npm and included in `package.json`.

In `app.js`, Express is configured to serve static files from both the `public` directory and `node_modules`:

```javascript
app.use(express.static(path.join(__dirname, 'public')));
app.use(express.static(path.join(__dirname, 'node_modules')));
```

This allows the application to access the installed libraries through paths such as:

```text
/bootstrap/dist/css/bootstrap.min.css
```

without manually copying library files into the public directory.

## Features

- Four separate portfolio pages with individual Express routes.
- Shared header and footer using EJS partials.
- Responsive page layouts using Bootstrap 5.
- Font Awesome icons throughout the interface.
- Personal biography, profile photograph, and introduction video.
- Project showcase featuring academic and independent learning projects.
- Contact form with browser-side input validation.
- GitHub and LinkedIn links in the shared footer.

**Note:** The contact form currently provides a front-end interface; it doesn't send messages to a backend service.

## External Sources and Citations

The assignment requires external code sources to be documented in the README, with non-lecture external code limited to 10% of the project.

The project was primarily developed using techniques demonstrated in the course lectures, alongside the official documentation for the technologies used. The majority of the implementation is based on course material and my own work.

### A. Course Lecture References

**INFR3120U – Tuesday, November 3, 2026**

The following lecture sections were particularly useful during development. Timestamps refer to the instructor's lecture recording.

| Timestamp       | Topic / Technique                                             |
| --------------- | ------------------------------------------------------------- |
| 0:00–44:00      | Node.js, Express, and Connect introduction                    |
| 45:04–46:38     | Installing Express Generator                                  |
| 47:43–48:15     | Generating an Express project with EJS                        |
| 50:13–50:38     | Installing project dependencies                               |
| 53:17–55:27     | Renaming `bin/www` to `server.js` and updating `package.json` |
| 57:20–58:15     | Changing `var` to `let` in `app.js`                           |
| 1:07:14–1:07:53 | MVC architecture                                              |
| 1:14:00–1:16:24 | Creating multiple Express routes                              |
| 1:27:35–1:28:35 | Installing Bootstrap through npm                              |
| 1:32:55–1:33:17 | Serving `node_modules` through Express                        |
| 1:44:53–1:45:56 | Installing Font Awesome Free                                  |
| 1:47:00–1:51:44 | Using Font Awesome icons                                      |
| 1:53:00–2:01:00 | Implementing an active navigation state with EJS conditionals |
| 2:02:45 onward  | Deployment to Render                                          |

### B. Official Documentation

The following documentation was used as a reference while working with the frameworks and tools:

- [Express Generator](https://expressjs.com/en/starter/generator.html) – Project generation.
- [Express Routing](https://expressjs.com/en/guide/routing.html) – Route handling.
- [EJS Documentation](https://ejs.co/) – Template syntax and includes.
- [Bootstrap 5 Documentation](https://getbootstrap.com/docs/5.3/) – Responsive layouts, navigation, cards, and forms.
- [Font Awesome Documentation](https://fontawesome.com/docs) – Icon usage.
- [Render Documentation](https://render.com/docs/deploy-node-express-app) – Express application deployment.
- [GitHub Documentation](https://docs.github.com/) – Repository and version-control guidance.

### C. Libraries and Licences

| Package           | Version in `package.json` | Licence                                                |
| ----------------- | ------------------------- | ------------------------------------------------------ |
| Express           | `~4.16.1`                 | MIT                                                    |
| EJS               | `~2.6.1`                  | Apache-2.0                                             |
| Bootstrap         | `^5.3.8`                  | MIT                                                    |
| Font Awesome Free | `^7.3.1`                  | CC BY 4.0 / SIL OFL 1.1 / MIT, depending on asset type |

### D. Original Content

The personal content in this portfolio, including my biography, education details, project descriptions, profile photograph, and introduction video, is my own content.

Any external source code used beyond course lecture examples is subject to the assignment's citation and 10% limit.

## Setup and Run Instructions

### Prerequisites

Make sure the following are installed:

- [Node.js](https://nodejs.org/) – Version 18 or higher recommended.
- npm – Included with Node.js.
- [Git](https://git-scm.com/) – For cloning the repository.

### Running Locally

**1. Clone the repository:**

```bash
git clone https://github.com/Jovitha-Dogga/assignment2-portfolio.git
cd assignment2-portfolio
```

**2. Install dependencies:**

```bash
npm install
```

**3. Start the application:**

```bash
npm start
```

**4. Open the website in your browser:**

```text
http://localhost:3000
```

The four portfolio pages are accessible through:

- Home: `/`
- About Me: `/about`
- Projects: `/projects`
- Contact Me: `/contact`

### Deployment – Render

The application is intended to be hosted on Render.

The deployment configuration uses:

| Setting       | Value         |
| ------------- | ------------- |
| Service Type  | Web Service   |
| Build Command | `npm install` |
| Start Command | `npm start`   |

The GitHub repository is connected to Render so that the application can be built and deployed from the project source.

The deployment process follows the instructor's Render deployment demonstration referenced in the November 3 lecture.

## Assignment Requirements Checklist

- [x] Project generated using `express --view=ejs`.
- [x] Express and Node.js application configured.
- [x] Four EJS portfolio pages created.
- [x] Four page routes implemented in `routes/index.js`.
- [x] Shared header and footer partials implemented.
- [x] GitHub and LinkedIn links included in the footer.
- [x] Bootstrap 5 installed and applied.
- [x] Font Awesome installed and applied.
- [x] Static assets organized under `public/`.
- [x] Public GitHub repository created.
- [x] Multiple meaningful commits planned throughout development.
- [ ] Render deployment completed and tested.
- [ ] Demonstration video recorded with face visible.
- [ ] Final ZIP package prepared.
- [x] New repository created for Assignment 2 rather than extending Assignment 1.
- [x] Portfolio pages implemented as EJS templates rather than HTML files.

## Author

**Jovitha Dogga**  
Bachelor of Information Technology (Honours)  
Major: Networking and IT Security  
Ontario Tech University

- GitHub: [https://github.com/Jovitha-Dogga](https://github.com/Jovitha-Dogga)
- LinkedIn: [https://www.linkedin.com/in/jovitha-dogga-32168944a/](https://www.linkedin.com/in/jovitha-dogga-32168944a/)


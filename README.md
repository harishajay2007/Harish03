🚀 Career360
India's AI-Powered Career Operating System
Smart India Hackathon — Problem ID: SIH25094
📖 Overview
Career360 is a personalized, AI-driven career and education advisor built for Indian students. It replaces one-size-fits-all career counselling with a data-backed, end-to-end journey: understand yourself, discover matching careers, see your skill gaps, follow a roadmap, and get evaluated on your resume and interview readiness — all in a single, self-contained web app.
❓ Problem Statement
Most students in India choose careers based on peer pressure, family expectations, or incomplete information, without structured self-assessment or a clear, actionable path toward their goals. Career360 solves this by combining a psychometric assessment (RIASEC), a real career-matching engine, and practical readiness tools (resume analysis, mock interviews) into one guided experience.
✨ Features
RIASEC Assessment — a structured interest-and-aptitude questionnaire that scores users across the six Holland Code dimensions (Realistic, Investigative, Artistic, Social, Enterprising, Conventional).
AI Career Matching — cosine-similarity matching between a student's RIASEC profile + skill tags and a seeded careers database, returning ranked matches with confidence scores and rationale.
Skill Gap Analysis — compares a student's current skills against the core skills required for their top career match.
Personalized Roadmap Generator — builds a step-by-step learning roadmap toward a chosen career based on missing skills.
Resume Analyzer — scores an uploaded/pasted resume against a target role and surfaces improvement areas.
Mock Interview Scoring — evaluates interview answers against a target role with structured feedback.
Persistent Local Profiles — registration/login and full user state (assessment, resume score, interview scores) persisted via localStorage, so no backend is required to demo the full flow.
In-App Assistant (Chat Widget) — a lightweight conversational helper available across screens.
Dashboard — a single view summarizing a student's profile, top career match, and progress.
🛠️ Technology Stack
Layer
Technology
UI Library
React 18 (via CDN, production.min.js)
JSX Transpiler
Babel Standalone (in-browser, no build step)
Styling
Hand-written CSS (assets/css/style.css)
Data Persistence
Browser localStorage
Hosting
GitHub Pages (static, zero backend)
CI/CD
GitHub Actions (actions/deploy-pages)
This project intentionally uses a build-free architecture — React, ReactDOM, and Babel are all loaded from CDN, and JSX is transpiled live in the browser. This keeps the project trivially deployable to GitHub Pages with zero build pipeline, at the cost of a slightly heavier first paint (Babel transpiles assets/js/app.js on load).
🏗️ Architecture
Code
┌─────────────────────────────────────────────────────────┐
│                      index.html                         │
│   (loads React, ReactDOM, Babel Standalone from CDN)     │
└───────────────────────┬───────────────────────────────────┘
                         │
              ┌──────────┴──────────┐
              │   assets/js/app.js   │  (JSX, transpiled in-browser)
              └──────────┬──────────┘
                         │
   ┌─────────────────────┼─────────────────────┐
   │                     │                     │
┌──▼───┐  ┌──────────┐ ┌──▼─────────┐ ┌────────▼────────┐
│ Auth  │  │Assessment│ │  Matching  │ │  Resume/Interview│
│Screens│  │  Engine  │ │  Engine    │ │     Scoring       │
└──┬───┘  └────┬─────┘ └─────┬──────┘ └────────┬──────────┘
   │           │              │                 │
   └───────────┴──────────────┴─────────────────┘
                         │
                ┌────────▼─────────┐
                │  localStorage DB   │
                │ (users, scores,    │
                │  assessments)      │
                └───────────────────┘

📁 Folder Structure
Code
Career360/
├── index.html                  # Entry point
├── 404.html                    # GitHub Pages fallback / redirect
├── manifest.json                # PWA manifest
├── robots.txt
├── sitemap.xml
├── favicon.ico
├── favicon.png
├── LICENSE
├── README.md
├── .gitignore
├── assets/
│   ├── css/
│   │   └── style.css           # All app styling
│   ├── js/
│   │   └── app.js              # Full application logic (React components, engines)
│   ├── images/                 # Reserved for future screenshots/assets
│   ├── icons/
│   │   ├── icon-192.png
│   │   └── icon-512.png
│   └── fonts/                  # Reserved for custom font files
└── .github/
    └── workflows/
        └── deploy.yml           # GitHub Pages CI/CD workflow

💻 Installation & Running Locally
No build step, no dependencies to install. Any static file server works:
Bash
# Clone the repository
git clone https://github.com/<your-username>/Career360.git
cd Career360

# Option A — Python
python3 -m http.server 8000

# Option B — Node (npx, no install)
npx serve .

# Then open:
http://localhost:8000

Opening index.html directly via file:// will not work reliably because assets/js/app.js is loaded as an external Babel script (<script type="text/babel" src="...">), which some browsers block under file:// due to CORS. Always serve via a local HTTP server.
🌐 GitHub Pages Deployment
This repo includes a ready-to-use GitHub Actions workflow at .github/workflows/deploy.yml.
Push this repository to GitHub (repo name: Career360, or update paths in 404.html, robots.txt, and sitemap.xml if you rename it).
In your repo, go to Settings → Pages → Build and deployment → Source, and select GitHub Actions.
Push to the main branch — the workflow will automatically build and deploy.
Your site will be live at:
Code
https://<your-username>.github.io/Career360/
Replace <your-github-username> in robots.txt, sitemap.xml, and the redirect URL in 404.html with your actual GitHub username once you know the final Pages URL.
📸 Screenshots
Add screenshots of the Home, Assessment, Results, Roadmap, Resume, Interview, and Dashboard screens here once captured — recommended path: assets/images/screenshots/.
Markdown
![Home Screen](assets/images/screenshots/home.png)
![Results Screen](assets/images/screenshots/results.png)
![Dashboard](assets/images/screenshots/dashboard.png)
🔭 Future Scope
Replace the seeded, static careers dataset with a live backend + real labour-market data (e.g. National Career Service, NASSCOM datasets).
Add server-side persistence (replacing localStorage) with proper auth and multi-device sync.
Integrate a real LLM (e.g. Claude API) for the resume analyzer, interview scorer, and chat widget, replacing heuristic scoring.
Add regional language support (Tamil, Hindi, and other Indian languages).
Add counsellor/mentor-facing dashboards for institutions.
🙏 Acknowledgements
Smart India Hackathon (SIH) for the problem statement (SIH25094).
V.S.B. Engineering College, Department of Electronics and Communication Engineering.
React, Babel, and the open-source community for the tools that made a build-free architecture possible.
📄 License
This project is licensed under the MIT License.

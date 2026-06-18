# Alice & Brian Portfolio — Local Project Setup

A Vite + React + Tailwind project. Create the folder structure below in here, paste in each file's content, then follow the setup steps at the bottom.

```
alice-brian-portfolio/
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
├── .gitignore
├── README.md
└── src/
    ├── main.jsx
    ├── App.jsx
    └── index.css
```

---

## `package.json`

```json
{
  "name": "alice-brian-portfolio",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.383.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.2.1",
    "autoprefixer": "^10.4.19",
    "postcss": "^8.4.38",
    "tailwindcss": "^3.4.3",
    "vite": "^5.2.0"
  }
}
```

---

## `vite.config.js`

```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
```

---

## `tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,jsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

---

## `postcss.config.js`

```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

---

## `index.html`

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Alice & Brian — Portfolio</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

---

## `src/main.jsx`

```javascript
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

---

## `src/index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## `src/App.jsx`

```javascript
import { useState } from "react";
import {
  Menu, X, Mail, Phone, Linkedin, ChevronDown, Code2, Database,
  Smartphone, Cpu, Plane, ShieldCheck, Sparkles, Send, CheckCircle2
} from "lucide-react";

const people = [
  {
    initial: "A",
    name: "Hsu Myat Than Sin",
    nickname: "Alice",
    role: "Software Developer",
    bio: "Software developer experienced in building scalable backend systems, APIs, and computer vision applications. Comfortable across the stack — from Oracle APEX and React Native to FastAPI and big data tools like Hadoop and Spark.",
    skills: ["Python", "FastAPI", "SQL", "Computer Vision", "Machine Learning", "React Native", "Oracle APEX"],
    email: "hsumyatthansin2000@gmail.com",
    phone: "+971 56 443 7482",
    gradient: "from-indigo-500 to-violet-500",
  },
  {
    initial: "B",
    name: "Kyaw Si Thu",
    nickname: "Brian",
    role: "Junior Data Scientist",
    bio: "Data scientist with a strong foundation in machine learning, NLP, and big data. AWS Cloud Practitioner and Google Data Analytics certified, with hands-on experience in IoT pipelines, predictive modeling, and translating data into clear business insight.",
    skills: ["Python", "Machine Learning", "NLP", "AWS", "Tableau", "SQL", "Big Data"],
    email: "",
    phone: "+971 56 166 3901",
    gradient: "from-teal-500 to-emerald-500",
  },
];

const projects = [
  {
    title: "CRM Platform",
    subtitle: "Coding Giants Dubai",
    category: "industry",
    icon: Database,
    description:
      "A web-based CRM built for Coding Giants Dubai to manage student leads, enrollments, and follow-ups in one centralized dashboard, replacing scattered spreadsheets with a streamlined system.",
    tags: ["Web App", "CRM", "Dashboard"],
  },
  {
    title: "Government Approval System",
    subtitle: "Web & Mobile · Government Services Provider",
    category: "industry",
    icon: ShieldCheck,
    description:
      "A web and native mobile solution enabling government staff to review, approve, and track service requests in real time, replacing manual approval workflows across departments.",
    tags: ["Web App", "Mobile App", "Workflow Automation"],
  },
  {
    title: "Airline Booking Management System",
    subtitle: "Industry Project",
    category: "industry",
    icon: Plane,
    description:
      "A booking management system for an airline, handling flight reservations, ticket issuance, and real-time booking status tracking for staff and customers.",
    tags: ["Booking System", "Reservations", "Web App"],
  },
  {
    title: "AspieByte",
    subtitle: "Adaptive Learning Platform · UOWD Innovation Fair",
    category: "academic",
    icon: Sparkles,
    description:
      "An inclusive learning platform that lets autistic individuals learn subjects like data science at their own pace, with real-time stress detection and behavior analysis powered by neural networks and IoT sensor data.",
    tags: ["Machine Learning", "IoT", "Accessibility"],
  },
  {
    title: "Real-Time Flavor Detection",
    subtitle: "Data Scientist Internship · Dunkin' Donuts",
    category: "industry",
    icon: Cpu,
    description:
      "A computer vision system using YOLOv8 to detect and classify donut flavors from live CCTV feeds across retail stores, paired with a FastAPI service for real-time access to results.",
    tags: ["Computer Vision", "FastAPI", "YOLOv8"],
  },
  {
    title: "German Traffic Sign Classification",
    subtitle: "Deep Learning Project",
    category: "academic",
    icon: Code2,
    description:
      "A deep learning image classifier built on Inception V3 to recognize German traffic signs, with a simple interface for uploading an image and getting an instant prediction.",
    tags: ["Deep Learning", "TensorFlow", "Image Classification"],
  },
  {
    title: "IoT Weather Station",
    subtitle: "School Project",
    category: "academic",
    icon: Cpu,
    description:
      "A real-time weather data collection system built with Arduino sensors, designed and documented using Scrum methodology for structured, iterative delivery.",
    tags: ["IoT", "Arduino", "Data Collection"],
  },
  {
    title: "Smart Attendance App",
    subtitle: "AWS Build on ASEAN Competition",
    category: "academic",
    icon: Smartphone,
    description:
      "A cloud-based smart attendance application deployed on AWS, covering the full lifecycle from system design to UI delivery.",
    tags: ["AWS", "Cloud", "Attendance System"],
  },
];

const filters = [
  { key: "all", label: "All Work" },
  { key: "industry", label: "Industry & Freelance" },
  { key: "academic", label: "Academic & Competitions" },
];

export default function App() {
  const [menuOpen, setMenuOpen] = useState(false);
  const [activeFilter, setActiveFilter] = useState("all");
  const [form, setForm] = useState({ name: "", email: "", message: "" });
  const [sent, setSent] = useState(false);

  const scrollTo = (id) => {
    document.getElementById(id)?.scrollIntoView({ behavior: "smooth" });
    setMenuOpen(false);
  };

  const handleSubmit = () => {
    if (!form.name || !form.email || !form.message) return;
    setSent(true);
  };

  const visibleProjects =
    activeFilter === "all" ? projects : projects.filter((p) => p.category === activeFilter);

  return (
    <div className="min-h-screen bg-white text-slate-800 font-sans">
      {/* NAV */}
      <nav className="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-md border-b border-slate-100">
        <div className="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
          <button onClick={() => scrollTo("home")} className="font-bold text-lg tracking-tight">
            <span className="bg-gradient-to-r from-indigo-600 to-teal-500 bg-clip-text text-transparent">
              Alice & Brian
            </span>
          </button>
          <div className="hidden md:flex items-center gap-8 text-sm font-medium text-slate-600">
            {["about", "projects", "contact"].map((id) => (
              <button
                key={id}
                onClick={() => scrollTo(id)}
                className="capitalize hover:text-indigo-600 transition-colors relative group"
              >
                {id}
                <span className="absolute -bottom-1 left-0 w-0 h-0.5 bg-indigo-600 transition-all group-hover:w-full" />
              </button>
            ))}
          </div>
          <button className="md:hidden" onClick={() => setMenuOpen(!menuOpen)} aria-label="Toggle menu">
            {menuOpen ? <X size={22} /> : <Menu size={22} />}
          </button>
        </div>
        {menuOpen && (
          <div className="md:hidden bg-white border-t border-slate-100 px-6 py-4 flex flex-col gap-4 text-sm font-medium text-slate-600">
            {["about", "projects", "contact"].map((id) => (
              <button key={id} onClick={() => scrollTo(id)} className="capitalize text-left">
                {id}
              </button>
            ))}
          </div>
        )}
      </nav>

      {/* HERO */}
      <section
        id="home"
        className="relative min-h-screen flex items-center justify-center overflow-hidden px-6 pt-16"
      >
        <div className="absolute top-1/4 -left-32 w-96 h-96 bg-indigo-200 rounded-full blur-3xl opacity-50" />
        <div className="absolute bottom-1/4 -right-32 w-96 h-96 bg-teal-200 rounded-full blur-3xl opacity-50" />
        <div className="relative text-center max-w-3xl mx-auto">
          <p className="text-indigo-600 font-semibold tracking-wide uppercase text-sm mb-4">
            Software Developer & Data Scientist
          </p>
          <h1 className="text-5xl md:text-7xl font-extrabold tracking-tight mb-6">
            <span className="bg-gradient-to-r from-indigo-600 via-violet-600 to-teal-500 bg-clip-text text-transparent">
              Alice & Brian
            </span>
          </h1>
          <p className="text-lg md:text-xl text-slate-600 mb-10 leading-relaxed">
            Two engineers building practical software and data solutions — from
            CRM platforms and government systems to machine learning and computer vision.
          </p>
          <div className="flex flex-wrap items-center justify-center gap-4">
            <button
              onClick={() => scrollTo("projects")}
              className="px-7 py-3 rounded-full bg-gradient-to-r from-indigo-600 to-violet-600 text-white font-semibold shadow-lg shadow-indigo-200 hover:shadow-xl hover:-translate-y-0.5 transition-all"
            >
              View Our Work
            </button>
            <button
              onClick={() => scrollTo("contact")}
              className="px-7 py-3 rounded-full border-2 border-slate-300 text-slate-700 font-semibold hover:border-indigo-400 hover:text-indigo-600 transition-colors"
            >
              Get In Touch
            </button>
          </div>
        </div>
        <button
          onClick={() => scrollTo("about")}
          className="absolute bottom-8 left-1/2 -translate-x-1/2 text-slate-400 animate-bounce"
          aria-label="Scroll down"
        >
          <ChevronDown size={28} />
        </button>
      </section>

      {/* ABOUT */}
      <section id="about" className="bg-slate-50 py-24 px-6">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-14">
            <p className="text-indigo-600 font-semibold uppercase text-sm tracking-wide mb-2">About Us</p>
            <h2 className="text-3xl md:text-4xl font-bold">Who We Are</h2>
          </div>
          <div className="grid md:grid-cols-2 gap-8">
            {people.map((p) => (
              <div
                key={p.nickname}
                className="bg-white rounded-2xl shadow-md p-8 hover:shadow-xl transition-shadow"
              >
                <div className="flex items-center gap-4 mb-5">
                  <div
                    className={`w-16 h-16 rounded-full bg-gradient-to-br ${p.gradient} flex items-center justify-center text-white text-2xl font-bold shrink-0`}
                  >
                    {p.initial}
                  </div>
                  <div>
                    <h3 className="text-xl font-bold leading-tight">{p.name}</h3>
                    <p className="text-sm text-slate-500">"{p.nickname}" · {p.role}</p>
                  </div>
                </div>
                <p className="text-slate-600 leading-relaxed mb-6">{p.bio}</p>
                <div className="flex flex-wrap gap-2">
                  {p.skills.map((s) => (
                    <span
                      key={s}
                      className="text-xs font-medium px-3 py-1 rounded-full bg-slate-100 text-slate-600"
                    >
                      {s}
                    </span>
                  ))}
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* PROJECTS */}
      <section id="projects" className="bg-white py-24 px-6">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-10">
            <p className="text-indigo-600 font-semibold uppercase text-sm tracking-wide mb-2">Our Work</p>
            <h2 className="text-3xl md:text-4xl font-bold">Projects</h2>
          </div>

          <div className="flex flex-wrap justify-center gap-3 mb-12">
            {filters.map((f) => (
              <button
                key={f.key}
                onClick={() => setActiveFilter(f.key)}
                className={`px-5 py-2 rounded-full text-sm font-semibold transition-colors ${
                  activeFilter === f.key
                    ? "bg-indigo-600 text-white shadow-md shadow-indigo-200"
                    : "bg-slate-100 text-slate-600 hover:bg-slate-200"
                }`}
              >
                {f.label}
              </button>
            ))}
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            {visibleProjects.map((proj) => {
              const Icon = proj.icon;
              return (
                <div
                  key={proj.title}
                  className="rounded-2xl border border-slate-200 p-6 hover:shadow-xl hover:-translate-y-1 transition-all bg-white flex flex-col"
                >
                  <div className="flex items-start justify-between mb-4">
                    <div className="w-11 h-11 rounded-xl bg-indigo-50 flex items-center justify-center text-indigo-600">
                      <Icon size={20} />
                    </div>
                    <span
                      className={`text-xs font-semibold px-2.5 py-1 rounded-full ${
                        proj.category === "industry"
                          ? "bg-indigo-100 text-indigo-700"
                          : "bg-teal-100 text-teal-700"
                      }`}
                    >
                      {proj.category === "industry" ? "Industry" : "Academic"}
                    </span>
                  </div>
                  <h3 className="font-bold text-lg leading-tight mb-1">{proj.title}</h3>
                  <p className="text-xs text-slate-400 mb-3">{proj.subtitle}</p>
                  <p className="text-sm text-slate-600 leading-relaxed mb-4 flex-grow">
                    {proj.description}
                  </p>
                  <div className="flex flex-wrap gap-2 mt-auto">
                    {proj.tags.map((t) => (
                      <span
                        key={t}
                        className="text-xs font-medium px-2.5 py-1 rounded-full bg-slate-100 text-slate-500"
                      >
                        {t}
                      </span>
                    ))}
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      </section>

      {/* CONTACT */}
      <section id="contact" className="bg-slate-50 py-24 px-6">
        <div className="max-w-5xl mx-auto">
          <div className="text-center mb-14">
            <p className="text-indigo-600 font-semibold uppercase text-sm tracking-wide mb-2">Contact</p>
            <h2 className="text-3xl md:text-4xl font-bold">Get In Touch</h2>
            <p className="text-slate-500 mt-3">Have a project in mind? We'd love to hear from you.</p>
          </div>

          <div className="grid md:grid-cols-2 gap-6 mb-12">
            {people.map((p) => (
              <div key={p.nickname} className="bg-white rounded-2xl shadow-md p-6">
                <div className="flex items-center gap-3 mb-4">
                  <div
                    className={`w-10 h-10 rounded-full bg-gradient-to-br ${p.gradient} flex items-center justify-center text-white font-bold text-sm shrink-0`}
                  >
                    {p.initial}
                  </div>
                  <h3 className="font-bold">{p.nickname}</h3>
                </div>
                <div className="space-y-3 text-sm text-slate-600">
                  {p.email && (
                    <div className="flex items-center gap-3">
                      <Mail size={16} className="text-indigo-500 shrink-0" />
                      <span className="break-all">{p.email}</span>
                    </div>
                  )}
                  <div className="flex items-center gap-3">
                    <Phone size={16} className="text-indigo-500 shrink-0" />
                    <span>{p.phone}</span>
                  </div>
                  <div className="flex items-center gap-3">
                    <Linkedin size={16} className="text-indigo-500 shrink-0" />
                    <span className="text-slate-400">LinkedIn profile (add link)</span>
                  </div>
                </div>
              </div>
            ))}
          </div>

          <div className="max-w-xl mx-auto bg-white rounded-2xl shadow-md p-8">
            {sent ? (
              <div className="flex flex-col items-center text-center py-6">
                <CheckCircle2 className="text-emerald-500 mb-3" size={40} />
                <h3 className="font-bold text-lg mb-1">Message sent!</h3>
                <p className="text-slate-500 text-sm">We'll get back to you as soon as possible.</p>
              </div>
            ) : (
              <div className="space-y-4">
                <div>
                  <label className="block text-sm font-medium text-slate-600 mb-1.5">Name</label>
                  <input
                    type="text"
                    value={form.name}
                    onChange={(e) => setForm({ ...form, name: e.target.value })}
                    className="w-full px-4 py-2.5 rounded-lg border border-slate-200 focus:outline-none focus:ring-2 focus:ring-indigo-400 text-sm"
                    placeholder="Your name"
                  />
                </div>
                <div>
                  <label className="block text-sm font-medium text-slate-600 mb-1.5">Email</label>
                  <input
                    type="email"
                    value={form.email}
                    onChange={(e) => setForm({ ...form, email: e.target.value })}
                    className="w-full px-4 py-2.5 rounded-lg border border-slate-200 focus:outline-none focus:ring-2 focus:ring-indigo-400 text-sm"
                    placeholder="you@example.com"
                  />
                </div>
                <div>
                  <label className="block text-sm font-medium text-slate-600 mb-1.5">Message</label>
                  <textarea
                    value={form.message}
                    onChange={(e) => setForm({ ...form, message: e.target.value })}
                    rows={4}
                    className="w-full px-4 py-2.5 rounded-lg border border-slate-200 focus:outline-none focus:ring-2 focus:ring-indigo-400 text-sm resize-none"
                    placeholder="Tell us about your project..."
                  />
                </div>
                <button
                  type="button"
                  onClick={handleSubmit}
                  className="w-full flex items-center justify-center gap-2 px-6 py-3 rounded-lg bg-gradient-to-r from-indigo-600 to-violet-600 text-white font-semibold hover:shadow-lg transition-shadow"
                >
                  <Send size={16} />
                  Send Message
                </button>
              </div>
            )}
          </div>
        </div>
      </section>

      <footer className="text-center py-8 text-slate-400 text-sm bg-white border-t border-slate-100">
        © 2026 Alice & Brian. All rights reserved.
      </footer>
    </div>
  );
}
```

---

## `.gitignore`

```
node_modules
dist
.DS_Store
.env
```

---

## `README.md`

```markdown
# Alice & Brian Portfolio

A one-page portfolio built with React, Vite, and Tailwind CSS.

## Getting Started

\`\`\`bash
npm install
npm run dev
\`\`\`

Open http://localhost:5173 in your browser.

## Build for production

\`\`\`bash
npm run build
\`\`\`
```

---

## Setup Steps

1. **Create the folder** in VS Code: `File → Open Folder` after creating `alice-brian-portfolio/` somewhere on your machine, then create the subfolders/files above exactly as shown.
2. **Open a terminal in VS Code** (`` Ctrl+` `` / `` Cmd+` ``) and run:
   ```
   npm install
   ```
3. **Run the dev server:**
   ```
   npm run dev
   ```
   Then open the local URL it prints (usually `http://localhost:5173`).

## Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit: portfolio site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

(Create the empty repo on GitHub first, then copy its URL into the `git remote add` command above.)

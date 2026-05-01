# 🏥 MediCare — Healthcare Patient Management Dashboard

A full-featured React capstone project built with Vite, Redux Toolkit, React Router, Chart.js, and CSS Modules.

---

## 📁 Project Structure

```
medicare-dashboard/
├── index.html
├── vite.config.js
├── package.json
└── src/
    ├── main.jsx                     # App entry point
    ├── App.jsx                      # Routes + lazy loading
    ├── styles/
    │   └── globals.css              # CSS variables, dark mode, reset
    ├── data/
    │   └── mockData.js              # Patient + appointment data
    ├── hooks/
    │   └── useDebounce.js           # Debounced search hook
    ├── store/
    │   ├── index.js                 # Redux store config
    │   ├── patientsSlice.js         # CRUD + filter/sort/search
    │   └── uiSlice.js               # Dark mode + notifications
    ├── components/
    │   ├── Layout/
    │   │   ├── Layout.jsx           # Sidebar + topbar shell
    │   │   └── Layout.module.css
    │   ├── UI/
    │   │   ├── index.jsx            # MetricCard, Badge, Avatar, Card...
    │   │   ├── Spinner.jsx
    │   │   └── UI.module.css
    │   └── Patients/
    │       ├── AddPatientModal.jsx  # Multi-step form with validation
    │       └── AddPatientModal.module.css
    └── pages/
        ├── Dashboard.jsx            # Charts, metrics, today's appointments
        ├── Dashboard.module.css
        ├── Patients.jsx             # Table with CRUD, filter, sort, pagination
        ├── Patients.module.css
        ├── PatientDetail.jsx        # Individual patient view + edit
        ├── PatientDetail.module.css
        ├── Appointments.jsx         # Timeline + calendar view
        ├── Appointments.module.css
        ├── Analytics.jsx            # Bar + line charts, stats
        ├── Analytics.module.css
        ├── Records.jsx              # Medical records grid
        └── Records.module.css
```

---

## ✅ SOP Requirements Covered

| Requirement               | Implementation                                      |
|---------------------------|-----------------------------------------------------|
| React (Vite) + ES6+       | Vite scaffold, arrow functions, destructuring, etc. |
| Redux Toolkit             | `patientsSlice` + `uiSlice` with selectors          |
| React Router              | 6 routes + lazy loading via `React.lazy`            |
| Fetch API / Axios         | Axios installed; mock data simulates API shape      |
| CSS Modules               | Every component has `.module.css`                   |
| Lazy loading              | All pages wrapped in `React.lazy` + `Suspense`      |
| Pagination                | Patients table — 6 per page with page controls      |
| Search + filter + sort    | Redux-powered, debounced search + dept/status pills |
| Dark mode toggle          | Full CSS variable swap via `data-theme` attribute   |
| Dashboard with charts     | Line, Doughnut, Bar via Chart.js + react-chartjs-2  |
| Multi-step form           | Add Patient modal — 2 steps with validation         |
| CRUD operations           | Add, view, edit, delete patients                    |
| Error handling            | `EmptyState` fallback, form validation, 404 redirect|
| Deployment ready          | `npm run build` → drop `dist/` on Vercel/Netlify    |

---

## 🚀 Getting Started

### 1. Install dependencies
```bash
npm install
```

### 2. Run dev server
```bash
npm run dev
```
Open [http://localhost:5173](http://localhost:5173)

### 3. Build for production
```bash
npm run build
```

### 4. Deploy to Vercel
```bash
npm install -g vercel
vercel
```
Or drag the `dist/` folder into [netlify.com/drop](https://app.netlify.com/drop)

---

## 🌐 Connect a Real API

Replace `src/data/mockData.js` with live calls. Example using **disease.sh** (free, no key):

```js
// src/hooks/useDiseaseData.js
import { useEffect, useState } from 'react'
import axios from 'axios'

export function useCountryStats(country = 'india') {
  const [data, setData] = useState(null)
  const [loading, setLoading] = useState(true)
  const [error, setError] = useState(null)

  useEffect(() => {
    axios.get(`https://disease.sh/v3/covid-19/countries/${country}`)
      .then(res => { setData(res.data); setLoading(false) })
      .catch(err => { setError(err.message); setLoading(false) })
  }, [country])

  return { data, loading, error }
}
```

Other free APIs:
- **OpenFDA** — drug adverse events: `https://api.fda.gov/drug/event.json`
- **disease.sh** — global health stats: `https://disease.sh/v3/covid-19/all`
- **WHO GHO** — global health observatory: `https://ghoapi.azureedge.net/api/`

---

## 🔑 Features Walkthrough

| Page           | Features                                                       |
|----------------|----------------------------------------------------------------|
| **Dashboard**  | Metric cards, line chart, donut chart, appointments, patient list |
| **Patients**   | Search (debounced), dept + status filter pills, sort by any column, pagination, add/delete |
| **Patient Detail** | View all vitals, edit status/BP/HR inline, go back         |
| **Appointments** | Today's timeline + appointment cards with status badges     |
| **Analytics**  | Monthly admissions vs discharges bar chart, line trend, dept stats |
| **Records**    | Medical records grid, filter by record type                    |

---

## 📦 Tech Stack

| Tool             | Purpose                      |
|------------------|------------------------------|
| React 18         | UI framework                 |
| Vite             | Build tool & dev server      |
| Redux Toolkit    | Global state management      |
| React Router v6  | Client-side routing          |
| Chart.js         | Data visualisation           |
| react-chartjs-2  | React wrapper for Chart.js   |
| Axios            | HTTP client (ready to use)   |
| CSS Modules      | Scoped component styles      |

---

## 🔒 Anti-Plagiarism Note

This project uses the **Healthcare** domain with a **custom patient management** feature set (CRUD + analytics + multi-step forms). To make it 100% unique for submission:
- Connect a different public API (OpenFDA, WHO GHO, etc.)
- Add authentication (Firebase Auth or Auth0)
- Extend with a real-time notification system (WebSocket / polling)

---

*Built for Capstone Project — React Frontend Engineering*

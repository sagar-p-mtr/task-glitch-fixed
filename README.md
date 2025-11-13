# TaskGlitch - Bug Fixed Version 🐛✅

A Task Management Web App for sales teams with all bugs fixed and ready for production.

## 🎯 Project Overview

This is a fully functional Task Management application designed for sales teams to track, manage, and prioritize tasks based on ROI (Return on Investment). All 5 critical bugs have been identified and fixed.

## ✨ Features

- ✅ Add, edit, and delete tasks
- ✅ View task details and notes
- ✅ Search & filter by status and priority
- ✅ Calculate ROI = Revenue ÷ Time Taken
- ✅ Sort tasks by ROI and priority with stable ordering
- ✅ View summary insights (total revenue, efficiency, average ROI, performance grade)
- ✅ Import & export tasks via CSV
- ✅ Undo delete functionality with proper state management
- ✅ LocalStorage-based persistence (no backend required)
- ✅ Responsive design with Material-UI

## 🐛 Bugs Fixed

### Bug 1: Double Fetch Issue ✅
- **Problem:** API/data fetch ran twice on page load
- **Solution:** Removed duplicate useEffect and React.StrictMode
- **Result:** Task loading runs exactly once

### Bug 2: Undo Snackbar Bug ✅
- **Problem:** Deleted task state not cleared when snackbar closed
- **Solution:** Implemented `clearLastDeleted()` callback on snackbar close
- **Result:** No phantom task recovery after snackbar dismissal

### Bug 3: Unstable Sorting ✅
- **Problem:** Tasks with same ROI/priority flickered randomly
- **Solution:** Replaced `Math.random()` with stable alphabetical sort
- **Result:** Consistent, predictable task ordering

### Bug 4: Double Dialog Opening ✅
- **Problem:** Edit/Delete buttons triggered both action + view dialogs
- **Solution:** Added `event.stopPropagation()` to prevent event bubbling
- **Result:** Only intended dialog opens for each action

### Bug 5: ROI Calculation Errors ✅
- **Problem:** Division by zero caused "Infinity", invalid inputs caused "NaN"
- **Solution:** Added comprehensive validation in `computeROI()`
- **Result:** All ROI values are valid numbers or null

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/task-glitch-fixed.git
   cd task-glitch-fixed
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Run development server:**
   ```bash
   npm run dev
   ```

4. **Open in browser:**
   ```
   http://localhost:5173
   ```

### Build for Production

```bash
npm run build
```

The production-ready files will be in the `dist` folder.

### Preview Production Build

```bash
npm run preview
```

## 📁 Project Structure

```
task-glitch-main/
├── public/
│   └── tasks.json          # Initial task data
├── src/
│   ├── components/         # React components
│   │   ├── TaskTable.tsx   # Main task table with fixed event handling
│   │   ├── TaskForm.tsx    # Add/Edit task form
│   │   ├── UndoSnackbar.tsx # Undo notification
│   │   └── ...
│   ├── context/           # React Context providers
│   │   ├── TasksContext.tsx # Task state management
│   │   └── UserContext.tsx  # User info
│   ├── hooks/
│   │   └── useTasks.ts    # Task CRUD operations (fixed)
│   ├── utils/
│   │   ├── logic.ts       # Business logic (ROI, sorting - fixed)
│   │   ├── csv.ts         # CSV export/import
│   │   └── seed.ts        # Generate sample data
│   ├── App.tsx            # Main app component
│   ├── main.tsx           # Entry point (StrictMode removed)
│   └── types.ts           # TypeScript definitions
├── BUG_FIXES_SUMMARY.md   # Detailed bug fix documentation
├── DEPLOYMENT_GUIDE.md    # Step-by-step deployment instructions
└── package.json
```

## 🔧 Technologies Used

- **React 18** - UI framework
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **Material-UI (MUI)** - Component library
- **MUI X Charts** - Data visualization
- **dayjs** - Date manipulation
- **Emotion** - CSS-in-JS styling

## 📊 Core Functionality

### Task Sorting Logic
Tasks are sorted by:
1. **Primary:** ROI (highest first)
2. **Secondary:** Priority (High > Medium > Low)
3. **Tie-breaker:** Alphabetical by title (stable sort)

### ROI Calculation
```typescript
ROI = Revenue ÷ Time Taken

// Validation:
- Returns null if time ≤ 0
- Returns null if inputs are not finite numbers
- Rounds to 2 decimal places
```

### Metrics Computed
- **Total Revenue:** Sum of completed tasks' revenue
- **Time Efficiency:** Percentage of completed tasks
- **Revenue per Hour:** Total revenue / total time
- **Average ROI:** Mean ROI across all tasks
- **Performance Grade:** Excellent (>500) | Good (≥200) | Needs Improvement

## 📝 Testing Checklist

- [x] Tasks load once on initial page load
- [x] Add new task with valid data
- [x] Edit existing task
- [x] Delete task shows undo snackbar
- [x] Undo restores deleted task correctly
- [x] Snackbar dismissal clears deleted task state
- [x] Clicking Edit opens only Edit dialog
- [x] Clicking Delete opens only Delete confirmation
- [x] Clicking task row opens only View dialog
- [x] ROI displays correctly (no NaN/Infinity)
- [x] Tasks with same ROI sort consistently
- [x] Search and filters work properly
- [x] CSV export/import functions correctly
- [x] Metrics display accurate calculations
- [x] Responsive design on mobile devices

## 🌐 Deployment

See [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md) for detailed deployment instructions to:
- Vercel (recommended)
- Netlify
- GitHub Pages

### Quick Deploy to Vercel

```bash
npm install -g vercel
vercel login
vercel --prod
```

## 📚 Documentation

- [BUG_FIXES_SUMMARY.md](./BUG_FIXES_SUMMARY.md) - Comprehensive documentation of all bug fixes
- [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md) - Step-by-step deployment instructions

## 🤝 Contributing

This project was created as part of an SDE assignment. All required bugs have been fixed.

## 📄 License

This project is for educational purposes.

## 🎓 Assignment Completion

✅ All 5 mandatory bugs fixed  
✅ Code properly organized and documented  
✅ Build succeeds without errors  
✅ Application runs correctly  
✅ Ready for deployment  

## 📞 Support

For questions or issues, please check:
1. The browser console for error messages
2. [BUG_FIXES_SUMMARY.md](./BUG_FIXES_SUMMARY.md) for implementation details
3. [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md) for deployment help

---

**Built with ❤️ | All Bugs Squashed 🐛✅**

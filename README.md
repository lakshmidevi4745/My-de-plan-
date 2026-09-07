<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GCP Data Engineer 112-Day Interview Mastery Platform</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Google Fonts: Inter & JetBrains Mono -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            mono: ['JetBrains Mono', 'monospace'],
          },
          colors: {
            brand: {
              50: '#eef2ff',
              100: '#e0e7ff',
              500: '#6366f1',
              600: '#4f46e5',
              700: '#4338ca',
            },
            gcp: {
              blue: '#4285F4',
              red: '#EA4335',
              yellow: '#FBBC05',
              green: '#34A853',
              dark: '#0a0e1a',
            }
          }
        }
      }
    }
  </script>

  <style>
    body {
      font-family: 'Inter', sans-serif;
      background-color: #070a12;
      color: #f1f5f9;
      overflow-x: hidden;
    }
    code, pre {
      font-family: 'JetBrains Mono', monospace;
    }
    ::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #0b0f19;
    }
    ::-webkit-scrollbar-thumb {
      background: #334155;
      border-radius: 9999px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #475569;
    }
    .active-day-pill {
      background: linear-gradient(135deg, #4f46e5 0%, #2563eb 100%);
      box-shadow: 0 4px 14px 0 rgba(79, 70, 229, 0.45);
      border-color: #818cf8;
    }
    .card-glass {
      background: rgba(13, 19, 33, 0.85);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(255, 255, 255, 0.07);
    }
    .card-glass:hover {
      border-color: rgba(99, 102, 241, 0.35);
    }
    .answer-blur {
      filter: blur(5px);
      user-select: none;
      transition: filter 0.25s ease-in-out;
    }
    .answer-blur:hover, .answer-blur.unblurred {
      filter: blur(0px);
      user-select: auto;
    }
  </style>
</head>
<body class="min-h-screen flex flex-col bg-[#070a12] text-slate-100">

  <header class="sticky top-0 z-50 border-b border-slate-800/80 bg-[#090e1b]/95 backdrop-blur-md">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
      <div class="flex items-center space-x-3">
        <div class="h-10 w-10 rounded-xl bg-gradient-to-tr from-indigo-600 via-blue-600 to-sky-400 flex items-center justify-center text-white font-bold shadow-lg shadow-indigo-500/30">
          <i class="fa-solid fa-cloud-bolt text-lg"></i>
        </div>
        <div>
          <div class="flex items-center space-x-2">
            <span class="font-black text-lg tracking-tight bg-gradient-to-r from-white via-slate-100 to-slate-400 bg-clip-text text-transparent">GCP Data Engineer</span>
            <span class="text-[11px] px-2 py-0.5 rounded-full font-bold bg-indigo-500/20 text-indigo-300 border border-indigo-500/30">112-Day Blueprint</span>
          </div>
          <p class="text-[11px] text-slate-400 hidden sm:block">5 Questions Daily • Engine Mechanics • Real-World Analogies • Out-Of-The-Box Edge Cases</p>
        </div>
      </div>

      <!-- Quick Metrics and Action Controls -->
      <div class="flex items-center space-x-2.5 sm:space-x-3">
        <div class="hidden lg:flex items-center space-x-4 px-3 py-1.5 rounded-xl bg-slate-900/90 border border-slate-800 text-xs">
          <div class="flex items-center space-x-1.5 text-slate-300">
            <i class="fa-solid fa-fire text-amber-500"></i>
            <span>Streak: <strong id="streakCount" class="text-amber-400">14 Days</strong></span>
          </div>
          <div class="h-3 w-px bg-slate-700"></div>
          <div class="flex items-center space-x-1.5 text-slate-300">
            <i class="fa-solid fa-circle-check text-emerald-500"></i>
            <span>Mastered: <strong id="masteredCount" class="text-emerald-400">0</strong> / 560</span>
          </div>
        </div>

        <button id="crossCloudModalBtn" class="flex items-center space-x-1.5 px-3 py-1.5 rounded-xl bg-sky-600/25 hover:bg-sky-600/40 text-sky-200 border border-sky-500/30 text-xs font-semibold transition" title="GCP vs AWS vs Azure Architecture Matrix">
          <i class="fa-solid fa-cloud-arrow-up text-sky-400"></i>
          <span class="hidden md:inline">Cross-Cloud Hub</span>
        </button>

        <button id="randomDrillBtn" class="px-3 py-1.5 rounded-xl bg-purple-600/20 hover:bg-purple-600/30 text-purple-300 border border-purple-500/30 text-xs font-semibold flex items-center space-x-1.5 transition" title="Test a random question under pressure">
          <i class="fa-solid fa-dice text-purple-400"></i>
          <span class="hidden md:inline">Random Drill</span>
        </button>

        <button id="openTimerBtn" class="flex items-center space-x-1.5 px-3 py-1.5 rounded-xl bg-indigo-600/25 hover:bg-indigo-600/40 text-indigo-200 border border-indigo-500/30 text-xs font-semibold transition" title="Practice 2-Minute Interview Speech">
          <i class="fa-solid fa-stopwatch text-indigo-400"></i>
          <span class="hidden sm:inline">Mock Pitch Timer</span>
        </button>

        <button id="syllabusModalBtn" class="flex items-center space-x-1.5 px-3 py-1.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs border border-slate-700 transition">
          <i class="fa-solid fa-map"></i>
          <span>Curriculum</span>
        </button>
      </div>
    </div>
  </header>

  <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 space-y-6">
    
    <!-- Top Filter Bar & Months Tabs -->
    <div class="space-y-4">
      <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
        <!-- Month Selection Tabs -->
        <div class="flex flex-wrap items-center gap-2" id="monthTabsContainer">
          <!-- Rendered dynamically -->
        </div>

        <!-- Search Bar and Flashcard Toggle -->
        <div class="flex items-center space-x-3 w-full md:w-auto">
          <div class="relative flex-1 md:w-72">
            <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-slate-400 text-xs"></i>
            <input 
              type="text" 
              id="globalSearchInput" 
              placeholder="Search concepts (e.g. Broadcast join, SCD-2, Slot skew)..." 
              class="w-full bg-slate-900 border border-slate-800 rounded-xl pl-9 pr-3 py-2 text-xs text-slate-200 focus:outline-none focus:border-indigo-500 transition placeholder-slate-500"
            >
          </div>
          
          <button id="flashcardModeToggle" class="px-3 py-2 rounded-xl bg-slate-900 border border-slate-800 hover:border-slate-700 text-xs text-slate-300 flex items-center space-x-2 transition" title="Toggle Answer Blur for active self-testing">
            <i class="fa-solid fa-brain text-purple-400"></i>
            <span class="hidden sm:inline">Recall Mode</span>
          </button>
        </div>
      </div>

      <div class="bg-slate-900/60 p-3 rounded-2xl border border-slate-800/80">
        <div class="flex items-center justify-between mb-2">
          <div class="flex items-center space-x-2">
            <span class="text-xs font-semibold uppercase tracking-wider text-slate-400" id="currentWeekTitle">Week 1: SQL + Python + Data Engineering Fundamentals</span>
            <span class="text-[10px] bg-slate-800 text-slate-400 px-2 py-0.5 rounded-full" id="dayRangeBadge">Days 1 - 7</span>
          </div>
          <div class="flex items-center space-x-2 text-xs">
            <!-- Direct Day Jump input box -->
            <div class="flex items-center space-x-1 bg-slate-950 border border-slate-800 rounded-lg px-2 py-1">
              <span class="text-[10px] text-slate-500 font-mono">Day:</span>
              <input type="number" id="jumpDayInput" min="1" max="112" placeholder="1-112" class="w-12 bg-transparent text-xs text-indigo-300 focus:outline-none font-mono text-center" aria-label="Jump to day">
              <button id="jumpDayBtn" class="px-1.5 py-0.5 rounded bg-indigo-600/30 hover:bg-indigo-600 text-indigo-200 hover:text-white text-[10px] font-semibold transition" title="Jump to Day">Go</button>
            </div>
            <div class="h-4 w-px bg-slate-800 hidden sm:block"></div>
            <button id="prevDayBtn" class="p-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-300 transition" title="Previous Day"><i class="fa-solid fa-chevron-left"></i></button>
            <span class="font-mono text-indigo-400 font-bold px-1" id="currentDayBadge">Day 1</span>
            <button id="nextDayBtn" class="p-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-300 transition" title="Next Day"><i class="fa-solid fa-chevron-right"></i></button>
          </div>
        </div>

        <!-- Horizontal scrollable Day selector pills -->
        <div class="flex items-center space-x-1.5 overflow-x-auto pb-1 pt-1" id="dayPillsContainer">
          <!-- Day pills generated by JS -->
        </div>
      </div>
    </div>

    <div class="relative overflow-hidden rounded-2xl bg-gradient-to-r from-slate-900 via-indigo-950/40 to-slate-900 border border-slate-800 p-5">
      <div class="absolute -right-10 -top-10 w-48 h-48 bg-indigo-500/10 rounded-full blur-3xl pointer-events-none"></div>
      <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 relative z-10">
        <div class="space-y-1">
          <div class="flex items-center space-x-2">
            <span class="px-2.5 py-0.5 rounded-full text-[11px] font-bold uppercase tracking-wider bg-indigo-500/20 text-indigo-300 border border-indigo-500/30" id="heroPhaseLabel">Month 1 • Foundation</span>
            <span class="text-slate-400 text-xs" id="heroFocusSubtext">SQL Joins • ETL vs ELT • Python Primitives • BigQuery Specs • Airflow DAGs</span>
          </div>
          <h1 class="text-xl sm:text-2xl font-black text-white" id="heroDayHeading">Day 1: Architectural Core & Engine Fundamentals</h1>
          <p class="text-xs sm:text-sm text-slate-300 max-w-3xl" id="heroDayGoal">
            Master the foundational memory models, engine execution semantics, and distributed storage principles that form the basis for 80% of data pipeline designs.
          </p>
        </div>

        <div class="flex items-center space-x-3">
          <button id="markAllMasteredBtn" class="px-3.5 py-2 rounded-xl bg-emerald-600/20 hover:bg-emerald-600/30 text-emerald-300 border border-emerald-500/30 text-xs font-semibold transition flex items-center space-x-2">
            <i class="fa-solid fa-check-double"></i>
            <span>Mark Day Complete</span>
          </button>
        </div>
      </div>
    </div>

    <div class="flex items-center space-x-2 overflow-x-auto pb-1 text-xs text-slate-400" id="categoryFilterBar">
      <span class="text-[11px] font-medium text-slate-500 uppercase tracking-wider mr-1">Filter:</span>
      <button class="cat-filter-btn active px-3 py-1 rounded-lg bg-indigo-600 text-white font-medium" data-cat="all">All (5)</button>
      <button class="cat-filter-btn px-3 py-1 rounded-lg bg-slate-900 border border-slate-800 hover:border-slate-700 text-slate-300" data-cat="Q1 — SQL / Python / Modeling">Q1: SQL / Modeling</button>
      <button class="cat-filter-btn px-3 py-1 rounded-lg bg-slate-900 border border-slate-800 hover:border-slate-700 text-slate-300" data-cat="Q2 — Core DE / dbt">Q2: Core DE & dbt</button>
      <button class="cat-filter-btn px-3 py-1 rounded-lg bg-slate-900 border border-slate-800 hover:border-slate-700 text-slate-300" data-cat="Q3 — Spark / Containers (Docker)">Q3: Spark & Docker</button>
      <button class="cat-filter-btn px-3 py-1 rounded-lg bg-slate-900 border border-slate-800 hover:border-slate-700 text-slate-300" data-cat="Q4 — GCP & Cross-Cloud (AWS/Azure)">Q4: GCP & Cross-Cloud</button>
      <button class="cat-filter-btn px-3 py-1 rounded-lg bg-slate-900 border border-slate-800 hover:border-slate-700 text-slate-300" data-cat="Q5 — Airflow / Terraform / CI-CD">Q5: Orchestration & IaC</button>
    </div>

    <div class="space-y-6" id="questionsContainer">
      <!-- Injected dynamically by JavaScript -->
    </div>

    <div class="flex items-center justify-between py-6 border-t border-slate-800/80">
      <button id="footerPrevBtn" class="flex items-center space-x-2 px-4 py-2 rounded-xl bg-slate-900 border border-slate-800 hover:border-indigo-500/50 text-slate-300 text-xs font-semibold transition">
        <i class="fa-solid fa-arrow-left"></i>
        <span>Previous Day</span>
      </button>

      <div class="text-xs text-slate-400 font-mono">
        Mastery: <span class="text-indigo-400 font-bold" id="progressPercentage">0%</span> of 560 Questions
      </div>

      <button id="footerNextBtn" class="flex items-center space-x-2 px-4 py-2 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-semibold shadow-lg shadow-indigo-600/30 transition">
        <span>Next Day</span>
        <i class="fa-solid fa-arrow-right"></i>
      </button>
    </div>
  </main>

  <!-- 2-Minute Speech Pitch Timer Modal -->
  <div id="timerModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-slate-900 border border-slate-800 rounded-2xl max-w-md w-full p-6 space-y-5 relative shadow-2xl">
      <button id="closeTimerModalBtn" class="absolute top-4 right-4 text-slate-400 hover:text-white transition">
        <i class="fa-solid fa-xmark text-lg"></i>
      </button>

      <div class="flex items-center space-x-3">
        <div class="h-10 w-10 rounded-xl bg-amber-500/20 text-amber-400 border border-amber-500/30 flex items-center justify-center text-lg">
          <i class="fa-solid fa-stopwatch"></i>
        </div>
        <div>
          <h3 class="font-bold text-white text-base">2-Minute Pitch Drill</h3>
          <p class="text-xs text-slate-400">Can you explain this architecture without stuttering?</p>
        </div>
      </div>

      <div class="bg-slate-950 p-6 rounded-2xl border border-slate-800/80 text-center space-y-2">
        <div class="text-5xl font-mono font-black text-indigo-400 tracking-wider" id="timerDisplay">02:00</div>
        <p class="text-[11px] uppercase tracking-widest text-slate-400 font-semibold" id="timerStatusLabel">Ready to Speak</p>
      </div>

      <div class="p-3.5 rounded-xl bg-slate-800/50 border border-slate-700/50 text-xs text-slate-300 space-y-1">
        <span class="font-bold text-amber-400"><i class="fa-solid fa-bolt mr-1"></i> The Winning Interview Pitch Formula:</span>
        <ol class="list-decimal list-inside space-y-1 text-[11px] text-slate-300 pt-1">
          <li><strong>00:00 - 00:30:</strong> Crisp Definition (Zero filler, immediate clarity).</li>
          <li><strong>00:30 - 01:15:</strong> Under-the-hood engine mechanics (Memory, Network, Disk).</li>
          <li><strong>01:15 - 01:45:</strong> 10-second production example with real metrics.</li>
          <li><strong>01:45 - 02:00:</strong> Call out the edge-case trap before the interviewer asks!</li>
        </ol>
      </div>

      <div class="flex items-center space-x-3">
        <button id="startTimerBtn" class="flex-1 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-bold transition shadow-lg shadow-indigo-600/30">
          Start Timer
        </button>
        <button id="resetTimerBtn" class="px-4 py-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-semibold transition">
          Reset
        </button>
      </div>
    </div>
  </div>

  <!-- Full Curriculum Syllabus Modal -->
  <div id="syllabusModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-slate-900 border border-slate-800 rounded-2xl max-w-4xl w-full max-h-[85vh] flex flex-col p-6 relative shadow-2xl">
      <div class="flex items-center justify-between pb-4 border-b border-slate-800">
        <div>
          <h3 class="font-bold text-white text-lg">112-Day Master Curriculum Syllabus</h3>
          <p class="text-xs text-slate-400">Click any day to jump directly into the interview drill</p>
        </div>
        <button id="closeSyllabusModalBtn" class="text-slate-400 hover:text-white transition">
          <i class="fa-solid fa-xmark text-lg"></i>
        </button>
      </div>

      <div class="overflow-y-auto py-4 space-y-4 pr-1 text-xs" id="syllabusModalContent">
        <!-- Injected dynamically -->
      </div>
    </div>
  </div>

  <!-- Cross-Cloud Comparative Hub Modal: GCP vs AWS vs Azure -->
  <div id="crossCloudModal" class="fixed inset-0 z-50 bg-black/85 backdrop-blur-md hidden flex items-center justify-center p-4">
    <div class="bg-[#0b1120] border border-slate-700/80 rounded-2xl max-w-5xl w-full max-h-[88vh] flex flex-col p-6 relative shadow-2xl overflow-hidden">
      <!-- Modal Header -->
      <div class="flex items-center justify-between pb-4 border-b border-slate-800">
        <div class="space-y-0.5">
          <div class="flex items-center space-x-2">
            <span class="px-2.5 py-0.5 rounded-full text-[10px] font-bold uppercase tracking-wider bg-sky-500/20 text-sky-300 border border-sky-500/30">
              Enterprise Rosetta Stone
            </span>
            <h3 class="font-black text-white text-lg sm:text-xl">Cross-Cloud Data Platform Comparison</h3>
          </div>
          <p class="text-xs text-slate-400">Compare GCP, AWS, and Azure equivalents, architectural differences, and when to pick each in technical interviews.</p>
        </div>
        <button id="closeCrossCloudModalBtn" class="text-slate-400 hover:text-white p-2 rounded-lg bg-slate-800 hover:bg-slate-700 transition">
          <i class="fa-solid fa-xmark text-lg"></i>
        </button>
      </div>

      <!-- Search & Category Filters for Matrix -->
      <div class="flex flex-wrap items-center justify-between gap-3 pt-4 pb-2">
        <div class="flex flex-wrap gap-1.5 text-xs" id="matrixFilterPills">
          <button class="matrix-filter active px-2.5 py-1 rounded-lg bg-sky-600 text-white font-medium" data-service="all">All Services</button>
          <button class="matrix-filter px-2.5 py-1 rounded-lg bg-slate-900 border border-slate-800 text-slate-300 hover:border-slate-700" data-service="modeling">dbt vs Dataform vs ETL</button>
          <button class="matrix-filter px-2.5 py-1 rounded-lg bg-slate-900 border border-slate-800 text-slate-300 hover:border-slate-700" data-service="warehouse">Warehousing</button>
          <button class="matrix-filter px-2.5 py-1 rounded-lg bg-slate-900 border border-slate-800 text-slate-300 hover:border-slate-700" data-service="compute">Spark / Compute</button>
          <button class="matrix-filter px-2.5 py-1 rounded-lg bg-slate-900 border border-slate-800 text-slate-300 hover:border-slate-700" data-service="orchestration">Orchestration & CI/CD</button>
          <button class="matrix-filter px-2.5 py-1 rounded-lg bg-slate-900 border border-slate-800 text-slate-300 hover:border-slate-700" data-service="streaming">Streaming & Storage</button>
        </div>
        <input 
          type="text" 
          id="matrixSearchInput" 
          placeholder="Filter (e.g., Dataform, dbt, R

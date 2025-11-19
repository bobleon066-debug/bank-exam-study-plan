
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bank Exam Master Roadmap 2025</title>
    <!-- Chosen Palette: Trustworthy Blue & Energetic Orange -->
    <!-- Application Structure Plan: SPA Dashboard. 
         - Sidebar/Top Nav: For quick switching between Phases and Habits.
         - Dashboard View: High-level metrics (Hours breakdown) using Chart.js Canvas.
         - Phase Views: Clean data tables for daily schedules.
         - Logic: Vanilla JS to handle tab switching and chart rendering. 
         - Purpose: To make the long text roadmap interactive and less overwhelming. -->
    <!-- Visualization: Chart.js used for "Time Distribution" donut chart (Canvas). NO SVG/Mermaid. -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Poppins', sans-serif; background-color: #f3f4f6; }
        
        /* Chart Container Constraints */
        .chart-wrapper {
            position: relative;
            width: 100%;
            max-width: 350px; /* Constraint width */
            height: 300px;    /* Constraint height */
            margin: 0 auto;
        }

        .nav-item {
            transition: all 0.2s ease-in-out;
        }
        .nav-item:hover {
            background-color: #e0f2fe;
            color: #0284c7;
        }
        .nav-item.active {
            background-color: #0284c7;
            color: white;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        
        /* Custom Scrollbar for tables */
        .custom-scroll::-webkit-scrollbar {
            height: 8px;
        }
        .custom-scroll::-webkit-scrollbar-track {
            background: #f1f1f1; 
        }
        .custom-scroll::-webkit-scrollbar-thumb {
            background: #cbd5e1; 
            border-radius: 4px;
        }
        .custom-scroll::-webkit-scrollbar-thumb:hover {
            background: #94a3b8; 
        }
    </style>
</head>
<body class="text-gray-800 h-screen flex flex-col md:flex-row overflow-hidden">

    <!-- Sidebar Navigation -->
    <aside class="bg-white w-full md:w-64 flex-shrink-0 border-r border-gray-200 flex flex-col z-10 md:h-full">
        <div class="p-6 border-b border-gray-100 flex items-center justify-between md:block">
            <div>
                <h1 class="text-xl font-bold text-blue-900">Bank Exam '25</h1>
                <p class="text-xs text-gray-500">Master Roadmap</p>
            </div>
            <!-- Mobile Menu Toggle (Simple visibility logic handled in CSS/Structure for simplicity) -->
        </div>
        
        <nav class="flex-1 overflow-y-auto p-4 space-y-2 flex md:block overflow-x-auto md:overflow-visible whitespace-nowrap md:whitespace-normal">
            <button onclick="switchTab('dashboard')" id="btn-dashboard" class="nav-item active w-full text-left px-4 py-3 rounded-lg font-medium flex items-center gap-3">
                <span>📊</span> Dashboard
            </button>
            <button onclick="switchTab('habits')" id="btn-habits" class="nav-item w-full text-left px-4 py-3 rounded-lg font-medium flex items-center gap-3">
                <span>⚡</span> Daily Habits
            </button>
            <div class="pt-4 pb-2 px-4 text-xs font-bold text-gray-400 uppercase tracking-wider hidden md:block">Study Phases</div>
            <button onclick="switchTab('phase1')" id="btn-phase1" class="nav-item w-full text-left px-4 py-3 rounded-lg font-medium flex items-center gap-3">
                <span>1️⃣</span> Phase 1 (Basics)
            </button>
            <button onclick="switchTab('phase2')" id="btn-phase2" class="nav-item w-full text-left px-4 py-3 rounded-lg font-medium flex items-center gap-3">
                <span>2️⃣</span> Phase 2 (Speed)
            </button>
            <button onclick="switchTab('phase3')" id="btn-phase3" class="nav-item w-full text-left px-4 py-3 rounded-lg font-medium flex items-center gap-3">
                <span>3️⃣</span> Phase 3 (Mains)
            </button>
            <div class="pt-4 pb-2 px-4 text-xs font-bold text-gray-400 uppercase tracking-wider hidden md:block">Strategy</div>
            <button onclick="switchTab('mock')" id="btn-mock" class="nav-item w-full text-left px-4 py-3 rounded-lg font-medium flex items-center gap-3">
                <span>📝</span> Mock Protocol
            </button>
        </nav>
    </aside>

    <!-- Main Content Area -->
    <main class="flex-1 overflow-y-auto bg-gray-50 p-4 md:p-8 relative" id="main-container">
        
        <!-- DASHBOARD VIEW -->
        <div id="dashboard" class="view-section animate-fade-in space-y-6">
            <header class="mb-6">
                <h2 class="text-3xl font-bold text-gray-900">Your 6-Month Strategy</h2>
                <p class="text-gray-600">August – December 2025 • PO & Clerk</p>
            </header>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Chart Card -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 lg:col-span-1">
                    <h3 class="text-lg font-bold text-gray-800 mb-4">Daily Time Commitment</h3>
                    <div class="chart-wrapper">
                        <canvas id="hoursChart"></canvas>
                    </div>
                    <div class="mt-4 text-center">
                        <p class="text-sm text-gray-500">Target: <span class="font-bold text-blue-600">4.5 Hours/Day</span></p>
                        <p class="text-xs text-gray-400">Minimum required for success</p>
                    </div>
                </div>

                <!-- Quick Stats -->
                <div class="lg:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex flex-col justify-between h-full">
                        <div>
                            <span class="bg-blue-100 text-blue-700 px-3 py-1 rounded-full text-xs font-bold">Phase 1</span>
                            <h3 class="text-xl font-bold mt-2">Foundation</h3>
                            <p class="text-gray-500 text-sm mt-1">56 Days • No Mocks</p>
                        </div>
                        <p class="text-gray-700 text-sm mt-4">Focus on accuracy and concept clarity. Build the base.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex flex-col justify-between h-full">
                        <div>
                            <span class="bg-orange-100 text-orange-700 px-3 py-1 rounded-full text-xs font-bold">Phase 2</span>
                            <h3 class="text-xl font-bold mt-2">Speed Building</h3>
                            <p class="text-gray-500 text-sm mt-1">28 Days • 1 Mock/Week</p>
                        </div>
                        <p class="text-gray-700 text-sm mt-4">Intermediate topics + Sectional timing strategies.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex flex-col justify-between h-full md:col-span-2">
                        <div>
                            <span class="bg-purple-100 text-purple-700 px-3 py-1 rounded-full text-xs font-bold">Phase 3</span>
                            <h3 class="text-xl font-bold mt-2">Exam Mode</h3>
                            <p class="text-gray-500 text-sm mt-1">56 Days • 2-3 Mocks/Week</p>
                        </div>
                        <p class="text-gray-700 text-sm mt-4">Advanced Mains topics, Critical Reasoning, and heavy Mock Analysis.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- HABITS VIEW -->
        <div id="habits" class="view-section hidden space-y-6">
            <header>
                <h2 class="text-2xl font-bold text-gray-900">⚡ Daily Non-Negotiables</h2>
                <p class="text-gray-600">Do these 3 things every single day. No excuses.</p>
            </header>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Card 1 -->
                <div class="bg-white p-6 rounded-xl shadow-sm border-l-4 border-yellow-400">
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="text-lg font-bold">Quick Maths</h3>
                        <span class="text-sm font-mono bg-gray-100 px-2 py-1 rounded">15 mins</span>
                    </div>
                    <ul class="text-sm text-gray-700 space-y-2">
                        <li>• Tables (1-30)</li>
                        <li>• Squares (1-50)</li>
                        <li>• Cubes (1-30)</li>
                        <li>• Fraction % Conversions</li>
                    </ul>
                </div>

                <!-- Card 2 -->
                <div class="bg-white p-6 rounded-xl shadow-sm border-l-4 border-blue-400">
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="text-lg font-bold">English Read</h3>
                        <span class="text-sm font-mono bg-gray-100 px-2 py-1 rounded">30 mins</span>
                    </div>
                    <ul class="text-sm text-gray-700 space-y-2">
                        <li>• 1 Editorial / Article</li>
                        <li>• Note 5-10 New Words</li>
                        <li>• Understand Context</li>
                        <li>• No Dictionary initially</li>
                    </ul>
                </div>

                <!-- Card 3 -->
                <div class="bg-white p-6 rounded-xl shadow-sm border-l-4 border-green-400">
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="text-lg font-bold">Gen. Awareness</h3>
                        <span class="text-sm font-mono bg-gray-100 px-2 py-1 rounded">45 mins</span>
                    </div>
                    <ul class="text-sm text-gray-700 space-y-2">
                        <li>• Daily CA Video/PDF</li>
                        <li>• Banking Terms Revision</li>
                        <li>• Static GK (Parks/Caps)</li>
                        <li>• <span class="font-bold text-red-500">Do not skip!</span></li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- PHASE 1 VIEW -->
        <div id="phase1" class="view-section hidden space-y-6">
            <header class="flex items-center justify-between">
                <div>
                    <h2 class="text-2xl font-bold text-blue-900">Phase 1: Foundation</h2>
                    <p class="text-gray-600">Aug – Sept (2 Months) • Focus: Concepts</p>
                </div>
                <div class="bg-blue-100 text-blue-800 text-xs font-bold px-3 py-1 rounded uppercase">Repeat 28-Day Cycle x2</div>
            </header>

            <div class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
                <div class="overflow-x-auto custom-scroll">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-gray-50">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Day</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Reasoning</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Quant</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">English</th>
                            </tr>
                        </thead>
                        <tbody class="bg-white divide-y divide-gray-200 text-sm">
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 1</td>
                                <td class="px-6 py-4">Blood Relations (Basic)</td>
                                <td class="px-6 py-4">Percentages (Basics)</td>
                                <td class="px-6 py-4">Error Spotting</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 2</td>
                                <td class="px-6 py-4">Direction Sense</td>
                                <td class="px-6 py-4">Simplification (BODMAS)</td>
                                <td class="px-6 py-4">Cloze Test</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 3</td>
                                <td class="px-6 py-4">Syllogism (2-Stmt)</td>
                                <td class="px-6 py-4">Profit & Loss</td>
                                <td class="px-6 py-4">Fill in Blanks</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 4</td>
                                <td class="px-6 py-4">Inequality</td>
                                <td class="px-6 py-4">SI / CI (Basic)</td>
                                <td class="px-6 py-4">Grammar (Tenses)</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 5</td>
                                <td class="px-6 py-4">Small Puzzle (Linear)</td>
                                <td class="px-6 py-4">Averages</td>
                                <td class="px-6 py-4">Synonyms/Antonyms</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 6</td>
                                <td class="px-6 py-4">Alphanumeric Series</td>
                                <td class="px-6 py-4">Quadratic Eqns</td>
                                <td class="px-6 py-4">Short RC</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-bold text-indigo-600">Day 7</td>
                                <td class="px-6 py-4 font-bold text-indigo-600" colspan="3">Revision + GA Weekly Capsule (No Mock)</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- PHASE 2 VIEW -->
        <div id="phase2" class="view-section hidden space-y-6">
            <header class="flex items-center justify-between">
                <div>
                    <h2 class="text-2xl font-bold text-orange-700">Phase 2: Speed</h2>
                    <p class="text-gray-600">October (1 Month) • Focus: Speed & Intermediate</p>
                </div>
                <div class="bg-orange-100 text-orange-800 text-xs font-bold px-3 py-1 rounded uppercase">Repeat 28-Day Cycle x1</div>
            </header>

            <div class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
                <div class="overflow-x-auto custom-scroll">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-orange-50">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-orange-800 uppercase tracking-wider">Day</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-orange-800 uppercase tracking-wider">Reasoning</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-orange-800 uppercase tracking-wider">Quant</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-orange-800 uppercase tracking-wider">English</th>
                            </tr>
                        </thead>
                        <tbody class="bg-white divide-y divide-gray-200 text-sm">
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 8</td>
                                <td class="px-6 py-4">Floor Puzzle</td>
                                <td class="px-6 py-4">Time Speed Dist</td>
                                <td class="px-6 py-4">Para Jumbles</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 9</td>
                                <td class="px-6 py-4">Box Puzzle</td>
                                <td class="px-6 py-4">Mixtures</td>
                                <td class="px-6 py-4">Long RC</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 10</td>
                                <td class="px-6 py-4">Month Puzzle</td>
                                <td class="px-6 py-4">Partnership</td>
                                <td class="px-6 py-4">Sentence Rearrange</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 11</td>
                                <td class="px-6 py-4">Order Ranking</td>
                                <td class="px-6 py-4">Caselet DI</td>
                                <td class="px-6 py-4">Phrase Replace</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 12</td>
                                <td class="px-6 py-4">Data Sufficiency</td>
                                <td class="px-6 py-4">Data Sufficiency</td>
                                <td class="px-6 py-4">Cloze Test (Hard)</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 13</td>
                                <td class="px-6 py-4">Mixed Puzzle</td>
                                <td class="px-6 py-4">Caselet DI II</td>
                                <td class="px-6 py-4">Grammar Recap</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-bold text-orange-600">Day 14</td>
                                <td class="px-6 py-4 font-bold text-orange-600" colspan="3">Prelims Mock + Analysis + Essay Practice</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- PHASE 3 VIEW -->
        <div id="phase3" class="view-section hidden space-y-6">
            <header class="flex items-center justify-between">
                <div>
                    <h2 class="text-2xl font-bold text-purple-800">Phase 3: Mains</h2>
                    <p class="text-gray-600">Nov – Dec (2 Months) • Focus: Mains & Mocks</p>
                </div>
                <div class="bg-purple-100 text-purple-800 text-xs font-bold px-3 py-1 rounded uppercase">Repeat 28-Day Cycle x2</div>
            </header>

            <div class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
                <div class="overflow-x-auto custom-scroll">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-purple-50">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-purple-800 uppercase tracking-wider">Day</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-purple-800 uppercase tracking-wider">Reasoning (Adv)</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-purple-800 uppercase tracking-wider">Quant (Adv)</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-purple-800 uppercase tracking-wider">Eng / Comp</th>
                            </tr>
                        </thead>
                        <tbody class="bg-white divide-y divide-gray-200 text-sm">
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 15</td>
                                <td class="px-6 py-4">Input-Output</td>
                                <td class="px-6 py-4">Mensuration</td>
                                <td class="px-6 py-4">Inference RC</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 16</td>
                                <td class="px-6 py-4">Machine Puzzle</td>
                                <td class="px-6 py-4">Probability</td>
                                <td class="px-6 py-4">Match Column</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 17</td>
                                <td class="px-6 py-4">Critical Reas.</td>
                                <td class="px-6 py-4">Permutation/Comb</td>
                                <td class="px-6 py-4">Connectors</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 18</td>
                                <td class="px-6 py-4">Mains Puzzle</td>
                                <td class="px-6 py-4">Radar/Missing DI</td>
                                <td class="px-6 py-4">Adv. Cloze</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-medium text-gray-900">Day 19</td>
                                <td class="px-6 py-4">Data Sufficiency</td>
                                <td class="px-6 py-4">Adv. Arithmetic</td>
                                <td class="px-6 py-4">Cyber Security</td>
                            </tr>
                            <tr class="bg-gray-50">
                                <td class="px-6 py-4 font-medium text-gray-900">Day 20</td>
                                <td class="px-6 py-4">Full Sectional</td>
                                <td class="px-6 py-4">Full Sectional</td>
                                <td class="px-6 py-4">Full Sectional</td>
                            </tr>
                            <tr>
                                <td class="px-6 py-4 font-bold text-purple-600">Day 21</td>
                                <td class="px-6 py-4 font-bold text-purple-600" colspan="3">MAINS MOCK + Analysis + Full GA Rev</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- MOCK PROTOCOL VIEW -->
        <div id="mock" class="view-section hidden space-y-6">
            <header>
                <h2 class="text-2xl font-bold text-red-800">Mock Analysis Protocol</h2>
                <p class="text-gray-600">Without this, taking tests is a waste of time.</p>
            </header>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-white p-6 rounded-xl border-t-4 border-red-500 shadow-sm">
                    <h3 class="text-lg font-bold mb-2 text-red-900">1. The Environment</h3>
                    <p class="text-gray-600 text-sm">Do not pause. Do not use a phone. Sit at a table. Simulate the exam noise if possible.</p>
                </div>
                <div class="bg-white p-6 rounded-xl border-t-4 border-red-500 shadow-sm">
                    <h3 class="text-lg font-bold mb-2 text-red-900">2. The Analysis</h3>
                    <p class="text-gray-600 text-sm">Spend <b>more time analyzing</b> than taking the test. Check every wrong answer. Was it conceptual? Silly mistake? Or timing?</p>
                </div>
                <div class="bg-white p-6 rounded-xl border-t-4 border-red-500 shadow-sm">
                    <h3 class="text-lg font-bold mb-2 text-red-900">3. The Error Log</h3>
                    <p class="text-gray-600 text-sm">Write down the mistake in a dedicated notebook. Revise this notebook every Sunday. Never repeat the same mistake twice.</p>
                </div>
            </div>
        </div>

    </main>

    <script>
        // Tab Switching Logic
        function switchTab(tabId) {
            // Hide all sections
            document.querySelectorAll('.view-section').forEach(el => el.classList.add('hidden'));
            // Show target section
            document.getElementById(tabId).classList.remove('hidden');
            
            // Update nav buttons
            document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
            document.getElementById('btn-' + tabId).classList.add('active');

            // Refresh Chart if Dashboard is selected
            if(tabId === 'dashboard' && window.myChart) {
                window.myChart.resize();
            }
        }

        // Chart.js Initialization
        document.addEventListener('DOMContentLoaded', function() {
            const ctx = document.getElementById('hoursChart');
            if (ctx) {
                window.myChart = new Chart(ctx, {
                    type: 'doughnut',
                    data: {
                        labels: ['Core Topics (3h)', 'Habits/GA/Maths (1.5h)'],
                        datasets: [{
                            data: [3, 1.5],
                            backgroundColor: ['#3b82f6', '#f59e0b'],
                            borderWidth: 0,
                            hoverOffset: 4
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: {
                                position: 'bottom',
                                labels: { font: { family: 'Poppins' } }
                            }
                        }
                    }
                });
            }
        });
    </script>
</body>
</html>

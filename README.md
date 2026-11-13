<!DOCTYPE html>
<html lang="ckb" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سیستەمی دابەشکردنی خۆراک - بەڕێوەبردن و کۆگا (فراوان / Full Screen Desktop)</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Vazirmatn & Noto Sans Arabic -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Arabic:wght@300;400;500;600;700;800&family=Vazirmatn:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Vazirmatn', 'Noto Sans Arabic', 'sans-serif'],
                    },
                    colors: {
                        wheat: {
                            50: '#fdfaf3',
                            100: '#faf2de',
                            200: '#f4e1b8',
                            300: '#ecc987',
                            400: '#e2ab52',
                            500: '#d9912b',
                            600: '#c27520',
                            700: '#a1591c',
                            800: '#83471d',
                            900: '#6b3b1b',
                        },
                        emeraldDark: '#064e3b',
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Vazirmatn', 'Noto Sans Arabic', sans-serif;
            background-color: #f8fafc;
            font-size: 14px;
        }
        ::-webkit-scrollbar { width: 8px; height: 8px; }
        ::-webkit-scrollbar-track { background: #f1f5f9; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 9999px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
        @media print {
            .no-print { display: none !important; }
            body { background-color: white !important; }
        }
        .wheat-glow { filter: drop-shadow(0 4px 10px rgba(217, 145, 43, 0.25)); }
    </style>
</head>
<body class="text-slate-800 antialiased selection:bg-wheat-200 selection:text-wheat-900">

    <!-- Toast Notification Container -->
    <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 max-w-sm w-full pointer-events-none"></div>

    <!-- ===================================================================== -->
    <!-- 1. LOGIN SCREEN -->
    <!-- ===================================================================== -->
    <div id="login-screen" class="min-h-screen flex items-center justify-center bg-gradient-to-br from-slate-900 via-emerald-950 to-slate-900 p-4 relative">
        <div class="max-w-md w-full bg-white/95 backdrop-blur-md rounded-2xl shadow-2xl overflow-hidden border border-wheat-200/50">
            <div class="bg-gradient-to-l from-wheat-600 via-wheat-500 to-amber-500 p-6 text-center text-white relative overflow-hidden">
                <div class="w-16 h-16 mx-auto bg-white rounded-xl shadow-lg flex items-center justify-center mb-3 wheat-glow">
                    <svg class="w-10 h-10 text-wheat-600" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M32 58V14" stroke="currentColor" stroke-width="3" stroke-linecap="round"/>
                        <path d="M32 46C24 46 19 41 19 34C26 34 32 39 32 46Z" fill="#d9912b"/>
                        <path d="M32 36C24 36 19 31 19 24C26 24 32 29 32 36Z" fill="#e2ab52"/>
                        <path d="M32 26C24 26 19 21 19 14C26 14 32 19 32 26Z" fill="#d9912b"/>
                        <path d="M32 46C40 46 45 41 45 34C38 34 32 39 32 46Z" fill="#e2ab52"/>
                        <path d="M32 36C40 36 45 31 45 24C38 24 32 29 32 36Z" fill="#d9912b"/>
                        <path d="M32 26C40 26 45 21 45 14C38 14 32 19 32 26Z" fill="#e2ab52"/>
                        <path d="M32 16C28 11 28 6 32 3C36 6 36 11 32 16Z" fill="#c27520"/>
                        <path d="M19 34L14 28M19 24L14 18M19 14L14 8M45 34L50 28M45 24L50 18M45 14L50 8" stroke="#a1591c" stroke-width="1.5" stroke-linecap="round"/>
                    </svg>
                </div>
                <h1 class="text-lg font-extrabold tracking-tight">سیستەمی دابەشکردنی خۆراك و بەرێوەبردن</h1>
            </div>

            <div class="p-6">
                <form id="login-form" class="space-y-4">
                    <div>
                        <label for="login-password" class="block text-sm font-bold text-slate-700 mb-1.5">پاسۆردی چوونەژوورەوە بنووسە:</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 right-0 flex items-center pr-3.5 text-slate-400 text-sm">
                                <i class="fa-solid fa-lock"></i>
                            </span>
                            <input type="password" id="login-password" placeholder="پاسۆرد (بنەڕەتی: 009988)" required
                                class="w-full pr-10 pl-10 py-3 rounded-xl border border-slate-300 focus:border-wheat-500 focus:ring-2 focus:ring-wheat-200 outline-none text-left font-mono text-base tracking-widest transition">
                            <button type="button" onclick="togglePasswordVisibility('login-password', this)" class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400 hover:text-slate-600 text-sm">
                                <i class="fa-solid fa-eye"></i>
                            </button>
                        </div>
                    </div>

                    <button type="submit" class="w-full py-3 px-4 bg-gradient-to-l from-emerald-700 to-emerald-600 hover:from-emerald-800 hover:to-emerald-700 text-white font-bold rounded-xl shadow-lg shadow-emerald-600/20 transition flex items-center justify-center gap-2 text-sm">
                        <i class="fa-solid fa-right-to-bracket"></i>
                        <span>چوونەژوورەوە بۆ سیستەم</span>
                    </button>
                </form>
            </div>
        </div>
    </div>

    <!-- ===================================================================== -->
    <!-- 2. MAIN APPLICATION DASHBOARD (DESKTOP FULL SCREEN) -->
    <!-- ===================================================================== -->
    <div id="main-app" class="hidden min-h-screen flex flex-col w-full">
        <header class="bg-white border-b border-slate-200 sticky top-0 z-30 shadow-sm no-print w-full">
            <div class="w-full px-6 py-3">
                <div class="flex items-center justify-between">
                    <div class="flex items-center gap-3">
                        <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-wheat-100 to-amber-50 border border-wheat-300 flex items-center justify-center shadow-sm shrink-0">
                            <svg class="w-8 h-8 text-wheat-600" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M32 58V14" stroke="currentColor" stroke-width="3.5" stroke-linecap="round"/>
                                <path d="M32 46C24 46 19 41 19 34C26 34 32 39 32 46Z" fill="#d9912b"/>
                                <path d="M32 36C24 36 19 31 19 24C26 24 32 29 32 36Z" fill="#e2ab52"/>
                                <path d="M32 26C24 26 19 21 19 14C26 14 32 19 32 26Z" fill="#d9912b"/>
                                <path d="M32 46C40 46 45 41 45 34C38 34 32 39 32 46Z" fill="#e2ab52"/>
                                <path d="M32 36C40 36 45 31 45 24C38 24 32 29 32 36Z" fill="#d9912b"/>
                                <path d="M32 26C40 26 45 21 45 14C38 14 32 19 32 26Z" fill="#e2ab52"/>
                                <path d="M32 16C28 11 28 6 32 3C36 6 36 11 32 16Z" fill="#c27520"/>
                                <path d="M19 34L14 28M19 24L14 18M19 14L14 8M45 34L50 28M45 24L50 18M45 14L50 8" stroke="#a1591c" stroke-width="1.5" stroke-linecap="round"/>
                            </svg>
                        </div>
                        <div>
                            <h1 class="text-base font-extrabold text-slate-800 leading-tight">سیستەمی دابەشکردنی خۆراك و بەرێوەبردن</h1>
                            <div class="flex items-center gap-2 text-xs text-slate-500 mt-0.5">
                                <span class="inline-flex items-center gap-1.5 text-wheat-800 font-bold bg-wheat-100 px-2.5 py-1 rounded-md">
                                    <i class="fa-solid fa-calendar-days text-wheat-600"></i>
                                    <span id="header-current-day">شەممە</span>
                                </span>
                            </div>
                        </div>
                    </div>
                </div>

                <nav class="flex items-center gap-2 mt-3 pt-3 border-t border-slate-100 overflow-x-auto pb-1">
                    <button onclick="switchTab('distribution')" id="tab-btn-distribution" class="tab-btn active flex items-center gap-2 px-4 py-2.5 rounded-xl font-bold text-sm transition whitespace-nowrap bg-emerald-700 text-white shadow-sm">
                        <i class="fa-solid fa-hand-holding-heart"></i>
                        <span>دابەشکردنی خۆراک</span>
                    </button>
                    <button onclick="switchTab('beneficiaries')" id="tab-btn-beneficiaries" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-xl font-bold text-sm transition whitespace-nowrap bg-slate-100 text-slate-600 hover:bg-slate-200">
                        <i class="fa-solid fa-user-plus"></i>
                        <span>زیادکردنی کەسەکان</span>
                    </button>
                    <button onclick="switchTab('monitoring')" id="tab-btn-monitoring" class="tab-btn flex items-center gap-2 px-4 py-2.5 rounded-xl font-bold text-sm transition whitespace-nowrap bg-slate-100 text-slate-600 hover:bg-slate-200">
                        <i class="fa-solid fa-clipboard-list"></i>
                        <span>لیستی تۆمار (تۆمارەکان)</span>
                    </button>
                </nav>
            </div>
        </header>

        <main class="flex-1 w-full p-6">
            <!-- TAB 3: MONITORING / لیستی تۆمار (بۆ جێگابوونەوەی فراوان و پڕ لە تەنیشت یەک) -->
            <section id="tab-monitoring" class="tab-content hidden space-y-6">
                <div class="bg-white rounded-2xl border border-slate-200 shadow-sm p-6 w-full">
                    <div class="flex flex-col sm:flex-row items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-base font-extrabold text-slate-800 flex items-center gap-2">
                                <i class="fa-solid fa-clipboard-list text-emerald-600 text-lg"></i>
                                <span>تۆماری گشتی دابەشکردن و چالاکییەکان</span>
                            </h2>
                            <p class="text-xs text-slate-500 mt-

# Parental-Control
DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAFEHAVEN - Interactive Prototype</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Configure Tailwind for Inter font -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f9fc;
            /* Use flexbox to center the phone frame vertically and horizontally */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        /* --- Custom CSS for the Mobile Phone Frame --- */
        #phoneFrame {
            width: 375px; /* Standard mobile width */
            height: 812px; /* Standard mobile height */
            background: #1f2937; /* Dark bezel */
            border-radius: 40px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3), 0 0 0 10px rgba(0, 0, 0, 0.1) inset;
            position: relative;
            overflow: hidden; /* Contains the screen content */
        }
        
        #screen {
            background-color: #ffffff; /* Inner screen color */
            width: 100%;
            height: 100%;
            border-radius: 36px;
            overflow-y: scroll; /* Allows the content to scroll within the phone frame */
            -webkit-overflow-scrolling: touch;
        }

        /* Mock speaker notch */
        #notch {
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            height: 25px;
            background: #1f2937;
            border-radius: 0 0 15px 15px;
            z-index: 20;
        }
        
        /* Ensure app content fills the screen area */
        #app {
            max-width: none;
            padding: 0;
            min-height: 100%;
        }

        /* Adjust footer positioning to be relative to the frame */
        #appFooter {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            width: 100%;
            box-shadow: 0 -5px 20px rgba(0, 0, 0, 0.05);
            z-index: 10;
        }

        /* Standard interactive styles */
        .nav-item {
            transition: color 0.2s;
        }
        .card-focus {
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
        }
        .card-focus:hover {
            transform: translateY(-4px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
         .toggle-switch-input:checked + .toggle-switch-label {
            background-color: #10b981; /* safe color */
        }
        .toggle-switch-input:checked + .toggle-switch-label:after {
            transform: translateX(20px);
        }
        .toggle-switch-label:after {
            content: '';
            position: absolute;
            top: 2px;
            left: 2px;
            width: 16px;
            height: 16px;
            background-color: white;
            border-radius: 9999px;
            transition: transform 0.3s ease-in-out;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
        }
        .toggle-switch-label {
             width: 40px;
             height: 20px;
             border-radius: 9999px;
             background-color: #ccc;
             position: relative;
             cursor: pointer;
             display: inline-block;
             transition: background-color 0.3s;
        }
    </style>
    <script>
        // Updated Color Palette for SAFEHAVEN (Added 'alert' red and brighter 'info' yellow)
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'primary': '#5DADEC', // Sky Blue (Trust)
                        'secondary': '#FF8A65', // Warm Coral (General Accent)
                        'alert': '#EF4444',    // Bright Red (Alerts/Blocks)
                        'info': '#FDE047',     // Brighter Yellow (Awareness/Suggestions)
                        'safe': '#10b981',     // Green for 'safe' status
                        'text-dark': '#1f2937', // Dark gray for text
                        'text-light': '#4b5563', // Medium gray for text
                    },
                }
            }
        }
    </script>
</head>
<body class="min-h-screen">
    
    <!-- Outer Phone Frame -->
    <div id="phoneFrame">
        <!-- Mock Notch -->
        <div id="notch"></div>
        
        <!-- Inner Screen Area -->
        <div id="screen">
            <div id="app">
                <!-- Header & Child Status (Top Bar) -->
                <header id="appHeader" class="fixed top-0 left-0 right-0 w-full p-4 bg-white shadow-lg flex items-center justify-between border-b-4 border-primary z-10 hidden" style="width: 375px;">
                    <!-- Child Avatar and Name (More colorful/branded look) -->
                    <div class="flex items-center space-x-4">
                        <!-- Branded Logo/Avatar: Brighter green ring and shadow -->
                        <div class="w-10 h-10 bg-safe rounded-full flex items-center justify-center text-white font-extrabold text-lg ring-4 ring-safe/50 shadow-lg">
                            L
                        </div>
                        <div>
                            <p class="text-lg font-bold text-text-dark">Leo's Dashboard</p>
                            <div class="flex items-center space-x-1 mt-1">
                                <span class="w-2 h-2 rounded-full bg-safe animate-pulse"></span>
                                <span class="font-medium text-safe text-xs">Connected</span>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Quick Info -->
                    <div class="text-right">
                        <p class="text-xs text-text-light">Last Sync: <span class="font-semibold">Now</span></p>
                        <!-- Highlight battery in safe green -->
                        <p class="text-xs text-text-light">Battery: <span class="font-semibold text-safe">78%</span></p>
                    </div>
                </header>

                <!-- Dynamic Content Area -->
                <div id="mainContent" class="space-y-6">
                    <!-- Content will be rendered here by JavaScript -->
                </div>
            </div>

            <!-- Bottom Navigation Bar (Fixed for mobile feel, class changed to fit frame) -->
            <footer id="appFooter" class="bg-white border-t border-gray-200 shadow-2xl p-3 z-10 hidden">
                <nav id="bottomNav" class="flex justify-around max-w-xl mx-auto text-gray-500">
                    <!-- Navigation items will be managed by JS -->
                </nav>
            </footer>
        </div>
    </div>

    <!-- Notification Container -->
    <div id="notification-container"></div>

    <script>
        let currentScreen = 'onboarding'; // Start on the onboarding flow
        let onboardingStep = 1; // Tracks the current step during onboarding
        const mainContent = document.getElementById('mainContent');
        const bottomNav = document.getElementById('bottomNav');
        const headerElement = document.getElementById('appHeader');
        const footerElement = document.getElementById('appFooter');
        
        /**
         * Function to display a temporary notification instead of an alert().
         */
        function showNotification(message) {
            const container = document.getElementById('notification-container');
            const msg = document.createElement('div');
            // Position relative to the center of the phone frame
            const phoneFrame = document.getElementById('phoneFrame');
            const phoneRect = phoneFrame.getBoundingClientRect();

            msg.className = "absolute bg-gray-800 text-white text-center p-3 rounded-xl shadow-xl transition-all duration-500 ease-out z-50 opacity-0";
            
            // Calculate position inside the frame
            msg.style.top = `${phoneRect.top + 30}px`; 
            msg.style.left = `${phoneRect.left + (phoneRect.width / 2)}px`;
            msg.style.transform = 'translate(-50%, 0)';
            msg.textContent = message;
            container.appendChild(msg);

            // Animate in
            setTimeout(() => {
                msg.style.opacity = '1';
            }, 10);

            // Animate out
            setTimeout(() => {
                msg.style.opacity = '0';
                msg.style.transform = 'translate(-50%, -20px)';
                setTimeout(() => msg.remove(), 500);
            }, 3000);
        }

        // --- ONBOARDING FLOW FUNCTIONS ---

        function nextOnboardingStep() {
            onboardingStep++;
            if (onboardingStep > 3) {
                // Transition to the main dashboard
                currentScreen = 'dashboard';
                headerElement.classList.remove('hidden');
                footerElement.classList.remove('hidden');
                // Restore dashboard specific padding/layout
                mainContent.style.padding = '5rem 1rem 5rem 1rem'; 
                mainContent.classList.add('space-y-6');
                changeScreen('dashboard'); // Go to main app screen
            } else {
                renderOnboarding(); // Render next onboarding screen
            }
        }

        function renderOnboarding() {
            headerElement.classList.add('hidden');
            footerElement.classList.add('hidden');
            mainContent.classList.remove('space-y-6');
            // Ensure main content fills the screen area without header/footer overlap
            mainContent.style.padding = '0'; 
            mainContent.style.minHeight = '100%';

            let onboardingHTML = '';
            switch(onboardingStep) {
                case 1:
                    onboardingHTML = renderOnboardingStep1();
                    break;
                case 2:
                    onboardingHTML = renderOnboardingStep2();
                    break;
                case 3:
                    onboardingHTML = renderOnboardingStep3();
                    break;
                default:
                    // Fallback to exit flow
                    nextOnboardingStep();
                    return;
            }
            mainContent.innerHTML = onboardingHTML;
        }

        function renderOnboardingStep1() {
            return `
                <div class="h-full flex flex-col justify-between items-center text-center p-8 bg-gradient-to-br from-primary to-blue-300 min-h-[812px]">
                    <div class="pt-10">
                        <div class="p-4 rounded-full bg-white/20 inline-block">
                             <!-- Trust Icon -->
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-20 h-20 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="M9 12l2 2 4-4"/></svg>
                        </div>
                    </div>
                    
                    <div class="space-y-4">
                        <h1 class="text-4xl font-extrabold text-white leading-tight">Welcome to SAFEHAVEN</h1>
                        <p class="text-xl text-white/90 font-light">
                            Intelligent parental controls built on **trust, consent, and transparency**. We protect without invading.
                        </p>
                    </div>

                    <div class="w-full space-y-4 pb-10">
                        <div class="flex justify-center space-x-2">
                            <span class="w-3 h-3 rounded-full bg-white"></span>
                            <span class="w-3 h-3 rounded-full bg-white/50"></span>
                            <span class="w-3 h-3 rounded-full bg-white/50"></span>
                        </div>
                        <button onclick="nextOnboardingStep()" class="w-full py-4 bg-white text-primary text-lg font-bold rounded-xl shadow-lg hover:bg-gray-100 transition duration-200">
                            Get Started
                        </button>
                    </div>
                </div>
            `;
        }

        function renderOnboardingStep2() {
            return `
                 <div class="h-full flex flex-col justify-between items-center text-center p-8 bg-gradient-to-br from-safe to-green-400 min-h-[812px]">
                    <div class="pt-10">
                        <div class="p-4 rounded-full bg-white/20 inline-block">
                             <!-- Connect Icon -->
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-20 h-20 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="5" y="2" width="14" height="20" rx="2" ry="2"/><line x1="12" y1="18" x2="12" y2="18"/><path d="M18 10a4 4 0 0 0-4-4h-4a4 4 0 0 0-4 4v4a4 4 0 0 0 4 4h4a4 4 0 0 0 4-4v-4z"/></svg>
                        </div>
                    </div>
                    
                    <div class="space-y-4">
                        <h1 class="text-4xl font-extrabold text-white leading-tight">Connect with Consent</h1>
                        <p class="text-xl text-white/90 font-light">
                            We require the child's explicit, on-device consent. This ensures an open conversation about boundaries, not surveillance.
                        </p>
                        <div class="bg-white/30 text-white p-4 rounded-xl text-left text-sm font-medium">
                            Status: **Awaiting Confirmation** on Leo's device.
                        </div>
                    </div>

                    <div class="w-full space-y-4 pb-10">
                        <div class="flex justify-center space-x-2">
                            <span class="w-3 h-3 rounded-full bg-white/50"></span>
                            <span class="w-3 h-3 rounded-full bg-white"></span>
                            <span class="w-3 h-3 rounded-full bg-white/50"></span>
                        </div>
                        <button onclick="nextOnboardingStep()" class="w-full py-4 bg-white text-safe text-lg font-bold rounded-xl shadow-lg hover:bg-gray-100 transition duration-200">
                            Simulate Connection Success
                        </button>
                    </div>
                </div>
            `;
        }

        function renderOnboardingStep3() {
            return `
                 <div class="h-full flex flex-col justify-between items-center text-center p-8 bg-gradient-to-br from-secondary to-orange-300 min-h-[812px]">
                    <div class="pt-10">
                        <div class="p-4 rounded-full bg-white/20 inline-block">
                             <!-- Rules Icon -->
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-20 h-20 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M19 19c0 .5-.5 1-1 1H6c-.5 0-1-.5-1-1V5c0-.5.5-1 1-1h12c.5 0 1 .5 1 1v14z"/><path d="M17 10h-2M17 14h-6"/><path d="M8 7h8"/></svg>
                        </div>
                    </div>
                    
                    <div class="space-y-4">
                        <h1 class="text-4xl font-extrabold text-white leading-tight">Safety Ready!</h1>
                        <p class="text-xl text-white/90 font-light">
                            You can now set your first **Smart Rules** and view real-time **AI Risk Scores** on your dashboard.
                        </p>
                        <div class="bg-white/30 text-white p-4 rounded-xl text-left text-sm font-medium">
                            Next Steps: Define bedtime limits and block social apps during school hours.
                        </div>
                    </div>

                    <div class="w-full space-y-4 pb-10">
                        <div class="flex justify-center space-x-2">
                            <span class="w-3 h-3 rounded-full bg-white/50"></span>
                            <span class="w-3 h-3 rounded-full bg-white/50"></span>
                            <span class="w-3 h-3 rounded-full bg-white"></span>
                        </div>
                        <button onclick="nextOnboardingStep()" class="w-full py-4 bg-white text-secondary text-lg font-bold rounded-xl shadow-lg hover:bg-gray-100 transition duration-200">
                            Go to Dashboard
                        </button>
                    </div>
                </div>
            `;
        }


        // --- SCREEN RENDERING FUNCTIONS (Dashboard, LiveInsight, Rules) ---

        function renderDashboard() {
            return `
                <!-- 1. AI Risk Score Card (Main Focus Card - Enhanced with Gradient/Shadow) -->
                <div id="aiRiskCard" class="bg-gradient-to-r from-green-50 to-white p-6 shadow-2xl rounded-xl border-t-8 border-safe card-focus cursor-pointer" onclick="showNotification('AI Risk Score details would expand here.')">
                    <div class="flex items-center justify-between">
                        <h2 class="text-2xl font-semibold text-text-dark flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7 mr-3 text-safe" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/><line x1="12" y1="9" x2="12" y2="13"/><line x1="12" y1="17" x2="12" y2="17"/></svg>
                            AI Risk Score
                        </h2>
                        <div class="text-4xl font-extrabold text-safe bg-safe/10 px-4 py-1 rounded-full border border-safe">
                            85%
                        </div>
                    </div>
                    <p class="text-lg mt-3 text-text-light">Your child is **85% safe today**. Tap for breakdown.</p>
                    <div class="w-full h-2 bg-gray-200 rounded-full mt-4">
                        <div class="h-full bg-safe rounded-full" style="width: 85%;"></div>
                    </div>
                    <p class="text-xs text-text-light mt-2">Status: Safe, minor gaming detected.</p>
                </div>

                <!-- Metric Cards Grid (2x2 Layout for quick stats) -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">

                    <!-- 2. Blocked Alerts Card (Using new 'alert' color) -->
                    <div class="bg-white p-6 shadow-md rounded-xl border-l-4 border-alert card-focus cursor-pointer" onclick="showNotification('Opening Incident Report Page...')">
                        <div class="flex items-center justify-between">
                            <h3 class="text-lg font-semibold text-text-dark">🚫 Blocked Alerts</h3>
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-alert" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="15" y1="9" x2="9" y2="15"/><line x1="9" y1="9" x2="15" y2="15"/></svg>
                        </div>
                        <p class="text-4xl font-bold mt-2 text-alert">2</p>
                        <p class="text-sm text-text-light mt-1">risky websites blocked.</p>
                        <button class="text-xs text-alert font-semibold mt-3 hover:underline">View Report</button>
                    </div>

                    <!-- 3. Social Chat Watch Card (Using new brighter 'info' color) -->
                    <div class="bg-white p-6 shadow-md rounded-xl border-l-4 border-info card-focus cursor-pointer" onclick="showNotification('Opening Flagged Conversation Log...')">
                        <div class="flex items-center justify-between">
                            <h3 class="text-lg font-semibold text-text-dark">💬 Social Chat Watch</h3>
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-info" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
                        </div>
                        <p class="text-4xl font-bold mt-2 text-info">1</p>
                        <p class="text-sm text-text-light mt-1">flagged conversation.</p>
                        <button class="text-xs text-info font-semibold mt-3 hover:underline">Review Chat</button>
                    </div>

                    <!-- 4. Screen Time Used Card -->
                    <div class="bg-white p-6 shadow-md rounded-xl border-l-4 border-primary card-focus">
                        <div class="flex items-center justify-between">
                            <h3 class="text-lg font-semibold text-text-dark">📱 Screen Time Used</h3>
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-primary" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="5" y="2" width="14" height="20" rx="2" ry="2"/><line x1="12" y1="18" x2="12" y2="18"/></svg>
                        </div>
                        <p class="text-4xl font-bold mt-2 text-primary">3h 10m</p>
                        <p class="text-sm text-text-light mt-1">Remaining: 50 minutes today</p>
                        <button class="text-xs text-primary font-semibold mt-3 hover:underline" onclick="changeScreen('rules')">Adjust Limits</button>
                    </div>

                    <!-- 5. Location Status Card -->
                    <div class="bg-white p-6 shadow-md rounded-xl border-l-4 border-gray-300 card-focus cursor-pointer" onclick="showNotification('Long-press action: Create Rule Shortcut...')">
                        <div class="flex items-center justify-between">
                            <h3 class="text-lg font-semibold text-text-dark">📍 Location Status</h3>
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-gray-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
                        </div>
                        <p class="text-xl font-bold mt-2 text-gray-600">At Home</p>
                        <p class="text-sm text-text-light mt-1">Last seen 5 min ago.</p>
                        <button class="text-xs text-gray-500 font-semibold mt-3 hover:underline">Live Map</button>
                    </div>
                </div>
            `;
        }

        function renderLiveInsight() {
            return `
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                    <!-- Left Column: Activity Feed -->
                    <div class="lg:col-span-2 bg-white p-6 shadow-xl rounded-xl border-t-8 border-primary space-y-4">
                        <h2 class="text-2xl font-semibold text-text-dark flex items-center mb-4">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7 mr-3 text-primary" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>
                            Live Activity Feed
                        </h2>

                        <!-- Activity Timeline Items -->
                        <div class="space-y-4 max-h-96 overflow-y-auto pr-2">
                            <div class="flex items-start space-x-3 p-3 bg-gray-50 rounded-lg border-l-4 border-safe/50">
                                <div class="w-2 h-2 mt-2 bg-safe rounded-full"></div>
                                <p class="text-sm text-text-light">
                                    <span class="font-bold text-gray-800">9:15 PM</span> – Playing <span class="font-semibold text-primary">Roblox</span> (<span class="text-alert">Chat flagged for language</span> - Level: Medium)
                                </p>
                            </div>
                            <div class="flex items-start space-x-3 p-3 bg-gray-50 rounded-lg border-l-4 border-primary/50">
                                <div class="w-2 h-2 mt-2 bg-primary rounded-full"></div>
                                <p class="text-sm text-text-light">
                                    <span class="font-bold text-gray-800">9:05 PM</span> – Watching YouTube (<span class="font-semibold text-safe">Educational content</span> - Math help)
                                </p>
                            </div>
                            <!-- Updated border color to use 'alert' -->
                            <div class="flex items-start space-x-3 p-3 bg-gray-50 rounded-lg border-l-4 border-alert/50">
                                <div class="w-2 h-2 mt-2 bg-alert rounded-full"></div>
                                <p class="text-sm text-text-light">
                                    <span class="font-bold text-gray-800">8:50 PM</span> – Attempted to access <span class="font-semibold text-alert">blocked URL</span> (Category: Gambling)
                                </p>
                            </div>
                            <div class="flex items-start space-x-3 p-3 bg-gray-50 rounded-lg border-l-4 border-primary/50">
                                <div class="w-2 h-2 mt-2 bg-primary rounded-full"></div>
                                <p class="text-sm text-text-light">
                                    <span class="font-bold text-gray-800">8:30 PM</span> – Opened <span class="font-semibold text-primary">Instagram</span> (Duration: 5 minutes)
                                </p>
                            </div>
                        </div>

                    </div>
                    
                    <!-- Right Column: AI Summary & Screenshot -->
                    <div class="lg:col-span-1 space-y-6">
                        <!-- AI Summary Chat (Updated to use brighter 'info') -->
                        <div class="bg-white p-4 shadow-md rounded-xl border-l-4 border-info">
                            <h3 class="text-lg font-semibold text-text-dark flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 mr-2 text-info" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2a5 5 0 0 0-5 5v3H5a2 2 0 0 0-2 2v9a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-9a2 2 0 0 0-2-2h-2V7a5 5 0 0 0-5-5z"/></svg>
                                AI Summary Chat
                            </h3>
                            <div class="mt-2 p-3 bg-info/20 rounded-lg text-sm text-gray-700 border border-info">
                                <span class="font-bold">Safe, minor warning detected.</span> Leo is mostly using educational content but needs a quick check on Roblox chat behavior. No immediate action required.
                            </div>
                        </div>

                        <!-- Screenshot & Consent -->
                        <div class="bg-white p-4 shadow-md rounded-xl border-l-4 border-safe">
                            <h3 class="text-lg font-semibold text-text-dark mb-3">Monitoring Tools</h3>
                            
                            <!-- Blurred Screenshot -->
                            <button onclick="requestScreenshot(event)" class="w-full py-2 px-4 bg-primary text-white font-semibold rounded-lg shadow-md hover:bg-primary/90 transition duration-200 flex items-center justify-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M23 15h-2a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2v-5z"/><path d="M1 9h2a2 2 0 0 0 2-2V5a2 2 0 0 0-2-2H1v5z"/><path d="M21 3h-2a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2V3zM3 21h2a2 2 0 0 0 2-2v-2a2 2 0 0 0-2-2H3v5z"/></svg>
                                Request Screenshot (Blurred Preview)
                            </button>
                            <p class="text-xs text-text-light mt-1 text-center italic">Only blurred images are shown for privacy.</p>

                            <hr class="my-4">

                            <!-- Teen Consent Toggle -->
                            <div class="flex items-center justify-between">
                                <p class="text-sm font-medium text-text-dark">Teen Consented Status:</p>
                                <div class="flex items-center space-x-2">
                                    <span class="text-safe font-bold">Yes</span>
                                    <input type="checkbox" id="teenConsent" class="hidden toggle-switch-input" checked>
                                    <label for="teenConsent" class="toggle-switch-label bg-safe"></label>
                                </div>
                            </div>
                        </div>

                        <!-- Mock Blurred Screenshot Preview (Updated text color to 'alert') -->
                        <div id="screenshotPreview" class="hidden bg-white p-3 rounded-xl shadow-md border border-gray-200">
                             <p class="text-sm font-semibold text-text-dark mb-2">Screenshot Preview (9:16 PM)</p>
                             <img src="https://placehold.co/400x200/cccccc/333333?text=BLURRED+SCREENSHOT+PREVIEW"
                                  alt="Blurred screenshot preview"
                                  class="w-full rounded-lg filter blur-sm">
                             <p class="text-xs text-alert mt-2 font-medium">Flagged area: Chat Window.</p>
                        </div>
                    </div>
                </div>
            `;
        }

        function renderRulesPanel() {
            return `
                <div class="space-y-6">
                    <h2 class="text-2xl font-semibold text-text-dark flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7 mr-3 text-primary" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 19c0 .5-.5 1-1 1H6c-.5 0-1-.5-1-1V5c0-.5.5-1 1-1h12c.5 0 1 .5 1 1v14z"/><path d="M17 10h-2M17 14h-6"/></svg>
                        Smart Rules Panel
                    </h2>
                    <p class="text-text-light text-lg">Automate safety with powerful rule templates.</p>

                    <!-- Smart Suggestions Section (Updated to use brighter 'info') -->
                    <div class="bg-info/20 p-4 rounded-xl border border-info shadow-sm">
                        <h3 class="text-xl font-bold text-info flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M12 16v-4"/><path d="M12 8h.01"/></svg>
                            Smart Suggestion (Einstein AI)
                        </h3>
                        <p class="text-gray-700 mt-2">
                            "We noticed **late-night app usage** (after 10:00 PM) 3 times this week. Create a bedtime limit now?"
                        </p>
                        <button class="mt-3 py-1 px-4 text-sm bg-info text-gray-800 font-semibold rounded-lg hover:bg-info/80 transition duration-200">
                            Apply Bedtime Rule
                        </button>
                    </div>

                    <!-- Quick Templates -->
                    <div class="space-y-4">
                        <h3 class="text-xl font-semibold text-text-dark pt-2">Quick Templates</h3>
                        
                        <!-- Template 1: School Mode -->
                        <div class="flex items-center justify-between bg-white p-4 rounded-xl shadow-md border-l-4 border-primary">
                            <div>
                                <p class="font-bold text-text-dark">🏫 "School Mode"</p>
                                <p class="text-sm text-text-light">Block all apps except Education and utility apps (9:00 AM - 3:00 PM).</p>
                            </div>
                            <div class="flex items-center">
                                <input type="checkbox" id="schoolMode" class="hidden toggle-switch-input">
                                <label for="schoolMode" class="toggle-switch-label"></label>
                            </div>
                        </div>

                        <!-- Template 2: Bedtime (Updated to use new 'alert' color) -->
                        <div class="flex items-center justify-between bg-white p-4 rounded-xl shadow-md border-l-4 border-alert">
                            <div>
                                <p class="font-bold text-text-dark">🌙 "Bedtime"</p>
                                <p class="text-sm text-text-light">Block social media and gaming after 9:30 PM.</p>
                            </div>
                            <div class="flex items-center">
                                <input type="checkbox" id="bedtimeMode" class="hidden toggle-switch-input" checked>
                                <label for="bedtimeMode" class="toggle-switch-label bg-safe"></label>
                            </div>
                        </div>
                    </div>

                </div>
            `;
        }
        
        // --- CORE NAVIGATION LOGIC ---

        function changeScreen(screenName) {
            // Only update screen and show header/footer if not in onboarding flow
            if (screenName === 'dashboard' || screenName === 'liveInsight' || screenName === 'rules' || screenName === 'settings') {
                currentScreen = screenName;
                headerElement.classList.remove('hidden');
                footerElement.classList.remove('hidden');
                // Restore dashboard specific padding/layout
                mainContent.style.padding = '5rem 1rem 5rem 1rem'; 
                mainContent.classList.add('space-y-6');

                let contentHTML = '';

                switch (screenName) {
                    case 'liveInsight':
                        contentHTML = renderLiveInsight();
                        break;
                    case 'rules':
                        contentHTML = renderRulesPanel();
                        break;
                    case 'dashboard':
                    default:
                        contentHTML = renderDashboard();
                }

                // Update main content
                mainContent.innerHTML = contentHTML;
                // Update navigation bar
                updateNavBar();
            } else if (screenName === 'onboarding') {
                // If explicitly told to go to onboarding, restart the flow
                onboardingStep = 1;
                renderOnboarding();
            }
        }

        function updateNavBar() {
            const navItems = [
                { name: 'dashboard', label: 'Home', icon: '<path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/>' },
                { name: 'liveInsight', label: 'Insights', icon: '<path d="M3 3v18h18"/><path d="M18 17V9"/><path d="M13 17V5"/><path d="M8 17v-3"/>' },
                { name: 'rules', label: 'Rules', icon: '<path d="M4 14.899A7 7 0 1 1 15.71 8h1.79a4.5 4.5 0 0 1 2.5 8.242"/><path d="M12 12v6"/><path d="M9 15l3 3 3-3"/>' },
                { name: 'settings', label: 'Settings', icon: '<circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/>' },
            ];

            bottomNav.innerHTML = navItems.map(item => {
                const isActive = item.name === currentScreen;
                const activeClasses = isActive ? 'text-primary font-bold' : 'text-gray-500';
                const clickAction = item.name === 'settings' ? "showNotification('Settings panel navigation not implemented yet.')" : `changeScreen('${item.name}')`;

                return `
                    <div class="flex flex-col items-center nav-item cursor-pointer p-1 ${activeClasses}" onclick="${clickAction}">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="${isActive ? 'currentColor' : 'none'}" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">${item.icon}</svg>
                        <span class="text-xs mt-1">${item.label}</span>
                    </div>
                `;
            }).join('');
        }

        function requestScreenshot(event) {
            showNotification('Screenshot Request Sent! A blurred image will arrive shortly.');
            
            const previewElement = document.getElementById('screenshotPreview');
            // Safely get the button element from the event target
            const button = event.target.closest('button');

            if (!button) return; // Prevent errors if the event target is missing

            button.disabled = true;
            button.textContent = 'Requesting...';
            button.classList.add('opacity-50');

            // Mock waiting for the image to arrive
            setTimeout(() => {
                if (previewElement) {
                    previewElement.classList.remove('hidden');
                }
                showNotification('Blurred Screenshot Received!');
                
                button.disabled = false;
                button.textContent = 'Request Screenshot (Blurred Preview)';
                button.classList.remove('opacity-50');
            }, 2500);
        }


        document.addEventListener('DOMContentLoaded', () => {
             // Initial render: always start with the onboarding flow
            renderOnboarding();

             // Mock Event Listeners for Long Press on Dashboard (Home screen)
            function setupDashboardLongPress() {
                const aiRiskCard = document.getElementById('aiRiskCard');
                if (!aiRiskCard) return;

                let pressTimer;

                const longPressAction = () => {
                     showNotification('Long Press Triggered: Creating Quick Rule...');
                     // After long press, navigate to rules panel
                     setTimeout(() => changeScreen('rules'), 500);
                };

                const startPress = (e) => {
                    // Only set up if we are on the dashboard screen
                    if (currentScreen !== 'dashboard') return;

                    // Prevent the default click action during a press
                    if (e.type === 'mousedown' || e.type === 'touchstart') {
                        // Temporarily disable the immediate click handler to allow long press detection
                        aiRiskCard.originalOnClick = aiRiskCard.onclick;
                        aiRiskCard.onclick = null; 
                    }
                    
                    pressTimer = window.setTimeout(longPressAction, 700); 
                };

                const endPress = (e) => {
                    window.clearTimeout(pressTimer);
                    
                    // Re-enable the click if it was a short press
                    if (aiRiskCard.originalOnClick) {
                         // A short delay to prevent the 'mouseup' from triggering the click immediately after a touchstart/touchend sequence
                         setTimeout(() => {
                            aiRiskCard.onclick = aiRiskCard.originalOnClick;
                            aiRiskCard.originalOnClick = null;
                        }, 0);
                    }
                };

                // Remove existing listeners before adding new ones (prevents duplicates after re-render)
                aiRiskCard.removeEventListener('mousedown', startPress, false);
                aiRiskCard.removeEventListener('touchstart', startPress, false);
                aiRiskCard.removeEventListener('mouseup', endPress, false);
                aiRiskCard.removeEventListener('mouseleave', endPress, false);
                aiRiskCard.removeEventListener('touchend', endPress, false);

                // Add new listeners
                aiRiskCard.addEventListener('mousedown', startPress, false);
                aiRiskCard.addEventListener('touchstart', startPress, false);
                aiRiskCard.addEventListener('mouseup', endPress, false);
                aiRiskCard.addEventListener('mouseleave', endPress, false);
                aiRiskCard.addEventListener('touchend', endPress, false);
            }

            // Observe the main content area for changes to re-bind the long press listener 
            // once the dashboard is rendered after onboarding is complete.
            const observer = new MutationObserver(function(mutationsList, observer) {
                for(const mutation of mutationsList) {
                    if (mutation.type === 'childList') {
                        if (currentScreen === 'dashboard') {
                            setupDashboardLongPress();
                        }
                    }
                }
            });

            // Start observing the target node for configured mutations
            observer.observe(mainContent.parentElement, { childList: true, subtree: true });

        });
    </script>
</body>
</html>

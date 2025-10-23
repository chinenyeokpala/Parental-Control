<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAFEHAVEN Parent Dashboard</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
            height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        /* --- SAFEHAVEN Color Palette: DARK PINK & BLACK --- */
        :root {
            --primary-pink: #E91E63; /* Primary/Trust/Action - Deep Pink */
            --light-pink: #F48FB1; /* Awareness/Accent */
            --warm-coral: #FF8A65; /* Alerts (kept for high visibility) */
            --white: #FFFFFF; 
            --dark-shell: #000000; /* True Black */
            --green-safe: #4ade80; /* Safe Status */
            --text-dark: #1f2937; /* Dark text for contrast */
        }

        /* --- Phone Shell Styling (Re-used for presentation) --- */
        #phone-shell {
            width: 100%;
            max-width: 400px;
            height: 95vh;
            max-height: 750px; 
            background-color: var(--dark-shell); 
            border-radius: 3rem; 
            padding: 10px; 
            box-shadow: 0 0 0 10px var(--dark-shell), 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
        }
        #content-wrapper {
            flex-grow: 1;
            background-color: var(--white);
            border-radius: 2.5rem; 
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        .view-content {
            flex-grow: 1;
            overflow-y: auto;
            padding: 1.5rem;
            background-color: #f8fafc; /* Light off-white background for cards */
        }

        /* Custom Toggle Switch Styles */
        .toggle-switch {
            width: 48px;
            height: 28px;
            background-color: #ccc;
            border-radius: 14px;
            position: relative;
            transition: background-color 0.4s;
            cursor: pointer;
        }
        .toggle-switch::after {
            content: '';
            width: 20px;
            height: 20px;
            background-color: white;
            border-radius: 50%;
            position: absolute;
            top: 4px;
            left: 4px;
            transition: transform 0.4s;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.4);
        }
        .toggle-switch.on {
            background-color: var(--primary-pink);
        }
        .toggle-switch.on::after {
            transform: translateX(20px);
        }

        /* Custom Range Slider Track (Pink color) */
        input[type=range]::-webkit-slider-runnable-track {
            background: #d1d5db; /* Default gray track */
        }
        input[type=range]::-webkit-slider-thumb {
            -webkit-appearance: none;
            height: 20px;
            width: 20px;
            border-radius: 50%;
            background: var(--primary-pink);
            cursor: pointer;
            margin-top: -6px; /* Adjust vertical alignment */
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.4);
        }
    </style>
</head>
<body class="bg-gray-100">

    <div id="phone-shell">
        <div id="content-wrapper">
            <!-- Content Area -->
            <div id="content-area" class="view-content">
                <!-- Content will be dynamically injected here -->
            </div>
            
            <!-- Navigation Bar (Only visible when not on setup) -->
            <nav id="nav-bar" class="bg-white border-t border-gray-100 p-3 flex justify-around items-center rounded-b-[2.5rem] shadow-2xl hidden">
                <!-- Home Icon -->
                <button id="nav-dashboard" onclick="navigate('dashboard')" class="nav-item flex flex-col items-center text-xs font-semibold text-gray-400">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
                    Home
                </button>
                <!-- Insights Icon -->
                <button id="nav-insights" onclick="navigate('insights')" class="nav-item flex flex-col items-center text-xs text-gray-400">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><path d="M14 2v6h6"/><path d="M10 15h4"/><path d="M12 18V12"/></svg>
                    Insights
                </button>
                <!-- Rules Icon -->
                <button id="nav-rules" onclick="navigate('rules')" class="nav-item flex flex-col items-center text-xs text-gray-400">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3v18h18"/><path d="M18 17V9"/><path d="M13 17V5"/><path d="M8 17v2"/></svg>
                    Rules
                </button>
                <!-- Settings Icon -->
                <button id="nav-settings" onclick="navigate('settings')" class="nav-item flex flex-col items-center text-xs text-gray-400">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9v-.09A1.65 1.65 0 0 0 10.6 3a1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.82.33z"/></svg>
                    Settings
                </button>
            </nav>
        </div>
    </div>

    <script>
        // --- Application State ---
        let currentPage = 'setup'; // Start on the new setup screen
        let setupError = '';
        
        let appState = {
            // Dashboard Display Data
            childName: 'Maya',
            childStatus: 'Online', 
            childBattery: 85,
            screenTime: {
                weekdayLimit: 240, 
                weekendLimit: 360, 
                usedToday: 190, 
            },
            filters: { // This state is updated by the dashboard sliders
                socialMedia: true,
                gaming: false,
                adultContent: true,
                shopping: false
            },
            // Setup Configuration Data
            setup: {
                role: 'parent',
                email: 'mom@example.com', // Pre-fill for convenience
                childCode: 'SAFE123',     // Pre-fill for convenience
                ageGroup: 'teen', // 'child' | 'teen' | 'young-adult'
                features: {
                    screenTimeControl: true,
                    contentFiltering: true,
                    locationTracking: true,
                    chatWatch: false,
                }
            },
            // Insights Data
            activityLog: [
                { time: '10:45 AM', type: 'location', detail: 'Arrived at Central High School.', icon: '<path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><circle cx="12" cy="10" r="3"/>', color: 'var(--green-safe)' },
                { time: '11:15 AM', type: 'app', detail: 'Used TikTok (35 mins).', icon: '<path d="M22 4s-.7 2.1-2 3.4c1.6 10-9.4 17.3-18 11.6 2.2.1 4.4-.6 6-2 1.7-1.4 3-3.6 3-6.1 0-2.4-.6-4.7-2.6-6.4 1.4-.4 2.8-.8 4.3-1.4.3-1.6 1.4-2.8 3-3.2"/>', color: 'var(--light-pink)' },
                { time: '12:01 PM', type: 'blocked', detail: 'Attempted to access risky content (NSFW).', icon: '<path d="M18 6 6 18"/><path d="m6 6 12 12"/>', color: 'var(--warm-coral)' },
                { time: '01:30 PM', type: 'screen', detail: 'Screen Time Limit extended by 30 mins.', icon: '<circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/>', color: 'var(--primary-pink)' },
                { time: '02:40 PM', type: 'chat', detail: 'Flagged chat: keyword "bully" detected in Discord.', icon: '<path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="16 11 12 15 8 11"/><line x1="12" x2="12" y1="15" y2="3"/>', color: 'var(--warm-coral)' },
            ]
        };
        
        // --- Utility Functions ---

        // Converts minutes to H hours M minutes format
        function formatMinutes(minutes) {
            const h = Math.floor(minutes / 60);
            const m = minutes % 60;
            if (h > 0) return `${h} hrs ${m} mins`;
            return `${m} mins`;
        }

        // Updates setup state fields (email, code, ageGroup)
        window.updateSetup = function(field, value) {
            setupError = '';
            appState.setup[field] = value;

            // Logic to adjust suggested features based on Age Group (Monitoring Level)
            if (field === 'ageGroup') {
                if (value === 'child') {
                    appState.setup.features.screenTimeControl = true;
                    appState.setup.features.contentFiltering = true;
                    appState.setup.features.locationTracking = true;
                    appState.setup.features.chatWatch = true; // High monitoring default
                } else if (value === 'teen') {
                    appState.setup.features.screenTimeControl = true;
                    appState.setup.features.contentFiltering = true;
                    appState.setup.features.locationTracking = true;
                    appState.setup.features.chatWatch = false; // Moderate monitoring default
                } else if (value === 'young-adult') {
                    appState.setup.features.screenTimeControl = false;
                    appState.setup.features.contentFiltering = false;
                    appState.setup.features.locationTracking = false;
                    appState.setup.features.chatWatch = false; // Low/None monitoring default
                }
                render(); // Re-render the setup view to update feature toggles
            }
        }
        
        // Updates the state for feature toggles in setup
        window.updateSetupFeature = function(featureName, element) {
            const currentState = appState.setup.features[featureName];
            appState.setup.features[featureName] = !currentState;
            element.classList.toggle('on', !currentState);
        }

        // Handles transition from setup to dashboard
        window.handleSetupComplete = function() {
            setupError = '';
            
            if (!appState.setup.email.includes('@') || appState.setup.email.length < 5) {
                setupError = "Please enter a valid Parent Email address.";
            } else if (appState.setup.childCode.length < 5) {
                setupError = "Please enter the Child Link Code from the device.";
            } else if (!appState.setup.ageGroup) {
                setupError = "Please select a monitoring level based on your child's age.";
            }

            if (setupError) {
                render(); 
                return;
            }

            // Mock Success: Copy final selected features from setup to live filters
            appState.filters.socialMedia = appState.setup.features.contentFiltering;
            appState.filters.gaming = appState.setup.features.contentFiltering;
            appState.filters.adultContent = appState.setup.features.contentFiltering;
            appState.filters.chatWatchStatus = appState.setup.features.chatWatch; // Used for Dashboard card logic

            // Navigate to the Dashboard
            currentPage = 'dashboard';
            render();
        }


        // --- Dashboard Core Functions (Event Handlers) ---
        
        window.updateScreenTime = function(dayType, element) {
            const value = parseInt(element.value);
            const displayElement = document.getElementById(`${dayType}-display`);
            
            appState.screenTime[`${dayType}Limit`] = value;
            displayElement.textContent = formatMinutes(value);
        }

        window.toggleFilter = function(filterName, element) {
            const currentState = appState.filters[filterName];
            appState.filters[filterName] = !currentState;
            element.classList.toggle('on', !currentState);
        }

        // --- View Definitions (HTML Templates) ---

        const setupView = `
            <div class="h-full flex flex-col justify-between p-2 space-y-4">
                <div class="flex flex-col items-center text-center">
                    <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mb-3" style="color: var(--primary-pink);">
                        <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="M8 12l2 2 4-4"/>
                    </svg>
                    <h1 class="text-3xl font-extrabold text-gray-800 mb-1">SAFEHAVEN</h1>
                    <p class="text-sm text-gray-500">Empowering families with trust, safety, and awareness.</p>
                </div>

                <div class="space-y-6 flex-grow">
                    <!-- STEP 1: Role Selection (Only Parent flow enabled for prototype) -->
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-2">1. Your Role</label>
                        <button class="w-full p-3 border-2 border-green-500 bg-green-50 rounded-xl shadow-sm text-lg font-bold text-green-700">
                            I'm a Parent 👩‍👧
                        </button>
                        <button class="w-full p-3 border-2 border-gray-200 bg-white rounded-xl shadow-sm text-lg font-bold text-gray-400 mt-2 cursor-default">
                            I'm a Teen 🧑‍💻 (Coming Soon)
                        </button>
                    </div>

                    <!-- STEP 2: Device Connection & Sign-on -->
                    <div class="space-y-3">
                        <label class="block text-sm font-semibold text-gray-700 mb-2">2. Link Account & Device</label>
                        <input type="email" id="parent-email" value="${appState.setup.email}" oninput="updateSetup('email', this.value)"
                               class="w-full p-3 border border-gray-300 rounded-xl shadow-sm focus:ring-pink-500 focus:border-pink-500"
                               placeholder="Parent Email (for alerts)">
                        <input type="text" id="child-code" value="${appState.setup.childCode}" oninput="updateSetup('childCode', this.value)"
                               class="w-full p-3 border border-gray-300 rounded-xl shadow-sm focus:ring-pink-500 focus:border-pink-500"
                               placeholder="Child's Link Code (from their phone)">
                    </div>

                    <!-- STEP 3: Monitoring Level (Age-Based) -->
                    <div class="space-y-3 p-3 bg-white rounded-xl border border-gray-200">
                        <label class="block text-sm font-semibold text-gray-700 mb-3">3. Monitoring Level (Child's Age/Maturity)</label>
                        <div class="flex justify-between space-x-2">
                            ${[
                                {key: 'child', label: 'Child (High)', desc: 'Full control, high alerts.'},
                                {key: 'teen', label: 'Teen (Moderate)', desc: 'Time limits, focus on safety.'},
                                {key: 'young-adult', label: 'Young Adult (Low)', desc: 'Visibility only, minimal limits.'}
                            ].map(option => `
                                <div class="flex-1">
                                    <input type="radio" id="age-${option.key}" name="age-group" value="${option.key}"
                                           class="hidden" 
                                           ${appState.setup.ageGroup === option.key ? 'checked' : ''}
                                           onchange="updateSetup('ageGroup', this.value)">
                                    <label for="age-${option.key}" class="p-2 border-2 rounded-xl text-center block transition duration-200 cursor-pointer ${appState.setup.ageGroup === option.key ? 'border-[var(--primary-pink)] bg-[var(--primary-pink)] text-white shadow-md' : 'border-gray-300 bg-gray-50 text-gray-700 hover:border-[var(--primary-pink)]'}">
                                        <span class="font-bold text-sm">${option.label}</span>
                                    </label>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                    
                    <!-- STEP 4: Feature Selection -->
                    <div class="space-y-2 p-3 bg-white rounded-xl border border-gray-200">
                        <label class="block text-sm font-semibold text-gray-700 mb-2">4. Custom Security Features</label>
                        ${[
                            {key: 'screenTimeControl', label: 'Screen Time Limits', icon: '<path d="M12 2v6"/><path d="M12 18v4"/><circle cx="12" cy="12" r="7"/>'},
                            {key: 'contentFiltering', label: 'App & Web Filtering', icon: '<path d="M18 6 6 18"/><path d="m6 6 12 12"/>'},
                            {key: 'locationTracking', label: 'Real-Time Location', icon: '<path d="M20.2 10a8 8 0 0 0-16.3-2.1"/><path d="M12 2v6"/>'},
                            {key: 'chatWatch', label: 'Social Chat Monitoring', icon: '<path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="16 11 12 15 8 11"/><line x1="12" x2="12" y1="15" y2="3"/>'}
                        ].map(feature => `
                            <div class="flex justify-between items-center py-1">
                                <span class="text-sm text-gray-700 flex items-center">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2" style="color: var(--primary-pink);">${feature.icon}</svg>
                                    ${feature.label}
                                </span>
                                <div id="toggle-setup-${feature.key}" class="toggle-switch ${appState.setup.features[feature.key] ? 'on' : ''}" 
                                     onclick="updateSetupFeature('${feature.key}', this)"></div>
                            </div>
                        `).join('')}
                    </div>

                    <!-- ERROR MESSAGE DISPLAY -->
                    ${setupError ? `<div class="p-2 text-sm text-red-700 bg-red-100 border border-red-300 rounded-lg text-center">${setupError}</div>` : ''}
                </div>

                <!-- Call to Action -->
                <button onclick="handleSetupComplete()" 
                        style="background-color: var(--primary-pink);" 
                        class="py-3 px-6 rounded-xl text-white font-extrabold shadow-lg hover:opacity-90 transition duration-150 w-full">
                    Let’s Build a Safe Space
                </button>
            </div>
        `;

        const dashboardView = `
            <!-- Top Bar: Child Status -->
            <div class="flex justify-between items-center pb-4 border-b border-gray-100 sticky top-0 bg-white/90 backdrop-blur-sm z-10 -mx-1.5 -mt-1.5 px-1.5 pt-1.5 rounded-t-3xl">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 rounded-full bg-gray-300 flex items-center justify-center text-white font-bold text-lg">M</div>
                    <div>
                        <p class="text-sm font-semibold text-gray-800">${appState.childName}</p>
                        <div class="flex items-center text-xs space-x-1 ${appState.childStatus === 'Online' ? 'text-[var(--green-safe)]' : 'text-gray-500'}">
                            <span class="w-2 h-2 rounded-full ${appState.childStatus === 'Online' ? 'bg-[var(--green-safe)]' : 'bg-gray-400'}"></span>
                            <span>${appState.childStatus}</span>
                        </div>
                    </div>
                </div>
                <!-- Battery Status -->
                <div class="flex items-center text-sm text-gray-500">
                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-1"><rect width="16" height="10" x="2" y="7" rx="2" ry="2"/><line x1="22" x2="22" y1="11" y2="13"/></svg>
                    ${appState.childBattery}%
                </div>
            </div>

            <div class="py-4 space-y-4">
                <h1 class="text-2xl font-extrabold text-gray-900">Dashboard</h1>
                
                <!-- Main Dashboard Cards Grid -->
                <div class="grid grid-cols-2 gap-3">
                    
                    <!-- AI Risk Score -->
                    <div class="p-4 rounded-xl shadow-md cursor-pointer transition duration-200 bg-white hover:shadow-lg border-t-4" style="border-color: var(--green-safe);">
                        <p class="text-sm text-gray-500">AI Risk Score</p>
                        <p class="text-3xl font-extrabold my-1" style="color: var(--green-safe);">85%</p>
                        <p class="text-xs text-gray-600">Your child is safe today.</p>
                    </div>

                    <!-- Blocked Alerts -->
                    <div onclick="navigate('insights')" class="p-4 rounded-xl shadow-md cursor-pointer transition duration-200 bg-white hover:shadow-lg border-t-4" style="border-color: var(--warm-coral);">
                        <p class="text-sm text-gray-500">Blocked Alerts</p>
                        <p class="text-3xl font-extrabold text-gray-800 my-1">2</p>
                        <p class="text-xs text-gray-600">risky websites blocked.</p>
                    </div>
                    
                    <!-- Social Chat Watch -->
                    <div onclick="navigate('insights')" class="p-4 rounded-xl shadow-md cursor-pointer transition duration-200 bg-white hover:shadow-lg border-t-4 ${appState.setup.features.chatWatch ? 'border-[var(--light-pink)]' : 'border-gray-200'}">
                        <p class="text-sm text-gray-500">Chat Watch</p>
                        <p class="text-3xl font-extrabold text-gray-800 my-1">${appState.setup.features.chatWatch ? '1' : 'Off'}</p>
                        <p class="text-xs text-gray-600">${appState.setup.features.chatWatch ? 'flagged conversation.' : 'Monitoring Disabled.'}</p>
                    </div>
                    
                    <!-- Screen Time Used -->
                    <div class="p-4 rounded-xl shadow-md cursor-pointer transition duration-200 bg-white hover:shadow-lg border-t-4" style="border-color: var(--primary-pink);">
                        <p class="text-sm text-gray-500">Screen Time Used</p>
                        <p class="text-2xl font-extrabold text-gray-800 my-1">${formatMinutes(appState.screenTime.usedToday)}</p>
                        <p class="text-xs text-gray-600">of ${formatMinutes(appState.screenTime.weekdayLimit)} limit.</p>
                    </div>

                </div>

                <!-- Screen Time Settings Card (Only shown if enabled in setup) -->
                ${appState.setup.features.screenTimeControl ? `
                <div class="p-4 rounded-xl shadow-lg bg-white border border-gray-100 space-y-4">
                    <h2 class="text-lg font-bold text-gray-800 flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2" style="color: var(--primary-pink);"><path d="M12 2v6"/><path d="M12 18v4"/><path d="M4.93 4.93l3.54 3.54"/><path d="M15.53 15.53l3.54 3.54"/><path d="M2 12h6"/><path d="M18 12h4"/><path d="M4.93 19.07l3.54-3.54"/><path d="M15.53 8.47l3.54-3.54"/><circle cx="12" cy="12" r="7"/></svg>
                        Daily Time Limits
                    </h2>
                    
                    <!-- Weekday Slider -->
                    <div>
                        <div class="flex justify-between items-center mb-1">
                            <label class="text-sm font-medium text-gray-700">Weekday Limit:</label>
                            <span id="weekday-display" class="font-bold text-base" style="color: var(--primary-pink);">${formatMinutes(appState.screenTime.weekdayLimit)}</span>
                        </div>
                        <input type="range" min="60" max="600" value="${appState.screenTime.weekdayLimit}" step="30" 
                               oninput="updateScreenTime('weekday', this)"
                               class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer range-lg">
                        <div class="flex justify-between text-xs text-gray-500 mt-1"><span>1 hr</span><span>10 hrs</span></div>
                    </div>

                    <!-- Weekend Slider -->
                    <div>
                        <div class="flex justify-between items-center mb-1">
                            <label class="text-sm font-medium text-gray-700">Weekend Limit:</label>
                            <span id="weekend-display" class="font-bold text-base" style="color: var(--primary-pink);">${formatMinutes(appState.screenTime.weekendLimit)}</span>
                        </div>
                        <input type="range" min="120" max="720" value="${appState.screenTime.weekendLimit}" step="60" 
                               oninput="updateScreenTime('weekend', this)"
                               class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer range-lg">
                        <div class="flex justify-between text-xs text-gray-500 mt-1"><span>2 hrs</span><span>12 hrs</span></div>
                    </div>
                </div>
                ` : `<div class="p-4 rounded-xl shadow-lg bg-gray-100 border border-gray-200 text-center text-sm text-gray-500">Screen Time Control is disabled in your current settings.</div>`}

                <!-- App/Web Filtering Card (Only shown if enabled in setup) -->
                ${appState.setup.features.contentFiltering ? `
                <div class="p-4 rounded-xl shadow-lg bg-white border border-gray-100 space-y-3">
                    <h2 class="text-lg font-bold text-gray-800 flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2 text-red-500"><path d="M18 6 6 18"/><path d="m6 6 12 12"/></svg>
                        Content Filtering
                    </h2>
                    
                    ${Object.keys(appState.filters).map(key => {
                        const label = key.charAt(0).toUpperCase() + key.slice(1).replace(/([A-Z])/g, ' $1'); // Format: socialMedia -> Social Media
                        const isOn = appState.filters[key];
                        // Exclude chatWatchStatus from this list, as it's a dashboard state, not a filter category
                        if(key === 'chatWatchStatus') return '';
                        return `
                            <div class="flex justify-between items-center py-1">
                                <span class="text-sm text-gray-700">${label}</span>
                                <div id="toggle-${key}" class="toggle-switch ${isOn ? 'on' : ''}" 
                                     onclick="toggleFilter('${key}', this)"></div>
                            </div>
                        `;
                    }).join('')}
                </div>
                ` : `<div class="p-4 rounded-xl shadow-lg bg-gray-100 border border-gray-200 text-center text-sm text-gray-500">Content Filtering is disabled in your current settings.</div>`}
                
                <!-- Location Placeholder Card (Only shown if enabled in setup) -->
                ${appState.setup.features.locationTracking ? `
                <div class="p-4 rounded-xl shadow-lg bg-white border border-gray-100">
                    <h2 class="text-lg font-bold text-gray-800 mb-2 flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2 text-red-500"><path d="M20.2 10a8 8 0 0 0-16.3-2.1c.7-2.6 3.1-4.7 6.6-5.8"/><path d="M12 2v6"/><path d="M10 20h4"/></svg>
                        Last Known Location
                    </h2>
                    <p class="text-xs text-gray-500 mb-3">Updated 2 mins ago at Central High School.</p>
                    <img src="https://placehold.co/400x150/000000/E91E63?text=Mock+Map+Placeholder" 
                         alt="Map Placeholder" 
                         class="w-full rounded-xl border border-gray-200">
                </div>
                ` : `<div class="p-4 rounded-xl shadow-lg bg-gray-100 border border-gray-200 text-center text-sm text-gray-500">Location Tracking is disabled in your current settings.</div>`}
            </div>
        `;

        const insightsView = `
            <div class="py-4 space-y-5">
                <h1 class="text-2xl font-extrabold text-gray-900">Activity Insights</h1>

                <!-- AI Summary Card -->
                <div class="p-4 rounded-xl shadow-xl bg-white border-2 border-[var(--primary-pink)] space-y-3">
                    <div class="flex items-center justify-between">
                        <h2 class="text-base font-extrabold text-gray-800 flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2" style="color: var(--primary-pink);"><circle cx="12" cy="12" r="10"/><path d="M9 10a5 5 0 0 1 6 0"/><path d="M15 17c-2 2-4 2-6 0"/></svg>
                            AI Safety Summary
                        </h2>
                        <span class="text-xs text-gray-500">Just now</span>
                    </div>
                    <div class="bg-gray-50 p-3 rounded-lg text-sm text-[var(--text-dark)] border border-gray-200">
                        <p class="mb-2 font-semibold">"Today's risk score is **85% (Safe)**. Maya's screen time usage is moderate, currently at 3 hours 10 mins. There was a concerning chat interaction (Discord) flagged for **bullying keywords** at 2:40 PM. Two attempts to access adult content were automatically blocked by the filter."</p>
                        <button class="text-xs font-bold px-3 py-1 rounded-full text-white hover:opacity-90 transition duration-150" style="background-color: var(--primary-pink);">
                            View Flagged Chat Details
                        </button>
                    </div>
                </div>

                <!-- Activity Feed -->
                <h2 class="text-xl font-bold text-gray-800 pt-2">Timeline of Events</h2>
                <div class="space-y-4">
                    ${appState.activityLog.map(item => `
                        <div class="flex items-start space-x-3 p-3 bg-white rounded-xl shadow-sm border-l-4" style="border-color: ${item.color};">
                            <div class="mt-1 w-6 h-6 flex-shrink-0">
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: ${item.color};">${item.icon}</svg>
                            </div>
                            <div class="flex-grow">
                                <p class="text-sm font-semibold text-gray-800">${item.detail}</p>
                                <p class="text-xs text-gray-500">${item.time} - ${item.type.toUpperCase()}</p>
                            </div>
                        </div>
                    `).join('')}
                    
                    <div class="text-center text-sm text-gray-500 pt-2">--- End of Today's Activity ---</div>
                </div>
            </div>
        `;

        const rulesView = `
            <div class="flex flex-col items-center justify-center h-full text-center p-8">
                <h1 class="text-2xl font-bold mb-2" style="color: var(--primary-pink);">Smart Rules Panel</h1>
                <p class="text-gray-500 mb-4">This screen is where you'll define custom automation rules and view AI suggestions for safety policies.</p>
                <div class="p-4 bg-white rounded-xl shadow-md border-t-4 border-[var(--primary-pink)] w-full max-w-xs">
                    <p class="font-semibold text-gray-800">Coming soon:</p>
                    <ul class="text-sm text-left text-gray-600 list-disc list-inside mt-2">
                        <li>Time-based App Blocking</li>
                        <li>Geofence Alerts (Leaving school)</li>
                        <li>Rule Templates (Study Mode)</li>
                    </ul>
                </div>
            </div>
        `;
        
        const settingsView = `
            <div class="flex flex-col items-center justify-center h-full text-center p-8">
                <h1 class="text-2xl font-bold mb-2" style="color: var(--primary-pink);">App Settings</h1>
                <p class="text-gray-500 mb-4">This screen will manage account, notifications, and device linking.</p>
                <button onclick="navigate('dashboard')" class="mt-4 p-3 text-sm font-bold text-white rounded-xl shadow-md hover:opacity-90" style="background-color: var(--primary-pink);">Back to Dashboard</button>
            </div>
        `;


        // --- Render and Navigation Logic ---
        
        // Generic navigation function
        window.navigate = function(page) {
            currentPage = page;
            render();
        }

        function setActiveNav() {
            // Remove active style from all nav items
            document.querySelectorAll('.nav-item').forEach(button => {
                button.style.color = 'rgb(156 163 175)'; // gray-400
                button.classList.remove('font-semibold');
            });

            // Apply active style to the current page's nav item
            const activeNav = document.getElementById(`nav-${currentPage}`);
            if (activeNav) {
                activeNav.style.color = 'var(--primary-pink)';
                activeNav.classList.add('font-semibold');
            }
        }

        function render() {
            const contentArea = document.getElementById('content-area');
            const navBar = document.getElementById('nav-bar');
            
            // Render the correct view based on currentPage
            if (currentPage === 'setup') {
                contentArea.innerHTML = setupView;
                navBar.classList.add('hidden');
                contentArea.scrollTop = 0; 
            } else {
                let viewHtml = '';
                if (currentPage === 'dashboard') {
                    viewHtml = dashboardView;
                } else if (currentPage === 'insights') {
                    viewHtml = insightsView;
                } else if (currentPage === 'rules') {
                    viewHtml = rulesView;
                } else if (currentPage === 'settings') {
                    viewHtml = settingsView;
                }
                
                contentArea.innerHTML = viewHtml;
                navBar.classList.remove('hidden');
                setActiveNav(); // Highlight the active nav icon
                contentArea.scrollTop = 0; // Scroll to top on page change
            }
        }

        // Initialize the app on load
        window.onload = function() {
            render();
        };
    </script>
</body>
</html>

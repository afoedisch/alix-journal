# alix-journal
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ALIX FOEDISCH — Digital Journal</title>
    
    <!-- Tailwind CSS (Gives us easy, beautiful styles instantly) -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        serif: ['"Playfair Display"', 'Georgia', 'serif'],
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                        mono: ['"JetBrains Mono"', 'monospace'],
                    }
                }
            }
        }
    </script>
    
    <!-- Beautiful Fonts from Google -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Plus+Jakarta+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
    
    <style>
        /* Smooth transitions when you switch themes */
        * {
            transition: background-color 0.3s ease, border-color 0.3s ease, color 0.2s ease;
        }
        
        /* Premium custom scrollbars */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        .theme-cream ::-webkit-scrollbar-thumb {
            background: #e2dacb;
            border-radius: 3px;
        }
        .theme-dark ::-webkit-scrollbar-thumb {
            background: #2d2620;
            border-radius: 3px;
        }
        .theme-white ::-webkit-scrollbar-thumb {
            background: #e5e5e5;
            border-radius: 3px;
        }
    </style>
</head>
<body class="font-sans antialiased overflow-x-hidden theme-cream bg-[#faf7f2] text-[#2c2621]" id="body-root">

    <div class="min-h-screen flex flex-col md:flex-row">
        
        <!-- LEFT PANEL: YOUR ACTUAL PUBLIC WEBSITE -->
        <div class="flex-1 flex flex-col min-h-screen relative overflow-y-auto">
            
            <!-- Header bar with title, theme switches, and toggle button -->
            <header class="p-6 flex justify-between items-center border-b border-[#ebdcc8] sticky top-0 backdrop-blur-md bg-opacity-90 z-20" id="main-header">
                <div class="flex flex-col">
                    <!-- CHANGE YOUR NAME HERE -->
                    <h1 class="font-serif text-2xl font-bold tracking-tight" id="header-name">ALIX FOEDISCH</h1>
                    <!-- CHANGE YOUR SUBTITLE HERE -->
                    <span class="text-xs font-mono uppercase tracking-widest text-[#706456]" id="header-subtitle">Notes &amp; Narrative Closet</span>
                </div>
                
                <div class="flex items-center gap-3">
                    <!-- Themes Switcher Buttons -->
                    <div class="flex items-center gap-1 bg-black bg-opacity-5 p-1 rounded-full">
                        <button onclick="changeTheme('cream')" class="w-6 h-6 rounded-full bg-[#f4eee3] border-2 border-amber-600 scale-110" id="btn-theme-cream" title="Paper Cream"></button>
                        <button onclick="changeTheme('dark')" class="w-6 h-6 rounded-full bg-[#1c1815] border border-transparent" id="btn-theme-dark" title="Midnight Velvet"></button>
                        <button onclick="changeTheme('white')" class="w-6 h-6 rounded-full bg-white border border-transparent" id="btn-theme-white" title="Minimal Stark"></button>
                    </div>

                    <!-- Toggle Sidebar Button -->
                    <button onclick="toggleSidebar()" class="px-3 py-1.5 rounded-md text-xs font-mono flex items-center gap-1.5 border border-[#e6dcce] hover:bg-black hover:bg-opacity-5" id="sidebar-toggle-btn">
                        <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
                        <span id="toggle-btn-text">Hide Guide</span>
                    </button>
                </div>
            </header>

            <!-- Main Website Content area -->
            <main class="max-w-3xl mx-auto px-6 py-12 flex-1 w-full">
                
                <!-- Intro Quote -->
                <section class="mb-12 pb-12 border-b border-dashed border-[#e6dcce]" id="intro-divider">
                    <!-- CHANGE YOUR MAIN INTRO TEXT HERE -->
                    <p class="font-serif italic text-lg md:text-xl leading-relaxed text-opacity-90 max-w-2xl" id="intro-text">
                        "I collect pieces of scenes, characters left behind on stage, and alternative timelines. This is a public shelf of stories and unfinished ideas."
                    </p>
                </section>

                <!-- Navigation Tabs -->
                <div class="flex flex-wrap gap-2 mb-10" id="categories-container">
                    <!-- Built dynamically by JavaScript below -->
                </div>

                <!-- Feed Container (Dynamic Listing View or Focus Reading View) -->
                <div id="content-display-area">
                    <!-- Powered dynamically by JavaScript below -->
                </div>

            </main>

            <!-- Footer -->
            <footer class="p-8 text-center text-xs font-mono text-[#706456] border-t border-[#ebdcc8]" id="main-footer">
                © <span id="footer-year">2026</span> ALIX FOEDISCH • Proudly built minimal, public, and raw.
            </footer>
        </div>

        <!-- RIGHT PANEL: GETTING STARTED / CURATOR COMPANION (GUIDES YOU LOCALLY) -->
        <aside id="curator-sidebar" class="w-full md:w-[460px] bg-[#1a1816] text-gray-200 border-l border-neutral-800 p-6 overflow-y-auto flex flex-col justify-between max-h-screen shadow-2xl">
            <div>
                <div class="flex justify-between items-center mb-6 pb-4 border-b border-neutral-800">
                    <div class="flex items-center gap-2">
                        <span class="w-2.5 h-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
                        <h3 class="font-mono text-xs uppercase tracking-widest text-emerald-400 font-bold">Your Companion Guide</h3>
                    </div>
                    <button onclick="toggleSidebar()" class="text-gray-400 hover:text-white p-1 rounded">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                    </button>
                </div>

                <div class="space-y-6 text-sm leading-relaxed">
                    <!-- Welcome Box -->
                    <section class="bg-neutral-900 bg-opacity-70 p-4 rounded-lg border border-neutral-800">
                        <h4 class="font-bold text-emerald-300 font-serif mb-2 text-base">You are Ready for GitHub!</h4>
                        <p class="text-xs text-gray-300 leading-normal">
                            This single file contains everything you need. You can copy-paste it directly to a free GitHub repository and publish it to the live web. It has no build steps, compiling processes, or dependencies.
                        </p>
                    </section>

                    <!-- Design principles to keep this site beautiful -->
                    <section class="space-y-3">
                        <h4 class="font-mono text-xs uppercase tracking-wider text-amber-400 font-bold">Writing Structure Guide</h4>
                        
                        <div class="space-y-2 text-xs text-gray-400">
                            <div class="p-2.5 bg-neutral-900 rounded border-l-2 border-amber-500">
                                <strong class="text-white block mb-0.5">Short Stories:</strong> Keep descriptions sensory. Don't announce your story—let readers open directly into the environment.
                            </div>
                            <div class="p-2.5 bg-neutral-900 rounded border-l-2 border-emerald-500">
                                <strong class="text-white block mb-0.5">Fragments &amp; Ideas:</strong> Post numbered lists, interesting concepts, or single dialogue sentences that came to you at 2:00 AM.
                            </div>
                            <div class="p-2.5 bg-neutral-900 rounded border-l-2 border-blue-500">
                                <strong class="text-white block mb-0.5">Scribbles:</strong> Intimate personal reflection notes or actor's stage logs. These act as raw texture.
                            </div>
                        </div>
                    </section>

                    <!-- Interactive Live Customizer Sandbox -->
                    <section class="space-y-3 pt-2">
                        <h4 class="font-mono text-xs uppercase tracking-wider text-emerald-400 font-bold">Add / Edit Story Sandbox</h4>
                        <p class="text-[11px] text-gray-400 leading-snug">
                            Add a temporary story here to see how it instantly scales inside your theme structure! To save it permanently, open this `index.html` file in any text editor and edit the <code class="bg-neutral-800 px-1 py-0.5 text-white rounded text-[10px]">MY_STORIES</code> variable.
                        </p>
                        
                        <form id="sandbox-form" onsubmit="handleSandboxSubmit(event)" class="space-y-3 bg-neutral-950 p-4 rounded-lg border border-neutral-800 text-xs">
                            <div>
                                <label class="block text-[10px] uppercase font-mono tracking-wider text-gray-400 mb-1">Story Title</label>
                                <input id="sb-title" required type="text" placeholder="The Yellow Lighthouse" class="w-full bg-neutral-900 text-white border border-neutral-800 rounded px-2.5 py-1.5 focus:outline-none focus:border-emerald-500" />
                            </div>
                            <div class="grid grid-cols-2 gap-2">
                                <div>
                                    <label class="block text-[10px] uppercase font-mono tracking-wider text-gray-400 mb-1">Category</label>
                                    <select id="sb-category" class="w-full bg-neutral-900 text-white border border-neutral-800 rounded px-2.5 py-1.5 focus:outline-none focus:border-emerald-500">
                                        <option value="Short Stories">Short Stories</option>
                                        <option value="Fragments &amp; Ideas">Fragments &amp; Ideas</option>
                                        <option value="Scribbles">Scribbles</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-[10px] uppercase font-mono tracking-wider text-gray-400 mb-1">Tags (Comma split)</label>
                                    <input id="sb-tags" type="text" placeholder="Memory, Ocean" class="w-full bg-neutral-900 text-white border border-neutral-800 rounded px-2.5 py-1.5 focus:outline-none focus:border-emerald-500" />
                                </div>
                            </div>
                            <div>
                                <label class="block text-[10px] uppercase font-mono tracking-wider text-gray-400 mb-1">Content Prose</label>
                                <textarea id="sb-content" required rows="4" placeholder="Enter paragraph prose..." class="w-full bg-neutral-900 text-white border border-neutral-800 rounded px-2.5 py-1.5 focus:outline-none focus:border-emerald-500 font-serif"></textarea>
                            </div>
                            <button type="submit" class="w-full bg-emerald-500 hover:bg-emerald-400 text-black font-mono font-bold uppercase tracking-wider py-2 rounded">
                                Inject Live Preview
                            </button>
                        </form>
                    </section>
                </div>
            </div>

            <!-- Helpful notice -->
            <div class="mt-8 pt-4 border-t border-neutral-800 text-[11px] text-gray-500">
                You can easily hide this gray helper panel at any time by pressing the <strong class="text-gray-300">"Hide Guide"</strong> button in the top header.
            </div>
        </aside>

    </div>

    <!-- MAIN JAVASCRIPT: MANAGES THE STORIES & INTERACTION -->
    <script>
        // =========================================================================
        // 1. CONFIGURATION: EDIT YOUR BASIC INFORMATION BELOW
        // =========================================================================
        const CONFIG = {
            authorName: "ALIX FOEDISCH",
            subtitle: "Notes & Narrative Closet",
            introQuote: `"I collect pieces of scenes, characters left behind on stage, and alternative timelines. This is a public shelf of stories and unfinished ideas."`,
            year: new Date().getFullYear()
        };

        // =========================================================================
        // 2. DATA SOURCE: ADD, REMOVE, OR MODIFY YOUR JOURNAL STORIES HERE
        // =========================================================================
        let stories = [
            {
                id: 'story-1',
                title: 'The Weight of Quiet Railroads',
                category: 'Short Stories',
                excerpt: 'We met at a station where the trains only paused if someone waved a yellow flag. In the three minutes of stillness, we swapped pocketwatches.',
                content: `We met at a station where the trains only paused if someone waved a yellow flag. In the three minutes of stillness, we swapped pocketwatches. Mine kept perfect rhythm with my anxiety; hers had stopped entirely in 1994.\n\n"Why carry something that doesn't tell time?" I asked, watching the engine idle, puffing steam into the cold morning air.\n\n"It tells a very specific time," she said, tapping the glass. "It tells the exact minute my grandfather forgot where he was going. It’s a physical monument to a detour."\n\nWhen the whistle blew, I got on. She stayed on the platform. Sometimes, when my wrist ticks, I remember the absolute silence of those three minutes on the platform. The world wasn't waiting for us; it was just taking a deep breath.`,
                readTime: '3 min read',
                date: 'May 12, 2026',
                tags: ['Memory', 'Minimalism', 'Encounters']
            },
            {
                id: 'story-2',
                title: 'Anatomy of an Unwritten Novel',
                category: 'Fragments & Ideas',
                excerpt: 'Three sentences scribbled on a damp coaster. That is where all great tragedies begin before they are ruined by chapters.',
                content: `1. A lighthouse keeper who is profoundly afraid of the dark, yet more terrified of what the light reveals on the water.\n\n2. A city where names are currency. To speak a name is to spend it; thus, the wealthiest are completely silent and anonymous.\n\n3. The distinct feeling of grief for a house you only drove past once.`,
                readTime: '1 min read',
                date: 'April 28, 2026',
                tags: ['Concepts', 'Prompts']
            },
            {
                id: 'story-3',
                title: 'The Actor\'s Closet',
                category: 'Scribbles',
                excerpt: 'A closet full of clothes meant for people I am pretending to be. Yesterday, a 1920s detective. Today, an anxious bystander.',
                content: `There is a strange dislocation in looking at clothes that belong to a version of you that only existed for forty-five minutes under key lights. \n\nThe tweed jacket smells of theater dust and old hairspray. I wore it when I died on stage in Chicago. The yellow raincoat belongs to an extra who stood in fake rain for four hours without speaking a word. \n\nWe store these skins in cedar drawers, hoping the moths don't eat our alternative timelines first.`,
                readTime: '2 min read',
                date: 'March 15, 2026',
                tags: ['Identity', 'Reflections']
            }
        ];

        // =========================================================================
        // 3. ENGINE LOGIC (No need to edit this unless you want to change features!)
        // =========================================================================
        let activeCategory = "All";
        let activeStoryId = null;
        let activeTheme = "cream";
        let showSidebar = true;

        // Apply config to HTML Elements on Load
        document.getElementById('header-name').innerText = CONFIG.authorName;
        document.getElementById('header-subtitle').innerText = CONFIG.subtitle;
        document.getElementById('intro-text').innerText = CONFIG.introQuote;
        document.getElementById('footer-year').innerText = CONFIG.year;

        // Theme palette configurations
        const themeStyles = {
            cream: {
                bg: "bg-[#faf7f2] text-[#2c2621]",
                card: "bg-[#f4eee3] border-[#ebdcc8] hover:border-[#dfceba]",
                header: "border-[#ebdcc8]",
                mutedText: "text-[#706456]",
                badge: "bg-black bg-opacity-5 text-[#706456]",
                btnActive: "bg-[#2c2621] text-[#faf7f2]",
                btnInactive: "bg-[#f4eee3] text-[#706456] hover:bg-[#ebdcc8]"
            },
            dark: {
                bg: "bg-[#12100e] text-[#e8e3dc]",
                card: "bg-[#1c1815] border-[#2d2620] hover:border-[#42372e]",
                header: "border-[#2d2620]",
                mutedText: "text-[#a89e95]",
                badge: "bg-white bg-opacity-5 text-[#a89e95]",
                btnActive: "bg-[#e5c158] text-[#12100e]",
                btnInactive: "bg-[#1c1815] text-[#a89e95] hover:bg-[#2d2620]"
            },
            white: {
                bg: "bg-[#ffffff] text-[#1a1a1a]",
                card: "bg-[#fcfcfc] border-[#e5e5e5] hover:border-[#cccccc]",
                header: "border-[#e5e5e5]",
                mutedText: "text-[#666666]",
                badge: "bg-neutral-100 text-[#666666]",
                btnActive: "bg-[#1a1a1a] text-[#ffffff]",
                btnInactive: "bg-[#f4f4f4] text-[#666666] hover:bg-[#e8e8e8]"
            }
        };

        // Navigation Categories List
        const categories = ["All", "Short Stories", "Fragments & Ideas", "Scribbles"];

        function initApp() {
            renderCategoryTabs();
            renderContentFeed();
            applyTheme(activeTheme);
        }

        // Generate the navigation buttons
        function renderCategoryTabs() {
            const container = document.getElementById('categories-container');
            const theme = themeStyles[activeTheme];
            
            container.innerHTML = categories.map(cat => {
                const isActive = activeCategory === cat;
                const buttonClass = isActive ? theme.btnActive : theme.btnInactive;
                return `
                    <button onclick="setCategory('${cat}')" class="px-4 py-1.5 rounded-full text-xs font-mono transition-all duration-200 ${buttonClass}">
                        ${cat}
                    </button>
                `;
            }).join('');
        }

        function setCategory(cat) {
            activeCategory = cat;
            activeStoryId = null; // Exit story reader view
            renderCategoryTabs();
            renderContentFeed();
        }

        // Render feed or individual story focus view
        function renderContentFeed() {
            const displayArea = document.getElementById('content-display-area');
            const theme = themeStyles[activeTheme];

            // 1. Focus Reading View
            if (activeStoryId) {
                const story = stories.find(s => s.id === activeStoryId);
                if (story) {
                    displayArea.innerHTML = `
                        <div class="animate-fadeIn">
                            <!-- Back Button -->
                            <button onclick="closeStory()" class="mb-8 font-mono text-xs flex items-center gap-1.5 cursor-pointer opacity-70 hover:opacity-100">
                                <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path></svg>
                                <span>Back to the library</span>
                            </button>

                            <!-- Story Metadata Header -->
                            <div class="space-y-4 mb-8">
                                <div class="flex items-center gap-3 text-xs font-mono">
                                    <span class="px-2 py-0.5 rounded ${theme.badge}">${story.category}</span>
                                    <span class="${theme.mutedText}">${story.readTime}</span>
                                    <span class="${theme.mutedText}">•</span>
                                    <span class="${theme.mutedText}">${story.date}</span>
                                </div>
                                <h2 class="font-serif text-3xl md:text-5xl font-semibold leading-tight">${story.title}</h2>
                                <div class="flex flex-wrap gap-2 pt-1">
                                    ${story.tags.map(tag => `<span class="text-[11px] font-mono tracking-wider opacity-65">#${tag}</span>`).join('')}
                                </div>
                            </div>

                            <!-- Formatted Prose Content -->
                            <div class="font-serif text-lg md:text-xl leading-relaxed space-y-6 pt-8 border-t border-opacity-10 border-current whitespace-pre-line max-w-2xl">
                                ${story.content}
                            </div>
                        </div>
                    `;
                    // Scroll back to top smoothly when opening a story
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                    return;
                }
            }

            // 2. Filtered Post Feed Grid View
            const filtered = activeCategory === "All" 
                ? stories 
                : stories.filter(s => s.category === activeCategory);

            if (filtered.length === 0) {
                displayArea.innerHTML = `
                    <div class="py-12 text-center font-mono text-sm opacity-60">
                        No entries found in this category yet.
                    </div>
                `;
                return;
            }

            displayArea.innerHTML = `
                <div class="grid gap-8">
                    ${filtered.map(item => `
                        <div onclick="openStory('${item.id}')" class="p-6 rounded-xl border cursor-pointer group transform hover:scale-[1.005] transition-all duration-300 ${theme.card}">
                            <div class="flex justify-between items-start mb-3">
                                <span class="text-[10px] font-mono uppercase tracking-wider px-2 py-0.5 rounded ${theme.badge}">
                                    ${item.category}
                                </span>
                                <span class="text-xs font-mono ${theme.mutedText}">${item.readTime}</span>
                            </div>
                            <h3 class="font-serif text-xl md:text-2xl font-bold group-hover:underline decoration-1 underline-offset-4">
                                ${item.title}
                            </h3>
                            <p class="mt-2 text-sm leading-relaxed ${theme.mutedText} line-clamp-3">
                                ${item.excerpt}
                            </p>
                            <div class="mt-4 flex justify-between items-center pt-2">
                                <div class="flex gap-2">
                                    ${item.tags.map(tag => `<span class="text-[11px] font-mono ${theme.mutedText}">#${tag}</span>`).join('')}
                                </div>
                                <span class="text-xs font-mono flex items-center gap-1 opacity-0 group-hover:opacity-100 transition-opacity">
                                    Read Immersive 
                                    <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                                </span>
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
        }

        function openStory(id) {
            activeStoryId = id;
            renderContentFeed();
        }

        function closeStory() {
            activeStoryId = null;
            renderContentFeed();
        }

        // Change Theme Switch Logic
        function changeTheme(themeName) {
            activeTheme = themeName;
            applyTheme(themeName);
        }

        function applyTheme(themeName) {
            const body = document.getElementById('body-root');
            const mainHeader = document.getElementById('main-header');
            const mainFooter = document.getElementById('main-footer');
            const divider = document.getElementById('intro-divider');
            const subtitle = document.getElementById('header-subtitle');
            
            // Remove previous theme classes
            body.className = "font-sans antialiased overflow-x-hidden";
            
            const theme = themeStyles[themeName];
            
            // Apply new classes
            body.classList.add(`theme-${themeName}`);
            themeName === 'cream' ? body.classList.add('bg-[#faf7f2]', 'text-[#2c2621]') : null;
            themeName === 'dark' ? body.classList.add('bg-[#12100e]', 'text-[#e8e3dc]') : null;
            themeName === 'white' ? body.classList.add('bg-[#ffffff]', 'text-[#1a1a1a]') : null;

            mainHeader.className = `p-6 flex justify-between items-center border-b sticky top-0 backdrop-blur-md bg-opacity-90 z-20 ${theme.header}`;
            mainFooter.className = `p-8 text-center text-xs font-mono border-t ${theme.mutedText} ${theme.header}`;
            divider.className = `mb-12 pb-12 border-b border-dashed ${theme.header}`;
            subtitle.className = `text-xs font-mono uppercase tracking-widest ${theme.mutedText}`;

            // Reset theme switcher button highlights
            const creamBtn = document.getElementById('btn-theme-cream');
            const darkBtn = document.getElementById('btn-theme-dark');
            const whiteBtn = document.getElementById('btn-theme-white');

            creamBtn.className = "w-6 h-6 rounded-full bg-[#f4eee3] border-2 border-transparent";
            darkBtn.className = "w-6 h-6 rounded-full bg-[#1c1815] border-2 border-transparent";
            whiteBtn.className = "w-6 h-6 rounded-full bg-white border-2 border-transparent";

            if (themeName === 'cream') creamBtn.classList.add('border-amber-600', 'scale-110');
            if (themeName === 'dark') darkBtn.classList.add('border-amber-400', 'scale-110');
            if (themeName === 'white') whiteBtn.classList.add('border-blue-600', 'scale-110');

            // Apply specific class mappings onto customized layout nodes dynamically
            renderCategoryTabs();
            renderContentFeed();
        }

        // Toggle Sidebar Layout Visibility
        function toggleSidebar() {
            const sidebar = document.getElementById('curator-sidebar');
            const textSpan = document.getElementById('toggle-btn-text');
            showSidebar = !showSidebar;
            
            if (showSidebar) {
                sidebar.classList.remove('hidden');
                textSpan.innerText = "Hide Guide";
            } else {
                sidebar.classList.add('hidden');
                textSpan.innerText = "Show Guide";
            }
        }

        // Sandbox Form Injector Handler
        function handleSandboxSubmit(e) {
            e.preventDefault();
            
            const titleInput = document.getElementById('sb-title');
            const categoryInput = document.getElementById('sb-category');
            const tagsInput = document.getElementById('sb-tags');
            const contentInput = document.getElementById('sb-content');

            const contentText = contentInput.value;
            const wordCount = contentText.split(/\s+/).filter(Boolean).length;
            const computedReadTime = `${Math.max(1, Math.ceil(wordCount / 180))} min read`;

            const newStory = {
                id: `sandbox-${Date.now()}`,
                title: titleInput.value,
                category: categoryInput.value,
                excerpt: contentText.slice(0, 130) + '...',
                content: contentText,
                readTime: computedReadTime,
                date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' }),
                tags: tagsInput.value.split(',').map(t => t.trim()).filter(Boolean)
            };

            // Prepends live locally to our array
            stories = [newStory, ...stories];
            
            // Clear Sandbox Inputs
            titleInput.value = '';
            tagsInput.value = '';
            contentInput.value = '';

            // Update client feed display
            activeCategory = "All";
            renderCategoryTabs();
            renderContentFeed();

            // Auto focus on reading the newly-created item immediately
            openStory(newStory.id);
        }

        // Initialize App on DOM Content Loaded
        window.onload = function() {
            initApp();
        };
    </script>
</body>
</html>

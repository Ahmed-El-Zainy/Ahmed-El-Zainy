<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ahmed Mustafa Mohamed | Terminal Portfolio</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=VT323&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0a0e14;
            --bg-secondary: #0d1117;
            --text-primary: #00ff9f;
            --text-secondary: #7209b7;
            --text-accent: #9d4edd;
            --text-muted: #6b7280;
            --border-color: #560bad;
            --cursor-color: #00ff9f;
            --shadow-glow: 0 0 20px rgba(0, 255, 159, 0.3);
        }

        body {
            background: linear-gradient(135deg, #0a0e14 0%, #1a1f2e 100%);
            font-family: 'JetBrains Mono', monospace;
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated background particles */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: var(--text-primary);
            border-radius: 50%;
            opacity: 0.3;
            animation: float linear infinite;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) translateX(0);
                opacity: 0;
            }
            10% {
                opacity: 0.3;
            }
            90% {
                opacity: 0.3;
            }
            100% {
                transform: translateY(-100vh) translateX(100px);
                opacity: 0;
            }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        /* Terminal Header */
        .terminal-header {
            background: var(--bg-secondary);
            border: 2px solid var(--border-color);
            border-radius: 8px 8px 0 0;
            padding: 10px 15px;
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: var(--shadow-glow);
            animation: slideDown 0.5s ease-out;
        }

        @keyframes slideDown {
            from {
                transform: translateY(-50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .terminal-button {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }

        .terminal-button.red { background: #ff5f56; }
        .terminal-button.yellow { background: #ffbd2e; }
        .terminal-button.green { background: #27c93f; }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }

        .terminal-title {
            margin-left: auto;
            color: var(--text-accent);
            font-size: 14px;
            font-weight: 500;
        }

        /* Terminal Body */
        .terminal-body {
            background: var(--bg-primary);
            border: 2px solid var(--border-color);
            border-top: none;
            border-radius: 0 0 8px 8px;
            padding: 30px;
            min-height: 80vh;
            box-shadow: var(--shadow-glow);
            animation: fadeIn 0.8s ease-out 0.3s both;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ASCII Art */
        .ascii-art {
            font-family: 'VT323', monospace;
            font-size: 10px;
            line-height: 1;
            color: var(--text-secondary);
            white-space: pre;
            margin-bottom: 30px;
            overflow-x: auto;
            animation: glitchArt 3s ease-in-out infinite;
        }

        @keyframes glitchArt {
            0%, 100% { transform: translateX(0); }
            10% { transform: translateX(-2px); }
            20% { transform: translateX(2px); }
            30% { transform: translateX(0); }
        }

        /* Command Prompt */
        .prompt-line {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 20px;
            animation: slideInLeft 0.5s ease-out;
        }

        @keyframes slideInLeft {
            from {
                transform: translateX(-30px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .prompt-symbol {
            color: var(--text-secondary);
            font-weight: bold;
        }

        .prompt-path {
            color: var(--text-accent);
        }

        .prompt-arrow {
            color: var(--text-primary);
        }

        /* Typing Effect */
        .typed-text {
            color: var(--text-primary);
            position: relative;
        }

        .cursor {
            display: inline-block;
            width: 8px;
            height: 18px;
            background: var(--cursor-color);
            margin-left: 2px;
            animation: blink 1s step-end infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        /* Output Sections */
        .output-section {
            margin: 30px 0;
            opacity: 0;
            animation: fadeInUp 0.6s ease-out forwards;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section-title {
            color: var(--text-secondary);
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 15px;
            border-left: 4px solid var(--text-secondary);
            padding-left: 15px;
            animation: slideInRight 0.5s ease-out;
        }

        @keyframes slideInRight {
            from {
                transform: translateX(30px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        /* Info Cards */
        .info-card {
            background: rgba(125, 9, 183, 0.05);
            border-left: 3px solid var(--text-accent);
            padding: 15px 20px;
            margin: 10px 0;
            border-radius: 4px;
            transition: all 0.3s ease;
        }

        .info-card:hover {
            background: rgba(125, 9, 183, 0.1);
            transform: translateX(10px);
            box-shadow: 0 0 15px rgba(157, 78, 221, 0.3);
        }

        .info-label {
            color: var(--text-accent);
            font-weight: 700;
            margin-right: 10px;
        }

        .info-value {
            color: var(--text-primary);
        }

        /* Skills Grid */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .skill-item {
            background: linear-gradient(135deg, rgba(125, 9, 183, 0.1), rgba(0, 255, 159, 0.05));
            border: 1px solid var(--border-color);
            padding: 15px;
            border-radius: 6px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .skill-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 255, 159, 0.2), transparent);
            transition: left 0.5s ease;
        }

        .skill-item:hover::before {
            left: 100%;
        }

        .skill-item:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 10px 25px rgba(0, 255, 159, 0.3);
            border-color: var(--text-primary);
        }

        .skill-icon {
            font-size: 24px;
            margin-bottom: 8px;
            animation: bounce 2s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .skill-name {
            color: var(--text-primary);
            font-size: 14px;
            font-weight: 500;
        }

        /* Stats Display */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .stat-box {
            background: linear-gradient(135deg, var(--bg-secondary), var(--bg-primary));
            border: 2px solid var(--border-color);
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .stat-box::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 159, 0.1), transparent);
            animation: rotate 4s linear infinite;
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .stat-content {
            position: relative;
            z-index: 1;
        }

        .stat-number {
            font-size: 32px;
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 5px;
            font-family: 'VT323', monospace;
        }

        .stat-label {
            color: var(--text-accent);
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Command Input */
        .command-input-section {
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid var(--border-color);
        }

        .input-wrapper {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .command-input {
            flex: 1;
            background: var(--bg-secondary);
            border: 2px solid var(--border-color);
            color: var(--text-primary);
            padding: 12px 15px;
            border-radius: 6px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 14px;
            outline: none;
            transition: all 0.3s ease;
        }

        .command-input:focus {
            border-color: var(--text-primary);
            box-shadow: 0 0 15px rgba(0, 255, 159, 0.3);
        }

        /* Help Menu */
        .help-menu {
            background: rgba(125, 9, 183, 0.05);
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: 6px;
            margin: 20px 0;
        }

        .help-command {
            display: flex;
            margin: 10px 0;
            padding: 8px;
            border-radius: 4px;
            transition: background 0.2s ease;
        }

        .help-command:hover {
            background: rgba(0, 255, 159, 0.1);
        }

        .help-cmd {
            color: var(--text-secondary);
            font-weight: 700;
            min-width: 120px;
        }

        .help-desc {
            color: var(--text-muted);
        }

        /* Progress Bars */
        .progress-bar {
            width: 100%;
            height: 4px;
            background: var(--bg-secondary);
            border-radius: 2px;
            overflow: hidden;
            margin: 10px 0;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--text-secondary), var(--text-primary));
            border-radius: 2px;
            animation: fillProgress 2s ease-out forwards;
        }

        @keyframes fillProgress {
            from { width: 0; }
        }

        /* Loading Animation */
        .loading {
            display: inline-block;
            color: var(--text-primary);
        }

        .loading::after {
            content: '...';
            animation: loading 1.5s steps(4) infinite;
        }

        @keyframes loading {
            0% { content: '.'; }
            33% { content: '..'; }
            66% { content: '...'; }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .terminal-body {
                padding: 20px;
            }

            .ascii-art {
                font-size: 8px;
            }

            .skills-grid {
                grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            }

            .stats-container {
                grid-template-columns: 1fr;
            }
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
            height: 10px;
        }

        ::-webkit-scrollbar-track {
            background: var(--bg-primary);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--border-color);
            border-radius: 5px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--text-secondary);
        }

        .footer-text {
            text-align: center;
            color: var(--text-muted);
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid var(--border-color);
            font-size: 12px;
        }

        .link-hover {
            color: var(--text-primary);
            text-decoration: none;
            position: relative;
            transition: color 0.3s ease;
        }

        .link-hover:hover {
            color: var(--text-secondary);
        }

        .link-hover::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -2px;
            left: 0;
            background: var(--text-secondary);
            transition: width 0.3s ease;
        }

        .link-hover:hover::after {
            width: 100%;
        }
    </style>
</head>
<body>
    <!-- Background Particles -->
    <div class="particles" id="particles"></div>

    <div class="container">
        <!-- Terminal Header -->
        <div class="terminal-header">
            <div class="terminal-button red"></div>
            <div class="terminal-button yellow"></div>
            <div class="terminal-button green"></div>
            <div class="terminal-title">ahmed@shadow-terminal: ~</div>
        </div>

        <!-- Terminal Body -->
        <div class="terminal-body">
            <!-- ASCII Art Header -->
            <div class="ascii-art" id="asciiArt">
    _____ _               _                   _____           _           
   / ____| |             | |                 / ____|         | |          
  | (___ | |__   __ _  __| | _____      __ | |     ___   __| | ___ _ __ 
   \___ \| '_ \ / _` |/ _` |/ _ \ \ /\ / / | |    / _ \ / _` |/ _ \ '__|
   ____) | | | | (_| | (_| | (_) \ V  V /  | |___| (_) | (_| |  __/ |   
  |_____/|_| |_|\__,_|\__,_|\___/ \_/\_/    \_____\___/ \__,_|\___|_|   
                                                                          
  █████╗ ██╗  ██╗███╗   ███╗███████╗██████╗     ███╗   ███╗ ██████╗ ██╗  ██╗ █████╗ ███╗   ███╗███╗   ███╗███████╗██████╗ 
 ██╔══██╗██║  ██║████╗ ████║██╔════╝██╔══██╗    ████╗ ████║██╔═══██╗██║  ██║██╔══██╗████╗ ████║████╗ ████║██╔════╝██╔══██╗
 ███████║███████║██╔████╔██║█████╗  ██║  ██║    ██╔████╔██║██║   ██║███████║███████║██╔████╔██║██╔████╔██║█████╗  ██║  ██║
 ██╔══██║██╔══██║██║╚██╔╝██║██╔══╝  ██║  ██║    ██║╚██╔╝██║██║   ██║██╔══██║██╔══██║██║╚██╔╝██║██║╚██╔╝██║██╔══╝  ██║  ██║
 ██║  ██║██║  ██║██║ ╚═╝ ██║███████╗██████╔╝    ██║ ╚═╝ ██║╚██████╔╝██║  ██║██║  ██║██║ ╚═╝ ██║██║ ╚═╝ ██║███████╗██████╔╝
 ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝╚═════╝     ╚═╝     ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝     ╚═╝╚══════╝╚═════╝ 
            </div>

            <!-- Welcome Message -->
            <div class="prompt-line">
                <span class="prompt-symbol">┌──(</span>
                <span class="prompt-path">shadow@void</span>
                <span class="prompt-symbol">)-[</span>
                <span class="prompt-path">~</span>
                <span class="prompt-symbol">]</span>
            </div>
            <div class="prompt-line">
                <span class="prompt-symbol">└─</span>
                <span class="prompt-arrow">$</span>
                <span class="typed-text" id="welcomeText"></span>
                <span class="cursor"></span>
            </div>

            <!-- Main Content -->
            <div id="mainContent"></div>

            <!-- Command Input -->
            <div class="command-input-section">
                <div class="prompt-line">
                    <span class="prompt-symbol">└─</span>
                    <span class="prompt-arrow">$</span>
                    <input type="text" class="command-input" id="commandInput" placeholder="Type 'help' for available commands..." autocomplete="off">
                </div>
            </div>

            <!-- Footer -->
            <div class="footer-text">
                <p>🌙 Crafted in the shadows with precision | Always coding in darkness 🌙</p>
                <p style="margin-top: 10px;">Press <kbd style="background: var(--bg-secondary); padding: 2px 6px; border-radius: 3px; border: 1px solid var(--border-color);">Tab</kbd> for autocomplete | <kbd style="background: var(--bg-secondary); padding: 2px 6px; border-radius: 3px; border: 1px solid var(--border-color);">↑/↓</kbd> for command history</p>
            </div>
        </div>
    </div>

    <script>
        // Create particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDuration = (Math.random() * 10 + 5) + 's';
                particle.style.animationDelay = Math.random() * 5 + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Typewriter effect
        function typeWriter(element, text, speed = 50) {
            return new Promise((resolve) => {
                let i = 0;
                const cursor = element.nextElementSibling;
                
                function type() {
                    if (i < text.length) {
                        element.textContent += text.charAt(i);
                        i++;
                        setTimeout(type, speed);
                    } else {
                        resolve();
                    }
                }
                type();
            });
        }

        // Portfolio data
        const portfolioData = {
            about: {
                name: "Ahmed Mustafa Mohamed",
                role: "AI Researcher & Digital Phantom",
                location: "The Void Between 0s and 1s",
                mindset: "Embrace the chaos, create from darkness",
                obsession: {
                    building: "🧠 Large Language Models that think in shadows",
                    exploring: "🔮 The depths of Reinforcement Learning",
                    philosophy: "AI should hallucinate beautifully and intelligently"
                }
            },
            skills: {
                languages: [
                    { name: "Python", icon: "🐍", level: 95 },
                    { name: "C++", icon: "⚙️", level: 85 },
                    { name: "JavaScript", icon: "📜", level: 90 },
                    { name: "R", icon: "📊", level: 75 },
                    { name: "PHP", icon: "🐘", level: 70 }
                ],
                ai_ml: [
                    { name: "PyTorch", icon: "🔥", level: 95 },
                    { name: "TensorFlow", icon: "🧮", level: 90 },
                    { name: "Hugging Face", icon: "🤗", level: 92 },
                    { name: "OpenAI", icon: "🤖", level: 88 },
                    { name: "LangChain", icon: "🦜", level: 85 },
                    { name: "W&B", icon: "📈", level: 80 }
                ],
                databases: [
                    { name: "MongoDB", icon: "🍃", level: 88 },
                    { name: "PostgreSQL", icon: "🐘", level: 85 },
                    { name: "Pinecone", icon: "🌲", level: 80 },
                    { name: "Qdrant", icon: "⚡", level: 78 }
                ],
                cloud: [
                    { name: "AWS", icon: "☁️", level: 85 },
                    { name: "Azure", icon: "🌩️", level: 80 },
                    { name: "GCP", icon: "🌥️", level: 75 }
                ],
                devops: [
                    { name: "Docker", icon: "🐳", level: 90 },
                    { name: "GitHub Actions", icon: "⚡", level: 85 },
                    { name: "Git", icon: "🔧", level: 95 }
                ]
            },
            stats: {
                projects: 47,
                contributions: 1337,
                languages: 8,
                experience: "3+ Years"
            }
        };

        // Command history
        let commandHistory = [];
        let historyIndex = -1;

        // Commands
        const commands = {
            help: () => {
                return `
<div class="help-menu">
    <h3 style="color: var(--text-secondary); margin-bottom: 15px;">📚 Available Commands:</h3>
    <div class="help-command">
        <span class="help-cmd">about</span>
        <span class="help-desc">Display information about me</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">skills</span>
        <span class="help-desc">Show my technical arsenal</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">stats</span>
        <span class="help-desc">Display GitHub statistics</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">projects</span>
        <span class="help-desc">View my projects and contributions</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">contact</span>
        <span class="help-desc">Get in touch with me</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">clear</span>
        <span class="help-desc">Clear the terminal</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">matrix</span>
        <span class="help-desc">Enter the Matrix...</span>
    </div>
    <div class="help-command">
        <span class="help-cmd">hack</span>
        <span class="help-desc">Initiate hacking sequence 👾</span>
    </div>
</div>`;
            },

            about: () => {
                const data = portfolioData.about;
                return `
<div class="output-section">
    <h2 class="section-title">🕷️ About This Shadow Entity</h2>
    <div class="info-card">
        <span class="info-label">Name:</span>
        <span class="info-value">${data.name}</span>
    </div>
    <div class="info-card">
        <span class="info-label">Role:</span>
        <span class="info-value">${data.role}</span>
    </div>
    <div class="info-card">
        <span class="info-label">Location:</span>
        <span class="info-value">${data.location}</span>
    </div>
    <div class="info-card">
        <span class="info-label">Mindset:</span>
        <span class="info-value">${data.mindset}</span>
    </div>
    <div style="margin-top: 20px;">
        <h3 style="color: var(--text-accent); margin-bottom: 10px;">🎯 Current Obsession:</h3>
        <div class="info-card">
            <span class="info-label">Building:</span>
            <span class="info-value">${data.obsession.building}</span>
        </div>
        <div class="info-card">
            <span class="info-label">Exploring:</span>
            <span class="info-value">${data.obsession.exploring}</span>
        </div>
        <div class="info-card">
            <span class="info-label">Philosophy:</span>
            <span class="info-value">${data.obsession.philosophy}</span>
        </div>
    </div>
</div>`;
            },

            skills: () => {
                const skills = portfolioData.skills;
                let html = '<div class="output-section"><h2 class="section-title">⚡ Arsenal of Darkness</h2>';
                
                const categories = [
                    { title: '🐍 Core Languages', data: skills.languages },
                    { title: '🧠 AI/ML Sorcery', data: skills.ai_ml },
                    { title: '🗄️ Data Realms', data: skills.databases },
                    { title: '☁️ Cloud Dominion', data: skills.cloud },
                    { title: '🔧 DevOps Magic', data: skills.devops }
                ];

                categories.forEach(category => {
                    html += `
                    <div style="margin: 30px 0;">
                        <h3 style="color: var(--text-accent); margin-bottom: 15px;">${category.title}</h3>
                        <div class="skills-grid">`;
                    
                    category.data.forEach(skill => {
                        html += `
                        <div class="skill-item">
                            <div class="skill-icon">${skill.icon}</div>
                            <div class="skill-name">${skill.name}</div>
                            <div class="progress-bar" style="margin-top: 10px;">
                                <div class="progress-fill" style="width: ${skill.level}%"></div>
                            </div>
                            <div style="color: var(--text-muted); font-size: 11px; margin-top: 5px;">${skill.level}%</div>
                        </div>`;
                    });
                    
                    html += `</div></div>`;
                });

                html += '</div>';
                return html;
            },

            stats: () => {
                const stats = portfolioData.stats;
                return `
<div class="output-section">
    <h2 class="section-title">📊 Shadow Statistics</h2>
    <div class="stats-container">
        <div class="stat-box">
            <div class="stat-content">
                <div class="stat-number">${stats.projects}</div>
                <div class="stat-label">Projects</div>
            </div>
        </div>
        <div class="stat-box">
            <div class="stat-content">
                <div class="stat-number">${stats.contributions}</div>
                <div class="stat-label">Contributions</div>
            </div>
        </div>
        <div class="stat-box">
            <div class="stat-content">
                <div class="stat-number">${stats.languages}</div>
                <div class="stat-label">Languages</div>
            </div>
        </div>
        <div class="stat-box">
            <div class="stat-content">
                <div class="stat-number">${stats.experience}</div>
                <div class="stat-label">Experience</div>
            </div>
        </div>
    </div>
</div>`;
            },

            projects: () => {
                return `
<div class="output-section">
    <h2 class="section-title">🚀 Recent Projects</h2>
    <div class="info-card">
        <span class="info-label">🧠 LLM Shadow Engine</span><br>
        <span class="info-value" style="font-size: 12px; color: var(--text-muted);">
            Advanced language model fine-tuning framework with RLHF capabilities
        </span>
    </div>
    <div class="info-card">
        <span class="info-label">🎮 RL Game Master</span><br>
        <span class="info-value" style="font-size: 12px; color: var(--text-muted);">
            Deep reinforcement learning agents that master complex environments
        </span>
    </div>
    <div class="info-card">
        <span class="info-label">🔮 Neural Architect</span><br>
        <span class="info-value" style="font-size: 12px; color: var(--text-muted);">
            Automated neural architecture search for optimization
        </span>
    </div>
    <div class="info-card">
        <span class="info-label">🌐 Vector DB Explorer</span><br>
        <span class="info-value" style="font-size: 12px; color: var(--text-muted);">
            High-performance semantic search with vector databases
        </span>
    </div>
    <p style="margin-top: 20px; color: var(--text-muted);">
        💡 For more projects, check out my GitHub profile
    </p>
</div>`;
            },

            contact: () => {
                return `
<div class="output-section">
    <h2 class="section-title">🔮 Connect with the Shadows</h2>
    <div class="info-card">
        <span class="info-label">GitHub:</span>
        <span class="info-value"><a href="https://github.com/Ahmed-El-Zainy" class="link-hover" target="_blank">@Ahmed-El-Zainy</a></span>
    </div>
    <div class="info-card">
        <span class="info-label">Email:</span>
        <span class="info-value">ahmed.shadow@void.dev</span>
    </div>
    <div class="info-card">
        <span class="info-label">LinkedIn:</span>
        <span class="info-value"><a href="#" class="link-hover" target="_blank">Ahmed Mustafa Mohamed</a></span>
    </div>
    <div class="info-card">
        <span class="info-label">Twitter:</span>
        <span class="info-value"><a href="#" class="link-hover" target="_blank">@shadow_coder</a></span>
    </div>
    <p style="margin-top: 20px; color: var(--text-accent);">
        💬 Ready to collaborate in the darkness? Let's build something extraordinary!
    </p>
</div>`;
            },

            clear: () => {
                document.getElementById('mainContent').innerHTML = '';
                return '';
            },

            matrix: () => {
                let output = '<div class="output-section" style="font-family: VT323, monospace; color: var(--text-primary);">';
                const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
                for (let i = 0; i < 20; i++) {
                    let line = '';
                    for (let j = 0; j < 80; j++) {
                        line += chars[Math.floor(Math.random() * chars.length)];
                    }
                    output += line + '<br>';
                }
                output += '</div>';
                return output;
            },

            hack: () => {
                return `
<div class="output-section">
    <p style="color: var(--text-primary);">[<span class="loading">Initializing hacking sequence</span>]</p>
    <p style="margin-top: 10px; color: var(--text-secondary);">▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ 100%</p>
    <p style="margin-top: 15px; color: var(--text-primary);">
        [✓] Bypassing firewall...<br>
        [✓] Accessing mainframe...<br>
        [✓] Decrypting database...<br>
        [✓] Extracting data...<br>
        [✓] Covering tracks...<br>
        <br>
        <span style="color: var(--text-secondary); font-weight: bold;">ACCESS GRANTED</span><br>
        <span style="color: var(--text-muted); font-size: 12px;">Just kidding! I'm an ethical AI researcher 😉</span>
    </p>
</div>`;
            }
        };

        // Handle command input
        function handleCommand(cmd) {
            const command = cmd.trim().toLowerCase();
            commandHistory.unshift(command);
            historyIndex = -1;

            if (commands[command]) {
                const output = commands[command]();
                if (output) {
                    const mainContent = document.getElementById('mainContent');
                    const outputDiv = document.createElement('div');
                    outputDiv.innerHTML = output;
                    mainContent.appendChild(outputDiv);
                    
                    // Scroll to bottom
                    setTimeout(() => {
                        window.scrollTo({
                            top: document.body.scrollHeight,
                            behavior: 'smooth'
                        });
                    }, 100);
                }
            } else if (command) {
                const mainContent = document.getElementById('mainContent');
                const errorDiv = document.createElement('div');
                errorDiv.className = 'output-section';
                errorDiv.innerHTML = `<p style="color: #ff5f56;">Command not found: ${command}</p><p style="color: var(--text-muted); margin-top: 10px;">Type 'help' for available commands.</p>`;
                mainContent.appendChild(errorDiv);
            }
        }

        // Initialize
        async function init() {
            createParticles();
            
            const welcomeText = document.getElementById('welcomeText');
            await typeWriter(welcomeText, 'cat welcome.txt', 30);
            
            setTimeout(() => {
                document.getElementById('mainContent').innerHTML = commands.help();
                
                // Add animation delays
                const sections = document.querySelectorAll('.output-section');
                sections.forEach((section, index) => {
                    section.style.animationDelay = `${index * 0.1}s`;
                });
            }, 500);

            // Command input listener
            const commandInput = document.getElementById('commandInput');
            commandInput.addEventListener('keydown', (e) => {
                if (e.key === 'Enter') {
                    handleCommand(e.target.value);
                    e.target.value = '';
                } else if (e.key === 'ArrowUp') {
                    e.preventDefault();
                    if (historyIndex < commandHistory.length - 1) {
                        historyIndex++;
                        e.target.value = commandHistory[historyIndex];
                    }
                } else if (e.key === 'ArrowDown') {
                    e.preventDefault();
                    if (historyIndex > 0) {
                        historyIndex--;
                        e.target.value = commandHistory[historyIndex];
                    } else {
                        historyIndex = -1;
                        e.target.value = '';
                    }
                } else if (e.key === 'Tab') {
                    e.preventDefault();
                    const value = e.target.value.toLowerCase();
                    const matchingCommands = Object.keys(commands).filter(cmd => 
                        cmd.startsWith(value)
                    );
                    if (matchingCommands.length === 1) {
                        e.target.value = matchingCommands[0];
                    }
                }
            });

            // Auto-focus on command input
            commandInput.focus();
            document.addEventListener('click', () => commandInput.focus());
        }

        // Start
        init();
    </script>
</body>
</html>

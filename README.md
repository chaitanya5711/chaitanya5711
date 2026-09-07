<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chaitanya Jadhav - Data Analyst & AI Engineer</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #0891b2;
            --primary-dark: #0e7490;
            --secondary: #6366f1;
            --accent: #ec4899;
            --dark: #0f172a;
            --dark-lighter: #1e293b;
            --text: #e2e8f0;
            --text-muted: #94a3b8;
            --border: #334155;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, var(--dark) 0%, #1a1f35 50%, var(--dark) 100%);
            color: var(--text);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Animated background */
        .bg-gradient {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 50%, rgba(8, 145, 178, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(99, 102, 241, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(236, 72, 153, 0.05) 0%, transparent 50%);
            pointer-events: none;
            z-index: -1;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border);
            z-index: 1000;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .nav-logo {
            font-size: 1.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 0.9rem;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        /* Hero Section */
        .hero {
            margin-top: 80px;
            min-height: calc(100vh - 80px);
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 2rem;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 30% 30%, rgba(8, 145, 178, 0.15) 0%, transparent 60%),
                radial-gradient(circle at 70% 70%, rgba(99, 102, 241, 0.15) 0%, transparent 60%);
            z-index: -1;
        }

        .hero-content {
            max-width: 800px;
            animation: slideInUp 1s ease-out;
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: 4rem;
            font-weight: 800;
            margin-bottom: 1rem;
            line-height: 1.2;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 50%, var(--accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-subtitle {
            font-size: 1.3rem;
            color: var(--text-muted);
            margin-bottom: 2rem;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            margin-top: 2rem;
            flex-wrap: wrap;
        }

        .btn {
            padding: 0.75rem 2rem;
            border: none;
            border-radius: 0.5rem;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(8, 145, 178, 0.3);
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .btn-secondary:hover {
            background: rgba(8, 145, 178, 0.1);
        }

        /* Skills Section */
        .section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 3rem;
            text-align: center;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .skill-card {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.8) 0%, rgba(30, 41, 59, 0.8) 100%);
            border: 1px solid var(--border);
            padding: 2rem;
            border-radius: 0.75rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }

        .skill-card:hover {
            border-color: var(--primary);
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(8, 145, 178, 0.2);
        }

        .skill-category {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .skill-items {
            display: flex;
            flex-wrap: wrap;
            gap: 0.75rem;
        }

        .skill-badge {
            background: rgba(8, 145, 178, 0.2);
            color: var(--primary);
            padding: 0.5rem 1rem;
            border-radius: 0.35rem;
            font-size: 0.85rem;
            border: 1px solid rgba(8, 145, 178, 0.3);
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .project-card {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.8) 0%, rgba(30, 41, 59, 0.8) 100%);
            border: 1px solid var(--border);
            border-radius: 0.75rem;
            overflow: hidden;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .project-card:hover {
            border-color: var(--primary);
            transform: translateY(-8px);
            box-shadow: 0 25px 50px -12px rgba(8, 145, 178, 0.2);
        }

        .project-header {
            background: linear-gradient(135deg, rgba(8, 145, 178, 0.2) 0%, rgba(99, 102, 241, 0.2) 100%);
            padding: 1.5rem;
            border-bottom: 1px solid var(--border);
        }

        .project-icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }

        .project-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--text);
            margin-bottom: 0.5rem;
        }

        .project-tech {
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        .project-body {
            padding: 1.5rem;
        }

        .project-description {
            color: var(--text-muted);
            margin-bottom: 1rem;
            font-size: 0.95rem;
        }

        .project-features {
            list-style: none;
            margin: 1rem 0;
        }

        .project-features li {
            color: var(--text-muted);
            padding: 0.3rem 0;
            font-size: 0.9rem;
        }

        .project-features li::before {
            content: '✓ ';
            color: var(--primary);
            font-weight: 700;
            margin-right: 0.5rem;
        }

        .project-link {
            display: inline-block;
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            margin-top: 1rem;
            transition: all 0.3s ease;
        }

        .project-link:hover {
            gap: 0.5rem;
        }

        .project-link::after {
            content: ' →';
            transition: all 0.3s ease;
        }

        .project-link:hover::after {
            margin-left: 0.5rem;
        }

        /* Experience Section */
        .experience-item {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.8) 0%, rgba(30, 41, 59, 0.8) 100%);
            border: 1px solid var(--border);
            border-left: 3px solid var(--primary);
            padding: 2rem;
            margin-bottom: 2rem;
            border-radius: 0.5rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }

        .experience-item:hover {
            border-left-color: var(--secondary);
            transform: translateX(5px);
        }

        .experience-role {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .experience-company {
            color: var(--text-muted);
            margin-bottom: 1rem;
            font-size: 1rem;
        }

        .experience-details {
            list-style: none;
        }

        .experience-details li {
            color: var(--text-muted);
            padding: 0.3rem 0;
            padding-left: 1.5rem;
            position: relative;
        }

        .experience-details li::before {
            content: '→';
            position: absolute;
            left: 0;
            color: var(--primary);
            font-weight: 700;
        }

        /* Stats Section */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(8, 145, 178, 0.15) 0%, rgba(99, 102, 241, 0.15) 100%);
            border: 1px solid rgba(8, 145, 178, 0.3);
            padding: 2rem;
            text-align: center;
            border-radius: 0.75rem;
            backdrop-filter: blur(10px);
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: var(--text-muted);
            font-size: 0.95rem;
        }

        /* Footer */
        footer {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.95) 0%, rgba(30, 41, 59, 0.95) 100%);
            border-top: 1px solid var(--border);
            padding: 3rem 2rem;
            text-align: center;
            margin-top: 4rem;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .footer-links a {
            color: var(--text-muted);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: var(--primary);
        }

        .footer-divider {
            height: 1px;
            background: var(--border);
            margin: 2rem 0;
        }

        .footer-text {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-subtitle {
                font-size: 1.1rem;
            }

            .section {
                padding: 3rem 1.5rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .nav-links {
                gap: 1rem;
                font-size: 0.8rem;
            }

            .stat-value {
                font-size: 2rem;
            }
        }

        /* Animations */
        @keyframes glow {
            0%, 100% {
                box-shadow: 0 0 20px rgba(8, 145, 178, 0.3);
            }
            50% {
                box-shadow: 0 0 30px rgba(8, 145, 178, 0.5);
            }
        }

        .btn-primary {
            animation: glow 3s ease-in-out infinite;
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--dark);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--primary);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--secondary);
        }
    </style>
</head>
<body>
    <div class="bg-gradient"></div>

    <nav>
        <div class="nav-logo">CHAITANYA</div>
        <ul class="nav-links">
            <li><a href="#skills">Skills</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#experience">Experience</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <section class="hero">
        <div class="hero-content">
            <h1>Chaitanya Jadhav</h1>
            <p class="hero-subtitle">Data Analyst | AI/ML Enthusiast | Generative AI Engineer</p>
            <p class="hero-subtitle" style="font-size: 1.1rem; color: var(--text-muted); margin-bottom: 2rem;">
                Transforming data into intelligent decisions. Building AI-powered solutions that solve real problems.
            </p>
            <div class="cta-buttons">
                <a href="#projects" class="btn btn-primary">Explore Projects</a>
                <a href="https://github.com/chaitanya5711" class="btn btn-secondary">View GitHub</a>
            </div>
        </div>
    </section>

    <section id="skills" class="section">
        <h2 class="section-title">🛠️ Technical Arsenal</h2>
        
        <div class="skills-grid">
            <div class="skill-card">
                <div class="skill-category">📊 Data Analytics</div>
                <div class="skill-items">
                    <span class="skill-badge">Python</span>
                    <span class="skill-badge">SQL</span>
                    <span class="skill-badge">Pandas</span>
                    <span class="skill-badge">MySQL</span>
                    <span class="skill-badge">SQLite</span>
                </div>
            </div>

            <div class="skill-card">
                <div class="skill-category">📈 BI & Visualization</div>
                <div class="skill-items">
                    <span class="skill-badge">Power BI</span>
                    <span class="skill-badge">Plotly</span>
                    <span class="skill-badge">Matplotlib</span>
                    <span class="skill-badge">Seaborn</span>
                    <span class="skill-badge">Excel</span>
                </div>
            </div>

            <div class="skill-card">
                <div class="skill-category">🤖 AI & Machine Learning</div>
                <div class="skill-items">
                    <span class="skill-badge">Generative AI</span>
                    <span class="skill-badge">LLMs</span>
                    <span class="skill-badge">LangChain</span>
                    <span class="skill-badge">ChromaDB</span>
                    <span class="skill-badge">RAG</span>
                </div>
            </div>

            <div class="skill-card">
                <div class="skill-category">⚙️ Development</div>
                <div class="skill-items">
                    <span class="skill-badge">Streamlit</span>
                    <span class="skill-badge">n8n</span>
                    <span class="skill-badge">Git</span>
                    <span class="skill-badge">GitHub</span>
                    <span class="skill-badge">Python</span>
                </div>
            </div>
        </div>
    </section>

    <section id="projects" class="section">
        <h2 class="section-title">🌟 Featured Projects</h2>
        
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🧠</div>
                    <div class="project-title">AI-Powered Business Analytics</div>
                    <div class="project-tech">Python • Streamlit • Gemini AI • SQL</div>
                </div>
                <div class="project-body">
                    <p class="project-description">
                        End-to-end intelligent analytics platform transforming sales data into actionable insights.
                    </p>
                    <ul class="project-features">
                        <li>Interactive BI Dashboard</li>
                        <li>SQL Analytics Engine</li>
                        <li>AI-Powered Insights</li>
                        <li>Anomaly Detection</li>
                    </ul>
                    <a href="https://github.com/chaitanya5711/AI-Powered-Business-Analytics-Decision-Support-Dashboard" class="project-link">View Project</a>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🛒</div>
                    <div class="project-title">E-Commerce Sales Analysis</div>
                    <div class="project-tech">Python • MySQL • Power BI • Data Analysis</div>
                </div>
                <div class="project-body">
                    <p class="project-description">
                        Comprehensive analysis of 100K+ e-commerce transactions revealing business patterns.
                    </p>
                    <ul class="project-features">
                        <li>Sales & Revenue Analysis</li>
                        <li>Customer Segmentation</li>
                        <li>Product Performance</li>
                        <li>Power BI Dashboards</li>
                    </ul>
                    <a href="https://github.com/chaitanya5711/brazilian-ecommerce-sales-analysis" class="project-link">View Project</a>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🤖</div>
                    <div class="project-title">AI Cold Email Generator</div>
                    <div class="project-tech">LangChain • ChromaDB • Groq • Streamlit</div>
                </div>
                <div class="project-body">
                    <p class="project-description">
                        AI system generating personalized cold emails by matching jobs with portfolio projects.
                    </p>
                    <ul class="project-features">
                        <li>Job Requirement Extraction</li>
                        <li>Resume-to-Job Matching</li>
                        <li>Semantic Search (RAG)</li>
                        <li>Email Generation</li>
                    </ul>
                    <a href="https://github.com/chaitanya5711/AI-Cold-Email-Generator" class="project-link">View Project</a>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🏥</div>
                    <div class="project-title">Healthcare AI Platform</div>
                    <div class="project-tech">Generative AI • Groq • Streamlit • OpenStreetMap</div>
                </div>
                <div class="project-body">
                    <p class="project-description">
                        Healthcare assistant combining medical intelligence with facility discovery.
                    </p>
                    <ul class="project-features">
                        <li>Medical Report Analysis</li>
                        <li>Symptom Assessment</li>
                        <li>Facility Locator</li>
                        <li>AI Health Assistant</li>
                    </ul>
                    <a href="https://github.com/chaitanya5711/AI-Powered-Healthcare-Intelligence-Clinical-Decision-Suppport-Platform" class="project-link">View Project</a>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🍽️</div>
                    <div class="project-title">AI Restaurant Assistant</div>
                    <div class="project-tech">LLMs • Prompt Engineering • Streamlit</div>
                </div>
                <div class="project-body">
                    <p class="project-description">
                        Conversational AI assistant for natural restaurant-related interactions.
                    </p>
                    <ul class="project-features">
                        <li>NLP Understanding</li>
                        <li>Multi-turn Conversations</li>
                        <li>Prompt Optimization</li>
                        <li>LLM Integration</li>
                    </ul>
                    <a href="https://github.com/chaitanya5711/AI-Restaurant-Assistant-Python-LLMs-Prompt-Engineering-Streamlit" class="project-link">View Project</a>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">⚙️</div>
                    <div class="project-title">Restaurant Automation Workflow</div>
                    <div class="project-tech">n8n • AI Agents • WhatsApp API</div>
                </div>
                <div class="project-body">
                    <p class="project-description">
                        Intelligent automation system handling orders and reservations via AI.
                    </p>
                    <ul class="project-features">
                        <li>Intent Detection</li>
                        <li>Order Processing</li>
                        <li>Reservation Handling</li>
                        <li>API Integration</li>
                    </ul>
                    <a href="https://github.com/chaitanya5711" class="project-link">View Project</a>
                </div>
            </div>
        </div>
    </section>

    <section id="experience" class="section">
        <h2 class="section-title">💼 Professional Experience</h2>
        
        <div class="experience-item">
            <div class="experience-role">Data Analytics Intern</div>
            <div class="experience-company">Maestro Intellect • 6 Months</div>
            <ul class="experience-details">
                <li>Data analysis and reporting with SQL & Python</li>
                <li>Power BI dashboard development</li>
                <li>Data cleaning and ETL pipelines</li>
                <li>Business intelligence and insights extraction</li>
                <li>Excel and data visualization</li>
            </ul>
        </div>

        <div class="experience-item">
            <div class="experience-role">Technical Learner</div>
            <div class="experience-company">Self-Driven Development & Projects</div>
            <ul class="experience-details">
                <li>Built 7+ full-stack data and AI projects</li>
                <li>Mastered Python, SQL, and Power BI</li>
                <li>Explored Generative AI and LLM applications</li>
                <li>Developed end-to-end analytics solutions</li>
                <li>Contributing to open-source data projects</li>
            </ul>
        </div>
    </section>

    <section class="section">
        <h2 class="section-title">📊 By The Numbers</h2>
        
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-value">7+</div>
                <div class="stat-label">Projects Completed</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">100K+</div>
                <div class="stat-label">Data Records Analyzed</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">10+</div>
                <div class="stat-label">Technologies Mastered</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">2025</div>
                <div class="stat-label">Graduation Year (B.E.)</div>
            </div>
        </div>
    </section>

    <footer id="contact">
        <div class="footer-content">
            <h2 class="section-title" style="margin-bottom: 2rem;">Let's Connect</h2>
            
            <div class="footer-links">
                <a href="https://github.com/chaitanya5711" target="_blank">GitHub</a>
                <a href="https://www.linkedin.com/in/chaitanya-jadhav-369344259/" target="_blank">LinkedIn</a>
                <a href="mailto:jadhavchaitanya5911@gmail.com">Email</a>
            </div>

            <div class="footer-divider"></div>

            <p class="footer-text">
                💙 Made with Data. 🤖 Crafted with AI. 🔧 Built with Code.
            </p>
            <p class="footer-text" style="margin-top: 1rem;">
                © 2025 Chaitanya Jadhav. Exploring the intersection of data, AI, and impact.
            </p>
        </div>
    </footer>

    <script>
        // Smooth scroll behavior
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });

        // Add animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'slideInUp 0.6s ease-out forwards';
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.project-card, .skill-card, .experience-item').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>
</html>

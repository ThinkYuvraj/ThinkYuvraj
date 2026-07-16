
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yuvraj Singh | Portfolio</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;700&display=swap');

        :root {
            --bg: #050505;
            --primary: #00ff41;
            --secondary: #00d1ff;
            --accent: #ff6b35;
            --muted: #888;
            --glass: rgba(0, 255, 65, 0.04);
            --border: rgba(0, 255, 65, 0.2);
            --border-dim: rgba(0, 255, 65, 0.08);
            --terminal-header: #111;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; cursor: crosshair; }

        html { scroll-behavior: smooth; }

        body {
            background: var(--bg);
            color: var(--primary);
            font-family: 'Fira Code', monospace;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* CRT scanline overlay */
        body::before {
            content: "";
            position: fixed;
            inset: 0;
            background: linear-gradient(rgba(0,0,0,0) 50%, rgba(0,0,0,0.08) 50%),
                        linear-gradient(90deg, rgba(255,0,0,0.02), rgba(0,255,0,0.01), rgba(0,0,255,0.02));
            background-size: 100% 3px, 3px 100%;
            pointer-events: none;
            z-index: 9999;
        }

        /* ── LAYOUT ── */
        .shell {
            max-width: 1100px;
            margin: 20px auto;
            border: 1px solid var(--border);
            box-shadow: 0 0 40px rgba(0,255,65,0.08);
        }

        /* ── TITLE BAR ── */
        .titlebar {
            background: var(--terminal-header);
            padding: 10px 16px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .dots { display: flex; gap: 7px; }
        .dot { width: 12px; height: 12px; border-radius: 50%; }
        .dot.r { background: #ff5f56; }
        .dot.y { background: #ffbd2e; }
        .dot.g { background: #27c93f; }

        .titlebar-path { font-size: 11px; color: var(--muted); letter-spacing: 0.08em; }

        .nav-links { display: flex; gap: 18px; }
        .nav-links a {
            font-size: 11px;
            color: var(--muted);
            text-decoration: none;
            text-transform: uppercase;
            letter-spacing: 0.06em;
            transition: color 0.2s;
        }
        .nav-links a:hover { color: var(--primary); }

        /* ── HERO ── */
        header {
            padding: 60px 40px 50px;
            text-align: center;
            border-bottom: 1px solid var(--border);
            background: radial-gradient(ellipse at center, rgba(0,255,65,0.04) 0%, transparent 70%);
        }

        .glitch {
            font-size: clamp(2rem, 5vw, 3.4rem);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.08em;
            animation: glitch 2.5s infinite;
        }

        @keyframes glitch {
            0%, 90%, 100% { text-shadow: 0.05em 0 0 rgba(255,0,0,.6), -0.03em -0.04em 0 rgba(0,255,0,.6), 0.03em 0.04em 0 rgba(0,0,255,.6); }
            91% { text-shadow: -0.05em -0.02em 0 rgba(255,0,0,.6), 0.02em 0.02em 0 rgba(0,255,0,.6), -0.04em -0.04em 0 rgba(0,0,255,.6); }
            95% { text-shadow: 0.04em 0.03em 0 rgba(255,0,0,.6), -0.04em 0 0 rgba(0,255,0,.6), 0 -0.04em 0 rgba(0,0,255,.6); }
        }

        .tagline {
            color: var(--secondary);
            font-size: 13px;
            letter-spacing: 0.15em;
            margin-top: 10px;
            text-transform: uppercase;
        }

        .bio {
            max-width: 680px;
            margin: 18px auto 0;
            color: #bbb;
            font-size: 13px;
            line-height: 1.8;
        }

        .hero-links {
            margin-top: 28px;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 12px;
        }

        .hero-link {
            font-size: 11px;
            text-decoration: none;
            border: 1px solid var(--border);
            padding: 7px 18px;
            color: var(--primary);
            text-transform: uppercase;
            letter-spacing: 0.08em;
            transition: all 0.25s;
        }
        .hero-link:hover {
            background: var(--primary);
            color: #000;
            box-shadow: 0 0 14px var(--primary);
        }

        /* ── CONSOLE BODY ── */
        .console { padding: 0; }

        /* ── SECTION ── */
        .section {
            padding: 36px 40px;
            border-bottom: 1px solid var(--border-dim);
        }

        .cmd {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 22px;
        }
        .prompt { color: var(--secondary); font-size: 13px; white-space: nowrap; }
        .cmd-text { font-size: 13px; color: #ddd; }

        .section-title {
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.18em;
            color: var(--muted);
            border-left: 3px solid var(--primary);
            padding-left: 10px;
            margin-bottom: 20px;
        }

        /* ── ABOUT ── */
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }

        .about-item {
            background: var(--glass);
            border: 1px solid var(--border-dim);
            padding: 14px 16px;
            font-size: 12px;
            color: #ccc;
            line-height: 1.7;
        }

        .about-item::before {
            content: "> ";
            color: var(--primary);
        }

        /* ── EDUCATION ── */
        .edu-list { display: flex; flex-direction: column; gap: 12px; }

        .edu-item {
            border: 1px solid var(--border-dim);
            padding: 16px 20px;
            background: var(--glass);
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            gap: 20px;
        }

        .edu-left h4 { color: var(--secondary); font-size: 13px; margin-bottom: 4px; }
        .edu-left p { font-size: 12px; color: var(--muted); }
        .edu-right { text-align: right; flex-shrink: 0; }
        .edu-right .grade { color: var(--primary); font-size: 14px; font-weight: 700; }
        .edu-right .year { font-size: 11px; color: var(--muted); margin-top: 2px; }

        /* ── SKILLS ── */
        .filter-bar {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }

        .filter-btn {
            background: transparent;
            border: 1px solid var(--border);
            color: var(--primary);
            padding: 7px 16px;
            font-family: 'Fira Code', monospace;
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.06em;
            transition: all 0.25s;
            cursor: crosshair;
        }
        .filter-btn:hover, .filter-btn.active {
            background: var(--primary);
            color: #000;
            box-shadow: 0 0 12px rgba(0,255,65,0.4);
        }

        .skill-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 12px;
        }

        .skill-item { margin-bottom: 4px; }
        .skill-header { display: flex; justify-content: space-between; font-size: 12px; margin-bottom: 6px; }
        .skill-header span:last-child { color: var(--muted); }
        .bar-bg { background: #111; height: 6px; border: 1px solid var(--border-dim); }
        .bar-fill { height: 100%; background: linear-gradient(90deg, var(--primary), var(--secondary)); width: 0; transition: width 1s ease; }

        /* ── EXPERIENCE ── */
        .exp-list { display: flex; flex-direction: column; gap: 16px; }

        .exp-card {
            border: 1px solid var(--border-dim);
            border-left: 3px solid var(--secondary);
            padding: 18px 20px;
            background: var(--glass);
        }

        .exp-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 6px;
        }

        .exp-role { color: var(--secondary); font-size: 13px; font-weight: 700; }
        .exp-company { color: var(--primary); font-size: 12px; }
        .exp-date { font-size: 11px; color: var(--muted); white-space: nowrap; }
        .exp-tech { font-size: 11px; color: var(--muted); margin: 6px 0 10px; font-style: italic; }

        .exp-bullets { list-style: none; }
        .exp-bullets li {
            font-size: 12px;
            color: #ccc;
            padding: 3px 0 3px 16px;
            position: relative;
            line-height: 1.6;
        }
        .exp-bullets li::before { content: "▸"; color: var(--primary); position: absolute; left: 0; }

        /* ── PROJECTS ── */
        .project-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
            gap: 16px;
        }

        .project-card {
            border: 1px solid var(--border);
            padding: 20px;
            background: var(--glass);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: "";
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            transform: scaleX(0);
            transition: transform 0.3s;
        }

        .project-card:hover { border-color: rgba(0,255,65,0.4); box-shadow: 0 0 20px rgba(0,255,65,0.06); }
        .project-card:hover::before { transform: scaleX(1); }

        .project-name { color: var(--secondary); font-size: 13px; font-weight: 700; margin-bottom: 6px; }
        .project-tech { font-size: 10px; color: var(--muted); font-style: italic; margin-bottom: 10px; }
        .project-desc { list-style: none; }
        .project-desc li {
            font-size: 12px;
            color: #bbb;
            padding: 3px 0 3px 14px;
            position: relative;
            line-height: 1.6;
        }
        .project-desc li::before { content: "–"; color: var(--primary); position: absolute; left: 0; }

        .project-status {
            margin-top: 14px;
            font-size: 10px;
            letter-spacing: 0.1em;
            text-transform: uppercase;
        }
        .status-deployed { color: var(--primary); }
        .status-active { color: var(--secondary); }
        .status-research { color: var(--accent); }

        /* ── PUBLICATIONS ── */
        .pub-card {
            border: 1px solid var(--border-dim);
            border-left: 3px solid var(--accent);
            padding: 18px 20px;
            background: var(--glass);
        }
        .pub-title { font-size: 13px; color: #ddd; font-style: italic; line-height: 1.7; margin-bottom: 8px; }
        .pub-venue { font-size: 11px; color: var(--accent); letter-spacing: 0.08em; }

        /* ── CERTIFICATIONS ── */
        .cert-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 12px;
        }

        .cert-card {
            border: 1px solid var(--border-dim);
            padding: 14px 16px;
            background: var(--glass);
            font-size: 12px;
        }
        .cert-card .cert-name { color: var(--secondary); margin-bottom: 4px; }
        .cert-card .cert-issuer { color: var(--muted); font-size: 11px; }

        /* ── EXPLORING & COLLABORATE ── */
        .two-col {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .list-block { }
        .list-block h4 { font-size: 11px; text-transform: uppercase; letter-spacing: 0.14em; color: var(--muted); margin-bottom: 14px; border-bottom: 1px solid var(--border-dim); padding-bottom: 8px; }

        .tag-list { display: flex; flex-wrap: wrap; gap: 8px; }
        .tag {
            font-size: 11px;
            border: 1px solid var(--border);
            padding: 5px 12px;
            color: var(--primary);
            letter-spacing: 0.06em;
            transition: all 0.2s;
        }
        .tag:hover { background: var(--glass); box-shadow: 0 0 8px rgba(0,255,65,0.2); }
        .tag.blue { border-color: rgba(0,209,255,0.3); color: var(--secondary); }
        .tag.blue:hover { background: rgba(0,209,255,0.05); }

        /* ── CONTACT FOOTER ── */
        .contact-section {
            padding: 36px 40px;
            background: var(--terminal-header);
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 12px;
            margin-bottom: 30px;
        }

        .contact-item {
            border: 1px solid var(--border-dim);
            padding: 14px 18px;
            background: rgba(0,0,0,0.3);
            text-decoration: none;
            display: block;
            transition: all 0.25s;
        }
        .contact-item:hover { border-color: var(--primary); box-shadow: 0 0 12px rgba(0,255,65,0.1); }
        .contact-item .c-label { font-size: 10px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 4px; }
        .contact-item .c-value { font-size: 12px; color: var(--primary); }

        .footer-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            border-top: 1px solid var(--border-dim);
            padding-top: 18px;
            font-size: 10px;
            color: #333;
            letter-spacing: 0.08em;
        }

        .cursor { animation: blink 1s step-end infinite; }
        @keyframes blink { 50% { opacity: 0; } }

        /* ── RESPONSIVE ── */
        @media (max-width: 700px) {
            .section { padding: 28px 20px; }
            header { padding: 40px 20px 36px; }
            .about-grid { grid-template-columns: 1fr; }
            .two-col { grid-template-columns: 1fr; }
            .edu-item { flex-direction: column; gap: 6px; }
            .edu-right { text-align: left; }
            .nav-links { display: none; }
            .contact-section { padding: 28px 20px; }
        }
    </style>
</head>

<body>
<div class="shell">

    <!-- TITLE BAR -->
    <div class="titlebar">
        <div class="dots">
            <div class="dot r"></div>
            <div class="dot y"></div>
            <div class="dot g"></div>
        </div>
        <span class="titlebar-path">yuvraj@vps-04: ~/portfolio — zsh</span>
        <nav class="nav-links">
            <a href="#about">About</a>
            <a href="#skills">Skills</a>
            <a href="#experience">Experience</a>
            <a href="#projects">Projects</a>
            <a href="#contact">Contact</a>
        </nav>
    </div>

    <!-- HERO -->
    <header>
        <div class="glitch">Yuvraj Singh</div>
        <p class="tagline">[ Software Engineer &nbsp;|&nbsp; Full-Stack &nbsp;|&nbsp; Cloud &nbsp;|&nbsp; AI/ML ]</p>
        <p class="bio">
            Aspiring Computer Science Engineer with a passion for building scalable applications, intelligent systems, and impactful digital experiences. Pursuing B.Tech CSE at Amity University, Noida (2022–2026).
        </p>
        <div class="hero-links">
            <a class="hero-link" href="mailto:thinkyuvraj@gmail.com">/Mail</a>
            <a class="hero-link" href="https://linkedin.com/in/thinkyuvraj" target="_blank">/LinkedIn</a>
            <a class="hero-link" href="https://github.com/ThinkYuvraj" target="_blank">/GitHub</a>
            <a class="hero-link" href="https://my-portfolio-jc50.onrender.com/" target="_blank">/Portfolio</a>
        </div>
    </header>

    <div class="console">

        <!-- ABOUT -->
        <section class="section" id="about">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">whoami --full-profile</span>
            </div>
            <div class="about-grid">
                <div class="about-item">Passionate about Software Development, Full-Stack Web Development, and Cloud Technologies</div>
                <div class="about-item">Strong interest in building real-world solutions through clean, scalable, and efficient code</div>
                <div class="about-item">Enthusiastic about solving complex technical challenges and continuously learning emerging technologies</div>
                <div class="about-item">Co-authored research paper on hybrid ML methodologies presented at IC2SDT 2025, NIT Delhi</div>
                <div class="about-item">AWS Academy Graduate with hands-on experience in auto-scaling cloud infrastructures</div>
                <div class="about-item">Transforming innovative ideas into practical software solutions every single day</div>
            </div>
        </section>

        <!-- EDUCATION -->
        <section class="section" id="education">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">cat ./education/records.json</span>
            </div>
            <div class="edu-list">
                <div class="edu-item">
                    <div class="edu-left">
                        <h4>Bachelor of Technology — Computer Science &amp; Engineering</h4>
                        <p>Amity University, Noida</p>
                    </div>
                    <div class="edu-right">
                        <div class="grade">7.3 / 10 CGPA</div>
                        <div class="year">2022 – 2026</div>
                    </div>
                </div>
                <div class="edu-item">
                    <div class="edu-left">
                        <h4>CBSE Class XII</h4>
                        <p>Delhi Public School, Meerut</p>
                    </div>
                    <div class="edu-right">
                        <div class="grade">83.98%</div>
                        <div class="year">2022</div>
                    </div>
                </div>
                <div class="edu-item">
                    <div class="edu-left">
                        <h4>CBSE Class X</h4>
                        <p>Delhi Public School, Meerut</p>
                    </div>
                    <div class="edu-right">
                        <div class="grade">72.96%</div>
                        <div class="year">2020</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- SKILLS -->
        <section class="section" id="skills">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">run-system-check --tech-stack</span>
            </div>
            <div class="filter-bar">
                <button class="filter-btn active" onclick="loadSkills('all', this)">View_All</button>
                <button class="filter-btn" onclick="loadSkills('languages', this)">Languages</button>
                <button class="filter-btn" onclick="loadSkills('frontend', this)">Frontend</button>
                <button class="filter-btn" onclick="loadSkills('backend', this)">Backend</button>
                <button class="filter-btn" onclick="loadSkills('cloud', this)">Cloud_DevOps</button>
                <button class="filter-btn" onclick="loadSkills('tools', this)">Tools</button>
            </div>
            <div class="skill-grid" id="skill-output"></div>
        </section>

        <!-- EXPERIENCE -->
        <section class="section" id="experience">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">ls ./experience/ --verbose</span>
            </div>
            <div class="exp-list">
                <div class="exp-card">
                    <div class="exp-header">
                        <div>
                            <div class="exp-role">MERN Stack Developer Intern</div>
                            <div class="exp-company">SmartBridge</div>
                        </div>
                        <div class="exp-date">May – July 2025</div>
                    </div>
                    <div class="exp-tech">HTML5, Tailwind CSS, JavaScript, React, Node.js, MongoDB</div>
                    <ul class="exp-bullets">
                        <li>Architected a real-time event-driven chat infrastructure achieving deterministic end-to-end message delivery latency of &lt;100 ms.</li>
                        <li>Implemented optimized database indexing mechanisms and secure stateful authentication, reducing query latency by 25%.</li>
                        <li>Built scalable RESTful APIs and WebSocket synchronization primitives via Socket.IO for seamless multi-user experience.</li>
                    </ul>
                </div>
                <div class="exp-card">
                    <div class="exp-header">
                        <div>
                            <div class="exp-role">Web Developer</div>
                            <div class="exp-company">Jabsz Gaming Studios LLP</div>
                        </div>
                        <div class="exp-date">May – July 2025</div>
                    </div>
                    <div class="exp-tech">HTML5, Tailwind CSS, JavaScript, React, TypeScript, Godot</div>
                    <ul class="exp-bullets">
                        <li>Leveraged React and TypeScript to decouple state mutation logic and optimize rendering cycles under the Godot framework.</li>
                        <li>Improved interactive frame-rate responsiveness by 25% through optimized game logic and efficient state management.</li>
                        <li>Developed 'Time Rewind' game, directly driving a 30% increase in user session retention metrics.</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- PROJECTS -->
        <section class="section" id="projects">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">ls ./featured_projects/ --all</span>
            </div>
            <div class="project-grid">
                <div class="project-card">
                    <div class="project-name">WEATHERLY</div>
                    <div class="project-tech">Python, TensorFlow/Keras, Streamlit, Scikit-learn, Pandas, NumPy, Matplotlib, SciPy</div>
                    <ul class="project-desc">
                        <li>Designed hybrid deep learning architecture with 2 stacked LSTM (64-unit) and 2 GRU (64-unit) recurrent layers.</li>
                        <li>Trained over 50 epochs, achieving RMSE of 1.23 and MAE of 0.89 with Random Forest-based auto-stopping optimization.</li>
                        <li>Integrated a Gen AI-powered NLP assistant that converts weather forecasts into simplified natural-language insights.</li>
                    </ul>
                    <div class="project-status status-deployed">● DEPLOYED — Jan–Mar 2026</div>
                </div>
                <div class="project-card">
                    <div class="project-name">TEAM TASK MANAGER</div>
                    <div class="project-tech">React.js, Node.js, Express.js, MongoDB, Tailwind CSS</div>
                    <ul class="project-desc">
                        <li>Developed a centralized collaboration platform for project organization, task assignment, and progress tracking.</li>
                        <li>Implemented secure role-based access, dashboard analytics, and task prioritization for streamlined workflows.</li>
                        <li>Reduced communication gaps across teams by enabling real-time project visibility and status tracking.</li>
                    </ul>
                    <div class="project-status status-active">● ACTIVE — Mar–Apr 2026</div>
                </div>
                <div class="project-card">
                    <div class="project-name">TEAM COLLABORATION WORKSPACE</div>
                    <div class="project-tech">HTML5, Tailwind CSS, Node.js, Express.js, Socket.IO, MongoDB</div>
                    <ul class="project-desc">
                        <li>Developed a real-time collaborative editing platform supporting concurrent multi-user editing with low-latency updates via Socket.IO.</li>
                        <li>Built scalable backend with Express.js, RESTful APIs, and MongoDB for efficient data storage and retrieval.</li>
                    </ul>
                    <div class="project-status status-active">● ACTIVE — Feb–Dec 2025</div>
                </div>
            </div>
        </section>

        <!-- PUBLICATIONS -->
        <section class="section" id="publications">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">cat ./publications/research.log</span>
            </div>
            <div class="pub-card">
                <div class="pub-title">"A Novice Approach to Weather Forecasting Using Hybrid Predictive Methodologies in Machine Learning"</div>
                <div class="pub-venue">IC2SDT 2025 Conference &nbsp;|&nbsp; NIT Delhi</div>
            </div>
        </section>

        <!-- CERTIFICATIONS -->
        <section class="section" id="certifications">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">ls ./certifications/</span>
            </div>
            <div class="cert-grid">
                <div class="cert-card">
                    <div class="cert-name">AWS Academy Graduate</div>
                    <div class="cert-issuer">AWS Academy Cloud Foundations &nbsp;·&nbsp; Jan 2025</div>
                </div>
                <div class="cert-card">
                    <div class="cert-name">MongoDB Developer Path</div>
                    <div class="cert-issuer">MongoDB (SmartBridge) &nbsp;·&nbsp; Jun 2025</div>
                </div>
                <div class="cert-card">
                    <div class="cert-name">Joy Computing using Python</div>
                    <div class="cert-issuer">NPTEL — IIT Ropar &nbsp;·&nbsp; Jul–Oct 2024</div>
                </div>
                <div class="cert-card">
                    <div class="cert-name">Design Thinking: A Primer</div>
                    <div class="cert-issuer">NPTEL — IIT Madras &nbsp;·&nbsp; Jan–Feb 2024</div>
                </div>
            </div>
        </section>

        <!-- CURRENTLY EXPLORING / OPEN TO COLLABORATE -->
        <section class="section">
            <div class="cmd">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">cat ./status/current.conf</span>
            </div>
            <div class="two-col">
                <div class="list-block">
                    <h4>Currently Exploring</h4>
                    <div class="tag-list">
                        <span class="tag">Advanced Java Backend</span>
                        <span class="tag">System Design</span>
                        <span class="tag">Scalable Architectures</span>
                        <span class="tag">Cloud Infrastructure</span>
                        <span class="tag">DevOps Practices</span>
                        <span class="tag">AI/ML Integration</span>
                    </div>
                </div>
                <div class="list-block">
                    <h4>Open to Collaborate On</h4>
                    <div class="tag-list">
                        <span class="tag blue">Full-Stack Web Apps</span>
                        <span class="tag blue">Software Dev Projects</span>
                        <span class="tag blue">Cloud-Based Solutions</span>
                        <span class="tag blue">AI/ML Integrated Systems</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- CONTACT -->
        <section class="contact-section" id="contact">
            <div class="cmd" style="margin-bottom: 22px;">
                <span class="prompt">ys@kernel:~$</span>
                <span class="cmd-text">ping --connect yuvraj</span>
            </div>
            <div class="contact-grid">
                <a class="contact-item" href="mailto:thinkyuvraj@gmail.com">
                    <div class="c-label">Email</div>
                    <div class="c-value">thinkyuvraj@gmail.com</div>
                </a>
                <a class="contact-item" href="tel:+919639677118">
                    <div class="c-label">Phone</div>
                    <div class="c-value">+91-9639677118</div>
                </a>
                <a class="contact-item" href="https://linkedin.com/in/thinkyuvraj" target="_blank">
                    <div class="c-label">LinkedIn</div>
                    <div class="c-value">linkedin.com/in/thinkyuvraj</div>
                </a>
                <a class="contact-item" href="https://github.com/ThinkYuvraj" target="_blank">
                    <div class="c-label">GitHub</div>
                    <div class="c-value">github.com/ThinkYuvraj</div>
                </a>
                <a class="contact-item" href="https://my-portfolio-jc50.onrender.com/" target="_blank">
                    <div class="c-label">Portfolio</div>
                    <div class="c-value">my-portfolio-jc50.onrender.com</div>
                </a>
                <div class="contact-item" style="cursor: crosshair;">
                    <div class="c-label">Location</div>
                    <div class="c-value">Noida, India</div>
                </div>
            </div>
            <div class="footer-bar">
                <span>ROOT ACCESS ENABLED &nbsp;|&nbsp; PORT 8080 OPEN &nbsp;|&nbsp; SECURE SESSION 2.0<span class="cursor">_</span></span>
                <span>YUVRAJ SINGH &copy; 2026</span>
            </div>
        </section>

    </div>
</div>

<script>
    const skills = {
        languages: [
            { name: "Python", level: 85 },
            { name: "JavaScript", level: 88 },
            { name: "TypeScript", level: 82 },
            { name: "Java", level: 65 }
        ],
        frontend: [
            { name: "React.js", level: 85 },
            { name: "HTML5 / CSS3", level: 95 },
            { name: "Tailwind CSS", level: 90 }
        ],
        backend: [
            { name: "Node.js", level: 85 },
            { name: "Express.js", level: 88 },
            { name: "Socket.IO", level: 80 },
            { name: "MongoDB", level: 82 },
            { name: "SQL", level: 80 },
            { name: "REST APIs", level: 88 }
        ],
        cloud: [
            { name: "AWS EC2 / Lambda", level: 75 },
            { name: "AWS S3 / RDS", level: 72 },
            { name: "AWS VPC / IAM", level: 70 },
            { name: "Docker", level: 68 },
            { name: "Git / CI-CD", level: 85 }
        ],
        tools: [
            { name: "GitHub", level: 90 },
            { name: "VS Code", level: 95 },
            { name: "IntelliJ IDEA", level: 80 },
            { name: "Jupyter Notebook", level: 85 },
            { name: "Linux", level: 75 }
        ]
    };

    function loadSkills(category, btn) {
        document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');

        const list = category === 'all'
            ? Object.values(skills).flat()
            : skills[category];

        const container = document.getElementById('skill-output');
        container.innerHTML = '';

        list.forEach((s, i) => {
            const el = document.createElement('div');
            el.className = 'skill-item';
            el.innerHTML = `
                <div class="skill-header"><span>${s.name}</span><span>${s.level}%</span></div>
                <div class="bar-bg"><div class="bar-fill" id="b${i}" style="width:0%"></div></div>`;
            container.appendChild(el);
            setTimeout(() => {
                document.getElementById('b' + i).style.width = s.level + '%';
            }, i * 40 + 80);
        });
    }

    window.onload = () => {
        loadSkills('all', document.querySelector('.filter-btn.active'));
    };
</script>

</body>
</html>
